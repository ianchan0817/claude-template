---
description: Activated via /project:spec. Defines what to build and why — use cases, prioritization, feature specs. Replaces the product-manager agent with a workflow-based skill. Always runs before design or implementation.
---

# Spec

Define the problem so precisely that the right solution becomes obvious.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "We already know what to build" | You know what was requested — not what's needed |
| "The spec will slow us down" | Building the wrong thing is slower |
| "We can figure it out as we go" | Scope creep and rework cost 3x |

## Process

### Step 1 — First Principles Challenge
Before writing anything, decompose the request:

1. **What is the user trying to accomplish?** (The job, not the feature)
2. **Why can't they do it today?** (The actual gap)
3. **Who has this problem?** (Specific segment)
4. **How frequent?** (Daily? Edge case?)
5. **Cost of not solving?** (User leaves? Revenue lost?)
6. **What does success look like, measurably?**
7. **What is the simplest thing that could work?**
8. **What are we explicitly NOT doing?**

### Step 2 — Use Case Document
Write to `.claude/product/use-cases/[feature-name].md`:

- Business context (problem, objective, success metric)
- User segments and frequency
- Jobs to be done (When [situation], I want to [action], so I can [outcome])
- Use cases with actor, preconditions, flow, postconditions
- Out of scope (with reasons)
- Open questions, dependencies, assumptions

### Step 3 — RICE Prioritization

| Factor | Score |
|--------|-------|
| Reach | Users affected per quarter |
| Impact | 0.25 / 0.5 / 1 / 2 / 3 |
| Confidence | 50% / 80% / 100% |
| Effort | Person-weeks |

**RICE = (Reach x Impact x Confidence) / Effort**

### Step 4 — Feature Spec
Write to `.claude/product/specs/[feature-name].md`:

- Problem, proposed solution, use cases addressed
- Acceptance criteria (Given/When/Then)
- Success metrics with baseline and target
- Constraints, out of scope, risks
- Integration impact (data dependencies, API surface changes, downstream effects)

### Step 5 — Handoff
Spec must be complete before `/project:plan` or `/project:design` begins:
- [ ] All open questions resolved
- [ ] Use cases documented with acceptance criteria
- [ ] Integration impact understood
- [ ] RICE score calculated

## Verification Gate
Do not proceed to planning or design until the spec has:
- A measurable success metric
- At least one complete use case with acceptance criteria
- Explicit out-of-scope items
