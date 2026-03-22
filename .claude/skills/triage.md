---
description: Automatically activated at the start of any complex or ambiguous request to route it to the right agent or workflow. Triggers when a request spans multiple domains, is unclear about who should handle it, or involves a new initiative. Prevents the wrong agent from picking up work meant for another.
---

# Triage

Before handling any complex request, silently determine the right agent and workflow. Do not answer the request directly if a specialist agent should own it.

## Routing Map

| Request type | Route to |
|-------------|---------|
| New feature / initiative / "I want to build X" | `cto` → product direction review → `product-manager` |
| "What should we build?" / prioritization | `product-manager` |
| "How should this look?" / UX / mobile | `ux-designer` |
| "How should this be designed?" / architecture | `architect` |
| Task breakdown / sprint planning | `engineering-manager` |
| Backend implementation | `backend-engineer` |
| Frontend implementation | `frontend-engineer` |
| "Does this work?" / QA / testing | `qa-manager` |
| Deploy / infra / DB / performance | `devops-manager` |
| "Is this secure?" / auth / data | `security-manager` |
| Error / bug / incident | `scrum-master` logs first → route to responsible engineer |
| Retro / process / team health | `scrum-master` |
| Daily summary / department review | `cto` → `/project:daily-report` |

## Triage Decision

For every incoming request:
1. Identify the **primary domain** (product, design, engineering, QA, infra, security, process)
2. Identify the **right agent** from the map above
3. If the request spans multiple domains → start with `cto` to coordinate
4. If unclear → ask one clarifying question before routing

## Fast-path rules

- "Build X" → always starts with a product direction review (confirm we're building the right thing) + `product-manager` before any implementation
- "Fix X" → `scrum-master` logs the error first, then route to the responsible engineer
- "Review X" → `engineering-manager` for code, `qa-manager` for E2E, `security-manager` for security
- "Ship X" → confirm: code review done? E2E sign-off received? Then ship.
- "What's the status?" → `cto` → `/project:daily-report`
