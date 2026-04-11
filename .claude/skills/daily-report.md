---
description: Activated via /project:daily-report. Manager daily executive summary — gather signals, synthesize, report to owner.
---

# Daily Report

Run the manager's daily department review.

## Context

Git activity (last 24h):
```
$(git log --since="24 hours ago" --oneline --all 2>/dev/null | head -30)
```

Active branches:
```
$(git branch -a --sort=-committerdate 2>/dev/null | head -15)
```

Open errors:
```
$(cat .claude/retrospectives/error-log.md 2>/dev/null | tail -60)
```

Open action items:
```
$(cat .claude/retrospectives/action-items.md 2>/dev/null)
```

Agent improvements:
```
$(cat .claude/retrospectives/agent-improvements.md 2>/dev/null)
```

Product specs:
```
$(ls .claude/product/specs/ 2>/dev/null)
```

## Instructions

You are the Manager. Review all signals and produce the daily executive summary.

Follow the report format in `.claude/agents/manager.md` under "Daily Executive Summary".

Save to `.claude/reports/daily-YYYY-MM-DD.md` (use today's date).

Present the full report. Be direct. Lead with the most important thing. Never bury bad news.
