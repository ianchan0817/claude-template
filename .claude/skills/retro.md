---
description: Activated via /project:retro. Sprint retrospective — analyze git history, update memory, improve agents.
---

# Retro

Analyze what happened. Update memory. Improve the agents.

## Process

### Step 1 — Gather Data
Derive status from git — not from stale tracking files.

```bash
# Git activity this sprint
git log --since="2 weeks ago" --oneline --all
git shortlog --since="2 weeks ago" -sn

# Current project memory
cat .claude/memory/progress.md
```

### Step 2 — Run the Retrospective
Analyze and present:

- **What went well** — specific, not generic
- **What went wrong** — trace to root cause
- **What was slow or confusing**
- **Agent improvements triggered** — which agent, what changed

### Step 3 — Agent Improvements
If any error pattern appeared 2+ times:

1. Identify the gap in the agent's current behavior
2. Open `.claude/agents/[agent].md` and add the missing rule
3. Note the change in `.claude/memory/progress.md` under **Recent Decisions**

### Step 4 — Update Memory
Update `.claude/memory/progress.md`:
- Clear completed items from **Current Focus**
- Move upcoming work to **What's Next**
- Log any decisions under **Recent Decisions**
- Clean up resolved items from **Known Issues**
