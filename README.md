# CLAUDE.md + BACKLOG.md: An Agentic Coding Workflow

A simple two-file system that lets [Claude Code](https://docs.anthropic.com/en/docs/claude-code) work through your project autonomously — reading what to build, writing code, running tests, committing, and moving to the next task — while you stay in control of *what* gets built and *when*.

This workflow was developed by a non-technical person who used it to build and ship a native iOS app from scratch in four weeks. No prior coding experience required.

---

## The idea

Most people use Claude Code by typing prompts one at a time. That works, but it means you're always in the loop, deciding what to do next.

This workflow flips that. You invest time upfront writing two documents — a project spec and a task list — and then Claude Code can work through them on its own. You step back from *how* and focus on *what*.

**`CLAUDE.md`** is your project spec. It tells Claude Code everything about your project: what you're building, how the app should look and behave, what technology to use, what rules to follow, and how to work autonomously. Think of it as a brief you'd hand to a developer on their first day.

**`BACKLOG.md`** is your task list. It's split into three sections — Next Up (do these now), Later (don't touch yet), and Done (completed work). Claude Code reads this file, picks up the next unchecked item, builds it, tests it, commits it, marks it done, and moves on.

Together, they create a loop where Claude Code can work through multiple tasks without you typing a single prompt.

---

## What's in this repo

| File | What it is |
|---|---|
| `template_CLAUDE.md` | A blank template for your project spec. Fill in the sections for your own project. |
| `template_BACKLOG.md` | A blank template for your task backlog. Add your own items. |
| `agentic-coding-project-overview.pdf` | A presentation walking through how this workflow was used to build a real app, with screenshots and examples. |

---

## How to use it

### 1. Set up your project

Create a new folder for your project. Copy `template_CLAUDE.md` and `template_BACKLOG.md` into the root and rename them to `CLAUDE.md` and `BACKLOG.md`.

```
your-project/
├── CLAUDE.md
├── BACKLOG.md
└── ... (your code goes here)
```

### 2. Fill in CLAUDE.md

This is where you spend most of your upfront time. Work through each section of the template with Claude Chat (claude.ai) as your thinking partner. Claude Chat can help you:

- Write a clear project overview and elevator pitch
- Define your screens and features
- Choose a tech stack
- Design wireframes
- Research APIs
- Draft architecture decisions and guardrails

The template includes placeholder sections — fill in what's relevant to your project and delete what isn't. The more specific your CLAUDE.md, the more autonomously Claude Code can work. Ambiguity in the docs leads to guesswork in the code.

### 3. Write your first backlog items

Add specific tasks to the **Next Up** section of `BACKLOG.md`. Each item should have a bold name and a detailed description. Claude Chat can help you break a feature down into individual tasks with clear success criteria.

Good backlog items are specific and self-contained. Instead of "Build the home screen", try something like "Create the home screen view with a scrollable list of cards, each showing the station name and line badge. Use the design tokens from the Design Language section of CLAUDE.md."

### 4. Run Claude Code

Open your terminal, navigate to your project folder, and start Claude Code. Then give it this prompt:

```
Read CLAUDE.md and BACKLOG.md in the project root. CLAUDE.md contains your
full project context and an "Autonomous workflow" section that describes
exactly how to process backlog items. Follow that workflow now — work through
every unchecked item in the "Next Up" section of BACKLOG.md, one at a time,
in order from top to bottom. For each item: plan the change, implement it,
build to confirm zero errors, commit, then mark it done in BACKLOG.md and
commit that update. Stop and report when all Next Up items are complete.
Start this sprint with a new feature branch.
```

Claude Code will read both files, understand your project, and start working through the backlog items one by one.

### 5. Between phases

When Claude Code finishes all the Next Up items, use this prompt to keep the documentation current:

```
Update CLAUDE.md with any changes or context that should be carried forward
to future phases. Then prepare BACKLOG.md for the next phase. Then commit
and push to the current feature branch.
```

Then move items from **Later** into **Next Up**, add detail to them (with Claude Chat's help), and run the start-of-phase prompt again.

---

## The autonomous workflow loop

The `template_CLAUDE.md` includes a full **Autonomous workflow** section that tells Claude Code how to process each backlog item. The loop is:

1. **Read the backlog** — find the next unchecked item in Next Up
2. **Plan before coding** — state which files will change, what the change involves, flag any risks
3. **Implement the change** — make the smallest set of changes needed, follow existing patterns
4. **Self-review** — check for duplicated logic, unnecessary code, and naming consistency
5. **Build and test** — must pass with zero errors and zero warnings
6. **Commit and update backlog** — one commit per item, then mark it done in a separate commit
7. **Move to the next item** — repeat until Next Up is empty

Key rules that keep things safe:
- One item at a time — finish and commit before starting the next
- Do not touch Later items — only work on Next Up
- Do not refactor unrelated code — stay focused
- If the build breaks, fix it before moving on
- If unsure about a design decision, stop and ask

---

## Tips for non-developers

**Use Claude Chat (claude.ai) as your thinking partner.** Don't try to fill in CLAUDE.md alone. Open a Claude Chat conversation, describe your idea, and let it ask you clarifying questions. It can draft the entire project spec and backlog items for you — you just review and refine. If you have a Notion project, give Claude Chat read access via the Notion connector so it can build context from your existing notes.

**Start simple.** Your first project should have no API, no accounts, no external services. A timer app, a calculator, a personal dashboard — something where the worst case is it doesn't work, not that it breaks something. Add complexity incrementally across projects.

**Limit the blast radius.** Use your personal laptop, your personal Claude account. No work tech involved. No money tied to APIs (start with free tiers). No personal information stored in the app. Claude Code is sandboxed — it can't take actions outside your project folder without asking.

**Invest in documentation before code.** It's tempting to jump straight to "build me an app." Resist. The time you spend on CLAUDE.md pays back tenfold in autonomous coding quality. A well-written CLAUDE.md can support 30-minute autonomous coding sessions with zero intervention.

**Test on a real device.** Claude Code can build and run tests, but it can't see your app. After each phase, test the app yourself and note anything that's wrong. Feed those observations back to Claude Chat to generate bug-fix backlog items.

**One commit per backlog item.** This makes it trivially easy to undo any single change if something goes wrong. Your main branch should always be in a deployable state.

---

## Tools used in this workflow

| Tool | Role |
|---|---|
| **Claude Chat** (claude.ai) | Thinking partner. Drafts project specs, wireframes, backlog items. Answers "why" questions. |
| **Claude Code** (terminal) | Coding agent. Reads CLAUDE.md and BACKLOG.md, writes code, runs builds, commits to Git. |
| **Git / GitHub** | Version control. One commit per backlog item. Feature branches per phase. |
| **Notion** *(optional)* | Project management. Store your project brief, screen list, data model, and other reference docs. Give Claude Chat read access via the Notion connector. |

---

## Adapting the template

The `template_CLAUDE.md` was designed for an iOS app built with Swift and Xcode. If you're building something different, adapt the template to your stack:

- **Web app?** Replace the Xcode build commands with your framework's build/test commands. Replace "Screens" with "Pages" or "Routes."
- **Python script?** Simplify heavily — you might only need Project Overview, Core Features, Architecture, and the Autonomous Workflow section.
- **No idea what stack to use?** Ask Claude Chat. Describe what you want to build and it will recommend a tech stack and help you fill in the Architecture section.

The structure of the workflow — spec in CLAUDE.md, tasks in BACKLOG.md, autonomous loop — works regardless of what you're building.

---

## Learn more

- [Claude Code documentation](https://docs.anthropic.com/en/docs/claude-code)
- [CLAUDE.md best practices](https://docs.anthropic.com/en/docs/claude-code/memory#claudemd)
- See `agentic-coding-project-overview.pdf` in this repo for a full walkthrough with screenshots from a real project build
