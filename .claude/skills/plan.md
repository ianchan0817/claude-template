---
description: Activated via /project:plan. Full planning sequence — architecture design, task breakdown, and sequencing. Runs after /project:spec confirms what to build.
---

# Plan

Architecture + task breakdown for a confirmed spec.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "Let's just start coding" | Rework from missing edge cases costs 5x |
| "We can refactor later" | Retrofitting architecture is 10x more expensive |
| "It's a small feature" | Small features with wrong architecture become big problems |

## Process

### Step 1 — Architecture Design
For every significant feature, work through:

1. **Use case** — read/write ratio, access pattern, consistency, latency, scale target
2. **Boundaries** — service responsibilities, APIs, data ownership, trust boundaries
3. **Sync vs async** — sync for immediate response; async for cross-service or deferrable
4. **Scale** — stateless services, horizontal scaling, circuit breakers, rate limiting
5. **Resilience** — timeouts, retries, dead-letter queues, idempotency
6. **Data** — schema from the query, indexes for hot paths, multi-tenant isolation
7. **Security** — threat model for anything touching auth, data, or external APIs

### Step 2 — ADR (if architectural decision involved)
Write to `.claude/decisions/ADR-NNN-title.md`:
- Context and scale assumptions
- Options considered with trade-offs
- Decision and reasoning
- Consequences (positive, negative, risks)

### Step 3 — Task Breakdown
Produce atomic, implementable tasks:

```markdown
## Feature: [Name]

### Tasks
- [ ] Task 1 — [S/M/L] — [description]
- [ ] Task 2 — [S/M/L] — [description]

### Test Tasks
- [ ] Unit tests for [module]
- [ ] Integration tests for [boundary]

### Dependencies
- Task 2 requires Task 1
- Needs security review for [component]

### Risks
- [Risk]: [Mitigation]

### Definition of Done
- [ ] 100% test coverage on new/modified code
- [ ] Code reviewed by reviewer
- [ ] E2E sign-off from reviewer
```

### Step 4 — Sprint Entry
Update `.claude/context/sprint.md` with the new work.

## Verification Gate
Do not begin implementation until:
- [ ] Architecture designed and documented
- [ ] Tasks broken down with estimates
- [ ] Dependencies identified and sequenced
- [ ] Definition of done agreed
