# Retro

Run the sprint or post-delivery retrospective.

## Instructions

**Step 1 — Data**
Analyze git log, commit history, work patterns, test ratios, and contributor activity.

**Step 2 — Scrum master layer**
The `scrum-master`:
1. Reviews `.claude/retrospectives/error-log.md` — any unresolved or recurring patterns?
2. Reviews `.claude/retrospectives/action-items.md` — any overdue items?
3. Checks `.claude/retrospectives/agent-improvements.md` — any agent updates triggered?
4. Writes the retro doc to `.claude/retrospectives/retro-YYYY-MM-DD.md`
5. Updates `.claude/context/sprint.md` for the next sprint

**Step 3 — Agent improvements**
If any error pattern appeared 2+ times this sprint, `scrum-master` updates the responsible agent file and logs the change in `agent-improvements.md`.
