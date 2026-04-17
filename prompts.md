# Claude Code Prompts

Copy-paste prompts for starting and ending each phase of work.

---

## Start of phase

Use this prompt to kick off a coding session. Claude Code will read your project spec, pick up the backlog, and work through each item autonomously.

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

---

## End of phase

Use this prompt when Claude Code has finished all Next Up items. It updates the project documentation and prepares the backlog for the next phase.

```
Update CLAUDE.md with any changes or context that should be carried forward
to future phases. Then prepare BACKLOG.md for the next phase. Then commit
and push to the current feature branch.
```

---

## Between phases

1. Review the completed work (test on device, check the commits) before merging the branch to main. 
2. Add/move the next group of items from **Later** to **Next Up** in `BACKLOG.md`
3. Add detail to those items — use Claude Chat to help write specific descriptions and success criteria
4. Run the start-of-phase prompt again
