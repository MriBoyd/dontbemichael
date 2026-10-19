# Office task helper tools for agents

Status: Draft design note proposing agent-facing deterministic tools (#250, follow-up to #418).  
Area: Agent tools & Hive runtime (`src/main/index.ts`, `resources/`).

## Premise

LLMs are versatile across open-ended natural language reasoning, but are slow, token-heavy, and error-prone when executing deterministic mechanical steps such as multi-line arithmetic or scanning tabular datasets for duplicate rows.

An earlier attempt (#418) implemented deterministic handlers as a pre-dispatch interception layer in front of the agent, matching keywords in incoming messages and auto-completing cards. That shape was rejected for two fundamental architectural reasons:
1. **Keyword matching drops work:** An incoming message like *"Calculate the total revenue for Q3 from QuickBooks and send it to the accountant"* got marked Done as a sum of numbers in the sentence, skipping QuickBooks and the email dispatch entirely.
2. **App invariants on card ownership:** In *Don't Be Michael*, Michael owns every card from start to Done; the app records and shows, but never creates, moves, or finishes a card itself.

### The Accepted Direction

Rather than placing deterministic code *in front* of the agent, offer these routines as **tools a team member can call**.
The model receives the request, plans the work, decides when a tool fits, executes exact code for that step, and uses the result to finish the card. The work remains on Michael's card with nothing skipped.

---

## 1. Initial Tools: Schemas and Refusal Rules

We propose starting with two focused, high-leverage tools:
1. `add_these_up`: Exact arithmetic across a list of numbers or currency values.
2. `find_duplicate_rows`: Exact detection and grouping of duplicate records across tabular data (CSV or JSON).

### Tool 1: `add_these_up`

Computes deterministic arithmetic across an array of numbers or currency strings.

#### Input Schema
```json
{
  "type": "object",
  "properties": {
    "values": {
      "type": "array",
      "items": { "type": ["number", "string"] },
      "description": "Numbers or currency strings to compute (e.g. [1200, \"$450.50\", \"-30.00\"])."
    },
    "operation": {
      "type": "string",
      "enum": ["sum", "average", "min", "max", "median"],
      "default": "sum",
      "description": "The calculation to perform. Defaults to 'sum'."
    },
    "precision": {
      "type": "integer",
      "minimum": 0,
      "maximum": 10,
      "description": "Optional decimal places for rounding. Defaults to 2 if any input contains currency/decimal points, otherwise exact."
    }
  },
  "required": ["values"]
}
```

#### Success Output
```json
{
  "ok": true,
  "operation": "sum",
  "count": 3,
  "result": 1620.5,
  "formatted": "1,620.50"
}
```

#### Refusals & Error Cases
The tool refuses execution cleanly without crashing or throwing unhandled exceptions:
- **Empty input:** `values` is empty or missing.
  `{ "ok": false, "error": "empty_values", "message": "At least one numeric value must be provided." }`
- **Invalid/unparseable values:** Items that cannot be parsed into finite numbers (e.g., `"N/A"`, `"TBD"`, words).
  `{ "ok": false, "error": "unparseable_values", "invalidIndices": [1], "invalidValues": ["TBD"], "message": "Value at index 1 ('TBD') could not be parsed as a number." }`
- **Array size limit:** More than 50,000 values in a single call (to prevent memory spikes).
  `{ "ok": false, "error": "payload_too_large", "message": "Maximum of 50,000 values allowed per call." }`
- **Non-finite results:** Division by zero or overflow.
  `{ "ok": false, "error": "calculation_error", "message": "Result is not a finite number." }`

---

### Tool 2: `find_duplicate_rows`

Identifies and groups duplicate rows in tabular data or record lists by specific keys or full-row equality.

#### Input Schema
```json
{
  "type": "object",
  "properties": {
    "data": {
      "type": ["string", "array"],
      "description": "The dataset to inspect: either a CSV formatted string (with header row) or an array of JSON objects."
    },
    "keys": {
      "type": "array",
      "items": { "type": "string" },
      "description": "Optional list of column names or keys to evaluate duplicates on (e.g. ['email'] or ['invoice_number']). If omitted, compares all fields."
    },
    "case_sensitive": {
      "type": "boolean",
      "default": false,
      "description": "Whether string comparisons should be case sensitive. Defaults to false."
    },
    "trim_whitespace": {
      "type": "boolean",
      "default": true,
      "description": "Whether to strip leading/trailing whitespace before comparison. Defaults to true."
    }
  },
  "required": ["data"]
}
```

#### Success Output
```json
{
  "ok": true,
  "total_rows": 150,
  "unique_rows": 146,
  "duplicate_groups_count": 2,
  "duplicate_rows_count": 4,
  "groups": [
    {
      "key": "alice@example.com",
      "count": 2,
      "row_indices": [12, 45],
      "sample": { "name": "Alice Smith", "email": "alice@example.com", "role": "Designer" }
    },
    {
      "key": "bob@example.com",
      "count": 2,
      "row_indices": [30, 88],
      "sample": { "name": "Bob Jones", "email": "bob@example.com", "role": "Developer" }
    }
  ]
}
```

#### Refusals & Error Cases
- **Empty dataset:** Zero rows or empty string.
  `{ "ok": false, "error": "empty_data", "message": "Data contains no records or rows to check." }`
- **Malformed CSV / JSON:** Parsing fails on syntax.
  `{ "ok": false, "error": "invalid_syntax", "message": "Could not parse data as CSV or JSON array: unclosed quote at line 14." }`
- **Unknown keys:** Specified `keys` are not present in the record headers/fields.
  `{ "ok": false, "error": "missing_keys", "missing": ["customer_id"], "availableKeys": ["id", "name", "email"], "message": "Key 'customer_id' not found in data columns." }`
- **Size limit:** Datasets larger than 20MB or 100,000 rows.
  `{ "ok": false, "error": "payload_too_large", "message": "Data exceeds maximum supported size (100,000 rows / 20MB)." }`

---

## 2. How a Team Member Gets Them

The app already delivers native tools to agents in two established ways:
1. **MCP Servers (`mcpServers`)**: e.g., `md-mail` (`resources/md-mail-mcp.cjs`), which is registered in the agent's MCP configuration when spawned (`src/main/index.ts:4262`). Claude Code communicates with it over stdio via JSON-RPC.
2. **CLI Helpers in Agent Shell**: e.g., `kg.cjs` (`resources/kg.cjs`), where the agent is informed of the command via system prompt instructions and invokes it in bash.

### Recommended Delivery Path: Bundled MCP Server (`md-office-tools-mcp.cjs`)

We recommend the **MCP server pattern**, matching `md-mail-mcp.cjs`:
- **Location:** `resources/md-office-tools-mcp.cjs` (pure Node standard library, zero external runtime dependencies).
- **Registration:** Added to `mcpServers` in the agent's configuration file alongside `md-mail`:
  ```json
  {
    "mcpServers": {
      "md-office-tools": {
        "command": hive.nodeCommand(),
        "args": [mdOfficeToolsScriptPath()]
      }
    }
  }
  ```
- **Why MCP over CLI:**
  - The model calls it natively as structured tool calls (`add_these_up`, `find_duplicate_rows`) with schema validation.
  - The model does not need to spawn a bash subshell, escape arguments, or handle stdout parsing.
  - Results return directly as structured JSON objects into the model's tool-response block.
  - No secrets or network broker are required; the script runs entirely locally with pure in-memory deterministic algorithms.

---

## 3. Verification & Benchmark Plan: Showing Concrete Savings

To prove this saves tokens and prevents errors rather than adding unnecessary overhead, we define an empirical benchmark suite comparing tasks **with the tools** vs. **without the tools (pure LLM reasoning)**.

### Benchmark Setup

Two representative tasks evaluated on the standard team member model:

#### Benchmark Task A: Summing Invoices
- **Dataset:** 50 line items extracted from a realistic multi-page billing statement (currency strings with varying decimals, negative refunds, and formatting).
- **Measurement criteria:**
  - **Correctness:** Arithmetic accuracy ($0\%$ error with tool vs. typical off-by-a-few errors in raw LLM mental math).
  - **Output token count:** Tokens required to produce step-by-step mental scratchpad vs. single tool call invocation.
  - **Latency:** Turn completion time in milliseconds.

#### Benchmark Task B: Customer List Deduplication
- **Dataset:** CSV with 200 customer rows containing 8 duplicate entries scattered across the file, matching on `email`.
- **Measurement criteria:**
  - **Precision & Recall:** Did the agent miss any duplicates? (Pure LLM attention over 200 rows frequently misses duplicate pairs separated by many tokens).
  - **Input/Output token count:** Tokens spent in agent reasoning steps.
  - **Reliability:** Reproducibility across 5 identical runs (deterministic code has $100\%$ consistency).

### Reporting & Measurement Methodology

To ensure transparent, reproducible evidence rather than assumed savings:
- A benchmark script (`test/bench-office-tools.cjs`) will run the two tasks against the agent session in both modes (with and without the tools enabled).
- Token usage will be extracted directly from the hive cost ledger (`<home>/hive/cost-ledger.jsonl` tracking `input` and `output` tokens, matching `tools/agent-metrics.cjs`).
- Correctness will be verified deterministically against known ground-truth outputs.

The PR implementation will populate the following empirical evidence table with recorded numbers from the benchmark run:

| Task | Mode | Correctness (Ground Truth Match) | Input Tokens | Output Tokens | Total Tokens |
|---|---|---|---|---|---|
| 50-Item Invoice Sum | Pure LLM (Baseline) | *[To be measured]* | *[To be measured]* | *[To be measured]* | *[To be measured]* |
| 50-Item Invoice Sum | With `add_these_up` | *[To be measured]* | *[To be measured]* | *[To be measured]* | *[To be measured]* |
| 200-Row Deduplication | Pure LLM (Baseline) | *[To be measured]* | *[To be measured]* | *[To be measured]* | *[To be measured]* |
| 200-Row Deduplication | With `find_duplicate_rows` | *[To be measured]* | *[To be measured]* | *[To be measured]* | *[To be measured]* |

---

## 4. Explicitly Out of Scope

To keep this work clean and aligned with the repo maintainers' guidance:
- **No pre-dispatch matching:** The webhook and incoming message flow will not inspect text or divert cards before agents see them.
- **No card status modification:** The tools return data to the calling agent; only Michael / the assigned agent moves cards or marks them Done.
- **No local models or alternative LLM providers:** Evaluated strictly on the existing engine; multi-provider / local model work remains blocked on #222.
