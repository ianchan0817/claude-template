---
description: Activated via /project:retro. Sprint retrospective — analyze, log, improve. Run after every sprint or major release.
---

# Retro

Analyze what happened. Log everything. Improve the agents.

## Process

### Step 1 — Gather Data
```bash
# Git activity this sprint
git log --since="2 weeks ago" --oneline --all
git shortlog --since="2 weeks ago" -sn

# Errors
cat .claude/retrospectives/error-log.md

# Open action items
cat .claude/retrospectives/action-items.md

# Agent improvements
cat .claude/retrospectives/agent-improvements.md
```

### Step 2 — Run the Retrospective
Write to `.claude/retrospectives/retro-YYYY-MM-DD.md`:

```markdown
# Retrospective — YYYY-MM-DD

## Errors this sprint
| ERR | Title | Severity | Resolved? |
|-----|-------|----------|-----------|

## What went well

## What went wrong

## What was slow or confusing

## Agent improvements triggered
- [agent]: [change] → ERR-NNN

## Action items
| # | Action | Owner | Due | Status |
|---|--------|-------|-----|--------|
```

### Step 3 — Agent Improvements
If any error pattern appeared 2+ times:

1. Identify the gap in the agent's current behavior
2. Open `.claude/agents/[agent].md` and add the missing rule
3. Log the change in `.claude/retrospectives/agent-improvements.md`

### Step 4 — Update Sprint
Update `.claude/context/sprint.md` for the next sprint:
- Move completed items to "Done"
- Carry over in-progress items
- Add new backlog candidates

### Step 5 — Close Action Items
Review `.claude/retrospectives/action-items.md`:
- Close items that are merged or verifiably complete
- Escalate overdue items to manager
