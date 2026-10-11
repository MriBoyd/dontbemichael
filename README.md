<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./branding/logo/lockup/dbm-lockup-horizontal-dark.svg">
  <img src="./branding/logo/lockup/dbm-lockup-horizontal-light.svg" alt="Don't Be Michael" width="420">
</picture>

### An AI office for your small business

**[dontbemichael.com](https://dontbemichael.com)**

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./branding/reference/studio/home-dark.png">
  <img src="./branding/reference/studio/home-light.png" alt="The office: a pod for each department around Michael's glass office, and the Needs you board on the right with what waits on you" width="1240">
</picture>

Pick your kind of business, pick your team, and Michael, your office manager, runs the office
while you run the business. Every team member is an AI agent with a job, its own folder and its
own memory, working on your computer.

<p>
  <a href="./LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-FF6B6B.svg?style=flat-square&labelColor=1A1320"></a>
  <img alt="Status: early release" src="https://img.shields.io/badge/status-early%20release-FFFDF5.svg?style=flat-square&labelColor=1A1320">
  <img alt="Platform: macOS and Windows 11" src="https://img.shields.io/badge/platform-macOS%20%7C%20Windows%2011-FFFDF5.svg?style=flat-square&labelColor=1A1320">
  <a href="https://dontbemichael.com"><img alt="Website: dontbemichael.com" src="https://img.shields.io/badge/web-dontbemichael.com-FF6B6B.svg?style=flat-square&labelColor=1A1320"></a>
</p>

<br>

**[Download for Mac](https://github.com/agentvivekkumar/dontbemichael/releases/latest)** · **[Download for Windows](https://github.com/agentvivekkumar/dontbemichael/releases/latest)**

</div>

---

> [!NOTE]
> **Talk to Michael. Let the office do the rest.**
> Tell Michael what you need. He hands the work to whoever's job it is, keeps the team moving, and
> brings you only the calls that need you.

> [!TIP]
> **New in 0.1.7: a clear Microsoft 365 message, and safer large files.**
> A mailbox on your own domain that runs on Microsoft 365 now says it cannot be connected yet,
> instead of a misleading error. A Word, Excel or PowerPoint file too big to read is refused before
> it can use up memory, an email is no longer sent twice after a restart, and web links open in your
> browser. In 0.1.6, Can send stopped putting emails on Ask me.
> [Every feature, release by release](./docs/FEATURES.md).

## Contents

- [What it is](#what-it-is)
- [How it differs from Munder Difflin](#how-it-differs-from-munder-difflin)
- [Your team](#your-team)
- [A mailbox for every job](#a-mailbox-for-every-job)
- [What the office does](#what-the-office-does)
- [Getting started](#getting-started)
- [Your data](#your-data)
- [For developers](#for-developers)
  - [Prerequisites and setup](#prerequisites-and-setup)
  - [Quick start: running your first agent](#quick-start-running-your-first-agent)
  - [Folder structure](#folder-structure)
  - [Troubleshooting common issues](#troubleshooting-common-issues)
  - [Where to read next](#where-to-read-next)
  - [What this build leaves out](#what-this-build-leaves-out)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## What it is

Don't Be Michael is a desktop app that runs a small office of AI team members for your business.
Each team member is a [Claude Code](https://claude.com/claude-code) agent with a role: finance,
customer support, sales, marketing and so on. Michael is the office manager. You talk to him; he
routes the work, answers the team's questions, and asks you only when something needs your
decision.

Everything runs on your computer, on the Claude plan you already have. Each team member has a
desk in an office you can watch, a pod for each department around Michael's glass office, so you
can see who is working on what.

## How it differs from Munder Difflin

Don't Be Michael grew out of [Munder Difflin](https://github.com/chaitanyagiri/munder-difflin),
and it keeps that project's core: every team member is a real Claude Code process in its own
terminal, and the team coordinates through the hive, a folder of plain files. What was built on
top is a different product for a different person.

Munder Difflin is an agent harness for developers: it turns the coding CLIs you already run into
clones of you. Don't Be Michael is an office for a small business owner who never opens a
terminal. That changes almost every decision:

| | Munder Difflin | Don't Be Michael |
|---|---|---|
| **Made for** | Developers running coding agents | Small business owners in any line of work, with no technical background needed |
| **Michael** | Your clone, routing work between your agents | Your office manager: the only one who assigns work, decides the team's day to day requests, and brings you only the calls that need you |
| **Setting up** | Start agents in terminals and give them work | Pick your kind of business, get a suggested team, and hire in four steps with a real job and a work style for each; no two teammates do the same work |
| **Email** | The one Gmail account on your Claude account, shared by every agent | As many mailboxes as the business runs on, one per team member, each set to Can send, Send on approval or Draft only; passwords stay encrypted on your computer |
| **Access control** | None: every agent can reach every app connected to your Claude account and every tool you set up in Claude Code | You decide exactly which apps the office can use and which team member uses each one; the app enforces it on every call |
| **Files and data** | Hard to give an agent a workspace of its own: agents work in code project folders, with no way to give each one its own set of files and data | Your business folder becomes the office's filing cabinet, with access that follows its hierarchy. Each team member works in its own folder with the files its job needs, such as product documentation and client lists for Sales, or survey results and user interviews for Marketing, and opens only that folder. Michael, above them, reads every folder and changes none. You organize your own work in the same folders the team uses |
| **User experience** | Lots of low level details and out of place screens, which make the system hard to use and hard to focus on the right things | A modern office workspace, redesigned from the ground up for business users. Unneeded details and repetition are gone, and there is one clear way to talk to the office, instead of every option piled into an orchestrator panel |
| **Cost and data** | Free, with a paid Pro plan; anonymous usage stats | Free, no paid plan, no usage data sent |

If you write code and want a team of coding agents, Munder Difflin is the better fit. If you run a
business and want the work done without watching terminals, this is the better fit.

## Your team

Setup asks for your business and your kind of business, then suggests a team from that business's
Office Pack. You pick who joins, and you can hire more later.

| Kind of business | Suggested team |
|---|---|
| Restaurant & Food | Finance, Executive Admin, Customer Support, Marketing, Quality Control, Supply Chain, HR Manager |
| Retail Shop | Finance, Executive Admin, Customer Support, Inventory & Shipping, Marketing, Supply Chain, Sales Director |
| Pro Services | Finance, Executive Admin, Customer Support, Sales Director, Marketing, IT Security |
| Home Services | Finance, Executive Admin, Customer Support, Sales Director, Inventory & Shipping, Supply Chain, Marketing |
| SaaS/Consulting | Finance, Executive Admin, HR Manager, Customer Support, Sales Director, Marketing, IT Engineer, IT Security |
| Something else | Pick from the core roles |

Each role comes with a Role description, which tells Michael what work to send there, and a Work
style, which tells the team member how to do its job at your business. You can change both in
Edit Agent.

## A mailbox for every job

Most AI assistants read one inbox: yours. Don't Be Michael connects as many mailboxes as your
business runs on, and each team member works from the one that matches its job.

| Team member | Watches | Can it send? |
|---|---|---|
| Pam, Executive Admin | ceo@yourbusiness.com | Send on approval: you approve each email in Needs you, then Pam sends it |
| Kelly, Customer Support | support@yourbusiness.com | Can send |
| Dwight, Sales Director | sales@yourbusiness.com | Can send |

- **Connect once.** In Settings, Connections, Mailboxes, add Gmail, Google Workspace, iCloud,
  Yahoo, Zoho or any other IMAP mailbox with an app password. The login is tested before it is
  saved, and the password stays encrypted on your computer, never in a file an agent can read.
- **Hand it out per team member.** On a team member's Access tab, under Email, choose **Add a
  mailbox**, pick it, choose **Watch the inbox**, and set **Can send**, **Send on approval** or **Draft only**. Nobody gets a mailbox until you give it one,
  and each mailbox is watched by one team member: moving it to another asks you first.
- **Let another team member send from it.** Add a mailbox someone else watches and choose
  **Send only**, with its own Can send, Send on approval or Draft only.
  Sales can send outreach from the CEO's address without reading the CEO's inbox: replies land
  with the mailbox's own team member, who passes them on. The mailbox shows who else sends from it.
- **You choose how mail leaves.** Can send goes out at once. Send on approval puts each email on
  Needs you, where you can edit it, approve it, ask for changes or stop it; the team member sends
  what you approved and learns from your edits. Draft only saves replies in the mailbox's Drafts
  for you to send.
- **Approve a kind of email once.** When you keep approving the same kind of email unchanged, the
  team member can offer to send that kind without asking. Tick the offer on the card, and it shows
  under Sends without asking on its Access tab, with Revoke. A separate quick check reads each such
  email first, and anything that doesn't fit comes to you.
- **Each one stays in its lane.** A team member reads, searches, files (archive, mark read, mark
  junk), drafts and sends only as you allowed, in the mailbox you gave it, and cannot forward or
  attach mail from another one. Nothing it does deletes mail.
- **Put it on a clock.** Add a schedule like "Check the support inbox" every hour in the same tab,
  with a focus area for each run, and the team member sorts new mail, answers it as its Sending
  setting allows and tells Michael what needs you. A new Executive Admin arrives with an Inbox to zero job already set.
- **You hear when it breaks.** If a provider stops accepting the password, the mailbox shows
  "needs you" and Michael asks you to fix it once, on the Needs you board.

Outlook and Microsoft 365 are not supported yet. The Gmail and Calendar connected to your Claude
account are separate: they are listed under Claude connectors in Settings, off until you turn them
on and give them to a team member.

## What the office does

<table>
<tr>
<td width="50%" valign="middle">

### Talk to Michael, not the whole team

Michael is the one you talk to. He sends each job to the team member whose role fits, keeps an eye
on the task board, and brings you only what needs you. He is the only one who hands out work: when
one team member needs another to do something, the request goes to Michael and he decides who
does it. Team members can still ask each other questions directly. When you answer a question, the
answer becomes his work until he routes it and closes it. Once an hour he runs a standup with the
team. He is the only one who sends you desktop notifications. To speak with one team member
directly, open it and choose **Talk 1:1**; Michael sends it no work until you end the 1:1.

</td>
<td width="50%">
  <img src="./branding/reference/studio/michael-office-schedule.png" alt="Michael selected: his card in the office and his Office schedule, every job on a clock across the team" width="100%">
</td>
</tr>
<tr>
<td width="50%" valign="middle">

### Hire a team member

The hire wizard has four steps: Who, Job, Role and Finalize. Pick a character and it brings a
job: one a teammate does today, one from your Office Pack, one from any other kind of business, or
a new one you write. Before you hire, the app checks the new job against every teammate's so no
two do the same work; an overlap has to be tied to its own mailbox or topic first. The work style
is plain words you can edit. Each hire gets its own folder inside your business folder and starts
working.

</td>
<td width="50%">
  <img src="./branding/reference/studio/hire.png" alt="The hire wizard: pick a character, then their job, role and work style" width="100%">
</td>
</tr>
<tr>
<td width="50%" valign="middle">

### Memory that improves

Each team member keeps a short list of lasting notes: your preferences and corrections, facts it
looked up, where things live, and the steps for tasks it does again. A tidy up in the background
merges and updates them, so memory gets better instead of piling up.

</td>
<td width="50%">
  <img src="./branding/reference/studio/kelly-memory.png" alt="Kelly's Memory tab: her preferences, facts, where things live and the steps she knows" width="100%">
</td>
</tr>
<tr>
<td width="50%" valign="middle">

### You stay in charge

Spending money, deleting things and changes of scope come to you. A team member that loops or
keeps failing is steered, then held, then stopped. Each one works under house rules: state only
what it can trace to a source, say when it doesn't know, and never make up people, customers or
quotes.

</td>
<td width="50%">
  <img src="./branding/reference/studio/settings-autonomy.png" alt="Settings, Agents: the default model, approvals and the circuit breaker" width="100%">
</td>
</tr>
<tr>
<td width="50%" valign="middle">

### Watch the office work

Desks light up as team members clock in and go dark at closing time. Envelopes fly between pods
as work moves, Michael points before he hands a job out, scheduled jobs ring his wall clock, and
idle teammates trade lines across the office. Click any pod to see that team member's work live.

</td>
<td width="50%">
  <img src="./branding/reference/studio/kelly-work.png" alt="Kelly selected: her pod in the office and her Work tab, her session live" width="100%">
</td>
</tr>
<tr>
<td width="50%" valign="middle">

### Set up once

Setup asks for your business name, your kind of business, the owner and your headquarters
address. Contact details, hours and prices are optional and can wait for Settings. Michael then
shows you around the office and suggests a starter team: you pick who joins and where each one
works. The last step, Get Michael ready, installs Claude Code if your computer doesn't have it
and signs you in where you can see it, or takes an Anthropic API key instead.

</td>
<td width="50%">
  <img src="./branding/reference/studio/onboarding-business.png" alt="Setup step 1: your business name, kind of business, owner and headquarters address" width="100%">
</td>
</tr>
<tr>
<td width="50%">
  <img src="./branding/reference/studio/onboarding-meet.png" alt="Setup step 3: Michael explains the starter team, how he runs the office, memory and approvals" width="100%">
</td>
<td width="50%">
  <img src="./branding/reference/studio/onboarding-team.png" alt="Setup step 4: pick your starter team; the office fills with a pod for each person picked" width="100%">
</td>
</tr>
</table>

**Running the office**
- **Needs you.** When the team needs a decision, Michael puts it on the Needs you board. Your answer goes back to whoever asked, and they remember it. Michael gets it too, as work he routes and then closes.
- **Michael answers in the app.** A question you type in the Talk to Michael box opens a conversation above it. Each question shows where it stands, such as Michael has it, Waiting for you or Answered, and his reply arrives under it, with one count on the box and one notification per answer. Commands such as /clear still go straight to his terminal. Scheduled outcomes, such as a weekly summary, arrive on Needs you as quiet Report cards you clear with Got it.
- **Schedules.** Each team member's jobs on a clock live in the On a schedule section of its Access tab. Say when and which job ("Follow up on unpaid invoices", every weekday at 9), and the team member does it the way its Work style says. One job can have several "when" lines, like every 2 hours on weekdays plus 2 pm on weekends. A team member can ask for a schedule change; Michael decides it, and asks you on Needs you only when he can't settle it. Michael's Office schedule tab lists every job that is on.
- **A mailbox for each team member.** Connect Gmail, Google Workspace, iCloud, Yahoo, Zoho or any other IMAP mailbox with an app password in Settings, Connections, Mailboxes. The password is tested before it is saved and stays encrypted on your computer. Then add it on a team member's Access tab to watch its inbox, and choose Can send, Send on approval or Draft only. Each mailbox has one team member watching it; others can be added to send only from it. Outlook is not supported yet.
- **Claude connectors.** Settings, Connections, Claude connectors lists every connector on your Claude account (HubSpot, Google Drive, Gmail, QuickBooks and the rest), read from Claude by itself. Each is off until you turn it on; then give it to the team members who need it on their Access tab. QuickBooks keeps Read only or Can make changes, and Oscar starts on and Read only. Your own Claude Code servers, plugin servers included, never reach the team.
- **Every team member's panel.** Profile first (the job, its folder and the instructions it works from), then Access (email, Claude connectors, and schedules), Messages as a day by day history, Memory as readable notes, and Work, its session live.
- **Office, Tasks, Who talks to whom.** Tabs in the top bar switch between the office, the whole task board, and who talks to whom.
- **Webhooks.** Another app sends a webhook (set it up in Settings, Connections) and Michael picks it up; the sender can check on the work and get its result.
- **A fresh start without losing work.** A team member that has sat idle with a long conversation writes a handoff of anything unfinished, then starts fresh. You can bring the old conversation back.

**Your business, known to everyone**
- **Company profile.** Your business name, owner, address, hours, time zone, currency and more, given to every team member. Change it in Settings.
- **Company knowledge.** Add your documents and policies in Memory & Knowledge: Word, Excel, PowerPoint, PDF, and on a Mac, scans or photos. Every team member can search them by words, and by meaning when MemPalace is installed, so "money back" finds your refund policy.

**Private folders**
- Michael works in your business folder, and each team member works in its own folder inside it.
- A team member opens only its own folder. Michael can read his team's folders but not change them. On a Mac, Claude Code's sandbox and the app both enforce this. On Windows, the app checks Claude's file tools, but shell commands are not limited yet.

**Also**
- **Updates.** The app tells you when a new version is out and links to the download.
- **Claude Code updates.** When Claude Code updates itself, team members already running stay on the old version until they restart. A "team upgrade ready" chip and note offer to close the office the safe way (everyone saves first) and reopen on the new version. Nothing restarts until you click.

<div align="right">(<a href="#what-it-is">↑ back to top</a>)</div>

## Getting started

### What you need

- A Mac with Apple Silicon or Intel, or a Windows 11 PC (x64).
- [Claude Code](https://claude.com/claude-code), signed in to your Claude plan. A Claude Max plan
  keeps the office running all day; smaller plans reach their usage limit during the day, and the
  office waits until it resets. No Claude plan? An Anthropic API key works too, billed to your
  Anthropic account. You don't need to install anything first: setup ends on **Get Michael
  ready**, which installs Claude Code and signs you in. Skip it, and Needs you keeps a card that
  opens the same step until Michael can start.

### Install

**On a Mac**

1. Download the `.dmg` from the [latest release](https://github.com/agentvivekkumar/dontbemichael/releases/latest).
2. Open it and drag **Don't Be Michael** into your Applications folder.
3. Open it from Applications. The first time, macOS says it could not verify the app. Click
   **Done**, then open **System Settings → Privacy & Security**, scroll to the message about Don't
   Be Michael and click **Open Anyway**.

You only do step 3 once. macOS asks because this early build is not yet signed with an Apple
Developer ID. Setup takes it from there.

**On Windows 11**

1. Download the file ending in `-win-x64-setup.exe` from the same [latest release](https://github.com/agentvivekkumar/dontbemichael/releases/latest).
2. Open it. The first time, Windows says **Windows protected your PC**. Click **More info**, then
   **Run anyway**.

You only do step 2 once. Windows asks because this build is not yet signed with a Microsoft
certificate. It runs on Windows 11 PCs with x64 processors; ARM PCs aren't supported. Linux will
follow.

## Your data

- **It stays on your computer.** Your team's work, memory and files live in folders on your
  computer. The team members themselves run through your own Claude Code and Claude plan, or
  your Anthropic API key.
- **No usage data.** The app sends nothing about how you use it. See [`TELEMETRY.md`](./TELEMETRY.md).

## For developers

Don't Be Michael is an Electron app (React, TypeScript, xterm.js, node-pty). Each team
member is a real Claude Code process in its own terminal. The team coordinates through the hive,
a folder of plain files with a mailbox, memory and a task board per agent; only the app commits to
it.

### Prerequisites and setup

To build and run the local multi-agent harness from source, you need:

- **Node.js 18 or newer** and npm.
- **C/C++ compiler toolchain** for building native addons like `node-pty`:
  - On macOS: run `xcode-select --install`.
  - On Windows: install Visual Studio C++ Build Tools (see [`node-pty`'s prerequisites](https://github.com/microsoft/node-pty#dependencies)).
  - On Linux: install build tools such as `build-essential`, `python3`, and `make`.
- **[Claude Code](https://claude.com/claude-code)** installed on your `PATH` (`claude`), signed in to a Claude plan, or an Anthropic API key (`ANTHROPIC_API_KEY`).

#### Install and launch

1. Clone the repository and navigate into the folder:
   ```bash
   git clone https://github.com/agentvivekkumar/dontbemichael.git
   cd dontbemichael
   ```
2. Install dependencies (the postinstall step automatically rebuilds `node-pty` for Electron):
   ```bash
   npm install
   ```
3. Start the application in development mode with live reloading:
   ```bash
   npm run dev
   ```

#### Helpful development commands

```bash
npm run typecheck     # type check main, preload and renderer
npm run test:focused  # run the node:test suite in test/
npm run build         # production build in out/
npm run dist:mac      # build macOS installer in dist/
npm run dist:win      # build Windows installer in dist/
npm run dist:linux    # build Linux AppImage in dist/
```

#### Configuring the harness

When the app launches for the first time, the onboarding flow sets up your local harness:
- **Business details**: Enter a business name and headquarters. The app sets up your primary business folder at `~/Documents/<BusinessName>`.
- **Suggested team**: Pick an Office Pack (such as Pro Services, SaaS/Consulting, Retail Shop, or Restaurant) to seed roles and starter tasks.
- **Get Michael ready**: The harness checks for an authenticated `claude` CLI on your system path. If you do not have a Claude account subscription, you can enter an Anthropic API key instead.

### Quick start: running your first agent

Once the office opens, here is how to get your multi-agent team working right away:

1. **Meet Michael (Office Manager)**:
   Michael sits in the glass office at the center of the office floor. He is your orchestrator and primary contact. When you talk to Michael, he decides who handles the work and keeps the task board updated.

2. **Add your first agent**:
   - Click **+ Add agent** on the office floor (or keep the starter team from setup).
   - In the hire wizard, choose a character (such as Kelly for Customer Support or Pam for Executive Admin).
   - Review the role description and work style. The app verifies that no two teammates have overlapping duties.
   - Click **Hire**. The app creates a private workspace folder for the agent and spins up their dedicated Claude Code process in its own terminal.

3. **Assign a task**:
   - In the **Talk to Michael** input box at the bottom, type a request such as:
     `"Ask Kelly to draft a customer welcome email for new signups."`
   - Michael receives the request, logs it on the task board, and routes a message to Kelly's inbox.

4. **Watch the agent work in real time**:
   - Click on the agent's pod on the office floor.
   - Switch to the **Work** tab to watch their live terminal session. You can see Claude Code read files, run tools, and draft responses.
   - Switch to the **Memory** tab to view notes the agent records as they complete tasks.

5. **Talk 1:1 directly**:
   - If you want to work with a team member directly without going through Michael, select their card and click **Talk 1:1**.
   - Michael holds off on assigning other work to that teammate until you finish your 1:1 session.

### Folder structure

Understanding how files and directories are organized helps when contributing or debugging:

#### Codebase layout

| Directory | Purpose |
|---|---|
| `src/main/` | Electron main process: PTY process manager (`pty.ts`), hook server (`hooks.ts`), hive multi-agent coordinator (`hive.ts`), configuration (`config.ts`), secret storage (`integrations.ts`), and native bridges. |
| `src/preload/` | Secure IPC bridge using Electron `contextBridge` to expose the typed `window.cth` API to the renderer. |
| `src/renderer/` | React front end: SVG office floor studio (`scene/studio/`), character avatars, xterm.js terminal integration, Kanban task board, panels, and Zustand state stores. |
| `src/shared/` | Shared TypeScript code used by both main and renderer: agent definitions, Office Pack schemas, mailbox models, and feature flags (`buildFeatures.ts`). |
| `resources/packs/` | Bundled Office Packs (`core.json`, `pro-services.json`, `saas.json`, etc.) with department roles, starter instructions, and schedules. |
| `hive/` | Specifications and contracts for autonomous multi-agent coordination, message schemas, and shared memory. |
| `test/` | Complete `node:test` suite verifying cross-platform compatibility, file safety, hook routing, and platform rules. |
| `docs/` | Architecture guides, design documentation, and feature changelogs. |

#### Runtime workspace layout

When the harness is running, it organizes runtime files on your computer:

```
~/Documents/<BusinessName>/       # Root business directory (filing cabinet)
  ├── Michael's workspace         # Michael reads the root directory and department folders
  ├── Executive Admin/            # Private working folder for Executive Admin
  │   └── ...                     # Department files, notes, and outputs
  └── Customer Support/           # Private working folder for Customer Support
      └── ...                     # Inquiries, drafts, and customer docs

<harnessHome>/hive/               # Multi-agent coordination directory
  ├── registry.json               # Roster: active agents, roles, and status
  ├── tasks.json                  # Central task ledger
  ├── board.md                    # Shared blackboard for cross-agent plans
  └── agents/<agentId>/           # Per-agent coordination folder
      ├── identity.md             # Role, prompt, and capabilities
      ├── memory.md               # Persistent long-term memory notes
      ├── inbox/                  # Incoming messages delivered by the router
      └── outbox/                 # Outgoing messages waiting for delivery
```

### Troubleshooting common issues

#### 1. Native `node-pty` build or `NODE_MODULE_VERSION` error
- **Symptom**: App fails to start with an error like `The module '...node-pty.node' was compiled against a different Node.js version` or native compilation fails during installation.
- **Cause**: `node-pty` includes native C/C++ bindings that must be compiled specifically for Electron's Node ABI version.
- **Fix**: Make sure your C/C++ compiler tools are installed (`xcode-select --install` on macOS, Visual Studio Build Tools on Windows, or `build-essential` on Linux). Then run `npm install` again, which automatically runs `electron-rebuild`.

#### 2. Claude Code CLI not found or login expired
- **Symptom**: Agent terminals fail to boot, or the setup screen says Claude Code is not ready.
- **Cause**: The `claude` executable is not installed globally on your system `PATH`, or your session is logged out.
- **Fix**: Verify that `claude --version` runs in your terminal. If missing, install it with `npm install -g @anthropic-ai/claude-code` and run `claude` once to complete sign in. Alternatively, enter your Anthropic API key in Settings or the setup wizard.

#### 3. Platform file locks or antivirus alerts on Windows
- **Symptom**: Intermittent `EPERM` or file lock errors when the app writes configuration or creates new agent directories.
- **Cause**: External tools such as antivirus software or search indexers can briefly hold open handles to freshly created files.
- **Fix**: The main process includes automatic retry logic for transient file locks, but adding an exclusion for your business workspace directory in active security tools can prevent timing conflicts.

#### 4. Paths with spaces
- **Symptom**: Commands fail or paths are truncated if your user folder or business directory contains spaces.
- **Cause**: Unquoted paths in shell invocations.
- **Fix**: The harness uses quoted paths and Node path helpers (`path.join`). If you write custom scripts or tools, always wrap directory paths in quotes.

### Where to read next

- [`docs/FEATURES.md`](./docs/FEATURES.md): every feature, and every change release by release.
- [`docs/ARCHITECTURE.md`](./docs/ARCHITECTURE.md): diagrams and the module map.
- [`HIVE.md`](./HIVE.md): how agents coordinate.
- [`SPEC.md`](./SPEC.md): the original spec. Its terminal and event planes still hold; the pixel canvas and command bar it describes were replaced by the Studio.
- [`branding/DESIGN.md`](./branding/DESIGN.md): the design system, for any new UI.

### What this build leaves out

Setup offers only Claude Code, signed in with a Claude account or an Anthropic API key. The code
still carries presets for other agent CLIs (Codex, Gemini, Grok, Kimi, Qwen, OpenCode, Crush, pi,
Copilot and Cursor), API keys for other providers and local models,
but this build doesn't offer them. Some developer features are switched off because business
owners don't use them: git views, the built in code editor, temporary helper agents, voice, and
opening a Terminal in an agent's folder. Each one has a switch in
[`src/shared/buildFeatures.ts`](./src/shared/buildFeatures.ts).

## Contributing

Contributions are welcome. Start with [`CONTRIBUTING.md`](./CONTRIBUTING.md). Found a bug or have an
idea? [Open an issue](https://github.com/agentvivekkumar/dontbemichael/issues).
[`CONTRIBUTORS.md`](./CONTRIBUTORS.md) lists everyone with a merged pull request. Changes are in
[`CHANGELOG.md`](./CHANGELOG.md).

## License

The **source code** is licensed under the **MIT License**. See [`LICENSE`](./LICENSE). The original
copyright notice of Munder Difflin, the project this grew out of, is kept in `LICENSE`, as the
MIT license requires.

*Don't Be Michael* is not affiliated with NBC, *The Office*, or Dunder Mifflin.

## Acknowledgements

- [Munder Difflin](https://github.com/chaitanyagiri/munder-difflin) by Chaitanya Giri and its contributors, the open-source project this product grew out of.
- [xterm.js](https://xtermjs.org/) · [node-pty](https://github.com/microsoft/node-pty) · [electron-vite](https://electron-vite.org/) · [CodeMirror](https://codemirror.net/) for the libraries this is built on.
