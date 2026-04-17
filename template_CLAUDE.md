# CLAUDE.md — [PROJECT NAME]

---

## Project overview

<!-- Fill in the basics so Claude Code immediately understands what it's working on. Ask Claude Chat to help you refine these if you're unsure — describe your idea in plain language and it will ask clarifying questions. -->

**App name:** <!-- What's your project called? -->
**Platform:** <!-- e.g. iOS, web, macOS, Android, CLI tool -->
**Distribution:** <!-- How will people get it? e.g. TestFlight, App Store, hosted on Vercel, runs locally -->
**Users:** <!-- Who is this for? Be specific. e.g. "London commuters who already know their stations and lines" -->

**Elevator pitch:** <!-- One or two sentences describing what the app does and why someone would use it. e.g. "A customisable transit companion for London — save the stations and lines you care about, see live departures at a glance, and nothing else." -->

---

## Core features

<!-- List what the app must do in its first version (MVP) and what it should explicitly NOT do yet. This prevents Claude Code from over-building. Use Claude Chat to help you refine this — describe your idea and ask it to help you separate must-haves from nice-to-haves. -->

### Must have
<!-- These are the features that make the app worth using. Be specific about behaviour, not just names. -->
- <!-- e.g. "Home screen cards — each saved view is a modular card showing real-time arrival data for a specific station, filtered to the user's chosen lines and destinations" -->
- <!-- e.g. "Search — search for any station via API, then pick which lines and destinations to track" -->
- <!-- e.g. "Offline support — show cached data with a stale-data banner when offline" -->

### Out of scope for MVP
<!-- Things you might want later but should NOT be built now. This is just as important as the must-haves — it stops Claude Code from adding features you didn't ask for. -->
- <!-- e.g. "User accounts, log-ins, or cloud sync" -->
- <!-- e.g. "Push notifications" -->
- <!-- e.g. "Route planning or journey directions" -->

---

## Screens

<!-- Describe every screen in the app: what the user sees, what they can do, and how they navigate to other screens. Include wireframe references if you have them (e.g. "See wireframes/home.png"). Claude Chat can design wireframes for you — ask it to propose screens based on your features, then iterate.

Add or remove screen sections to match your app. Sub-screens (like modals or drill-downs) can be numbered as 1a, 1b, etc. -->

### Screen 1: [Name]
<!-- What does this screen show? What can the user do here? Where can they navigate to? e.g. "The main screen. A scrollable list of saved view cards, each showing live arrival times. Tap a card to drill down (→ Screen 3). Tap + to add a new view (→ Screen 2). Long-press for edit/delete options." -->

### Screen 2: [Name]
<!-- Same as above — describe what the user sees and does. -->

### Screen 3: [Name]

### Screen 4: [Name]

---

## Design language

<!-- Define the visual identity of your app. This table gives Claude Code concrete values to use instead of guessing. Claude Chat can help you choose a colour palette and typography if you don't have preferences yet.

Add rows for whatever matters to your project. Common elements include colours (primary, secondary, background, text, error, success), fonts, corner radii, spacing, and icon style. -->

| Element | Value |
|---|---|
| <!-- e.g. Primary colour --> | <!-- e.g. #1A2B3C --> |
| <!-- e.g. Background --> | <!-- e.g. System background (adaptive light/dark) --> |
| <!-- e.g. Font family --> | <!-- e.g. SF Pro (system default) --> |
| <!-- e.g. Corner radius --> | <!-- e.g. 12pt for cards, 8pt for buttons --> |
| <!-- e.g. Spacing unit --> | <!-- e.g. 8pt grid --> |

---

## Architecture

<!-- This section tells Claude Code what technology to use and how the project is structured. If you're not sure what to put here, ask Claude Chat: "I want to build [your idea]. What tech stack would you recommend and why?" It will suggest options and explain the tradeoffs. -->

### Technology
<!-- Replace or remove lines that don't apply to your project. Add any that are missing. -->
- **Language:** <!-- e.g. Swift, TypeScript, Python -->
- **UI framework:** <!-- e.g. SwiftUI, React, Next.js, Flask -->
- **Minimum target:** <!-- e.g. iOS 17+, Node 20+, Python 3.11+ -->
- **Networking:** <!-- e.g. URLSession, fetch API, requests library -->
- **Data sources:** <!-- e.g. TfL Unified API, local JSON files, PostgreSQL -->
- **Storage:** <!-- e.g. Local JSON files, SQLite, UserDefaults, localStorage -->
- **Testing:** <!-- e.g. XCTest, pytest, Jest -->
- **Build tool:** <!-- e.g. Xcode, Vite, npm, pip -->

### File structure
<!-- Show the folder layout of your project. This helps Claude Code know where to put new files. Update this as the project grows. -->
```
project/
├── CLAUDE.md
├── BACKLOG.md
├── wireframes/              ← Screen wireframes (PNG or SVG)
├── assets/                  ← Logos, icons, and brand assets
│
```

### Key data models (summary)

<!-- Once your project has data models (defined in code), summarise the key ones here with any conventions or non-obvious details. This section is usually empty at the start and gets filled in as you build. e.g. "SavedView stores a user's configured station/line combination. Uses Codable for JSON persistence. The lineSelections array can be empty (meaning all lines)." -->

---

## Current build phase

See `BACKLOG.md` for current and future work.

### Backlog

All upcoming work is tracked in **`BACKLOG.md`** in the project root:
- **Next Up** — the active sprint. Work items in order, top to bottom.
- **Later** — future work. Do not touch unless explicitly asked.
- **Done** — completed and committed items.

---

## Autonomous workflow

When working through backlog items, follow this loop for **each item** in the Next Up section:

### 1. Read the backlog
Open `BACKLOG.md` and identify the **next unchecked item** in "Next Up".

### 2. Plan before coding
State which files you'll modify, what the change involves, and any risks. If anything is ambiguous, **stop and ask** — do not guess.

### 3. Implement the change
<!-- Customise these rules for your project. The examples below are generic — replace them with specific instructions relevant to your codebase. The more specific you are, the fewer mistakes Claude Code will make. -->
- If wireframes exist in `wireframes/`, **always consult them** before building or modifying any screen
- Make the smallest set of changes needed
- Follow existing patterns — match the style of surrounding code
- <!-- Add project-specific rules here, e.g. "Use design tokens from AppColours — never add colour literals in views" -->
- <!-- Add project-specific rules here, e.g. "All API calls go through the ApiClient module" -->

### 4. Self-review before committing
After implementing but BEFORE committing, review your own changes and check:
- Did I duplicate any logic that already exists in the codebase? If so, extract it.
- Did I add any code not required by the backlog item? If so, remove it.
- Is every new function under 40 lines? If not, split it.
- Are my names consistent with surrounding code?

### 5. Build and test
<!-- Replace these with the actual build and test commands for your project. Claude Code needs the exact commands to run. -->
- **Build:** `[your build command here]`
<!-- e.g. "npm run build", "python -m py_compile main.py", "xcodebuild build -scheme MyApp ..." -->
- **Test:** `[your test command here]`
<!-- e.g. "npm test", "pytest", "xcodebuild test -scheme MyApp ..." -->
- Build must pass with zero errors and zero warnings
- If the change is visual, describe what to check on device or in the browser
- Run relevant unit tests and confirm they pass

### 6. Commit and update backlog
- One Git commit per backlog item: `feat: <short description>`
- Do not bundle multiple items into one commit
- Mark the item done in `BACKLOG.md` and move to Done section, then commit separately: `chore: mark "<item>" complete in BACKLOG.md`

### 7. Move to the next item
Repeat until all "Next Up" items are complete, then stop and report.

### Rules
- **One item at a time.** Finish and commit before starting the next.
- **Do not touch "Later" items.** Only work "Next Up".
- **Do not refactor unrelated code.** Stay focused on the current item.
- **If a change breaks the build, fix it before moving on.** `main` must always be deployable.
- **If unsure about a design decision, stop and ask.**

---

## Git branch naming

- `feature/<short-description>` for new features
- `fix/<description>` for bug fixes
- Commit directly to the current working branch. One commit per backlog item.
- `main` must be deployable at all times.

---

## Do not do

<!-- This is your guardrail list — tell Claude Code what it must NEVER do. Be specific and opinionated. These prevent the most common ways an AI coder can go off-track. Start with the examples below and add rules based on your project's needs. -->

- <!-- e.g. "Do not add user accounts, log-ins, or cloud sync — all data is local" -->
- <!-- e.g. "Do not introduce third-party packages or dependencies without discussion" -->
- <!-- e.g. "Do not hardcode API keys — read from environment variables or config files" -->
- <!-- e.g. "Do not make network requests to any service not listed in the Data Sources section" -->
- <!-- e.g. "Do not modify the database schema without flagging it first" -->

---

## Architecture decisions & context

<!-- As your project grows, document important decisions here so Claude Code understands WHY things are the way they are. This prevents it from "fixing" things that are intentional. e.g. "We use local JSON files instead of a database because the app is single-user and offline-first. Do not migrate to SQLite." or "Refresh intervals are set to 30 seconds to stay well within the API's rate limit of 500 requests per minute." -->

---

## Display rules

<!-- If your app has specific formatting or display conventions, document them here so Claude Code is consistent. e.g. "Dates are always displayed as 'DD MMM YYYY'. Times use 24-hour format. Currency values show two decimal places. Null values display as a dash (—), never 'N/A'." -->

---

## Attribution

<!-- If your app uses third-party data, APIs, or assets that require attribution, list the exact text or format required. e.g. "Display 'Powered by TfL Open Data' in the footer of every screen that shows TfL data." -->

---

## Testing patterns

<!-- Once you establish testing conventions, document them here so Claude Code writes tests consistently. e.g. "Every new data model gets a round-trip encode/decode test. Every API response model gets a test using a hardcoded JSON fixture matching real API output. UI tests are not used — visual changes are verified manually on device." -->

---
