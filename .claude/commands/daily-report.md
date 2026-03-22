# Daily Executive Summary

Run the CTO's daily department review and generate an executive summary for the owner.

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

Recent agent improvements:
```
$(cat .claude/retrospectives/agent-improvements.md 2>/dev/null)
```

Product specs in flight:
```
$(ls .claude/product/specs/ 2>/dev/null)
```

## Instructions

You are the CTO. Review all signals above and produce the daily executive summary.

Follow the report format in `.claude/agents/cto.md` under "Daily Executive Summary".

Save the report to `.claude/reports/daily-YYYY-MM-DD.md` (use today's actual date).

Then present the full report to the owner. Be direct. Lead with the most important thing. Never bury bad news. End with what you need from them today.
