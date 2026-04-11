---
description: Activated via /project:e2e. E2E quality assurance — full user journey testing, release sign-off. Run before every ship.
---

# E2E

End-to-end quality assurance. Validate that the full system works for real users.

## Context

Current branch:
```
$(git branch --show-current)
```

Files changed vs main:
```
$(git diff origin/main --stat 2>/dev/null | head -20)
```

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "Unit tests are enough" | Units pass, integration breaks |
| "We tested it manually" | Manual testing doesn't scale or persist |
| "E2E tests are slow" | Broken user journeys are slower to fix in production |

## Process

### Step 1 — Identify affected journeys
From the diff, determine which user flows are affected.

### Step 2 — Run E2E suite
**On a feature branch:** Target affected routes and pages.
**For staging sign-off:** Run the full regression suite.
**For a specific flow:** Navigate, interact, screenshot, check console.

Use the project's headless browser framework (Playwright, Cypress).

### Step 3 — Write new journey tests
For each new feature, document:

```markdown
## E2E: [Feature]

### Journey: [Name]
| Step | Action | Expected |
|------|--------|----------|
| 1 | Navigate to [page] | Page loads |
| 2 | Enter [input] | Validation passes |
| 3 | Submit | API 200, data saved |
| 4 | UI updates | New state visible |
```

### E2E Test Rules
- Each test sets up its own state — no shared mutable state
- Use `data-testid` for selectors — never CSS classes or text
- No `sleep()` — use `waitFor`, retry assertions
- Tests must pass 3 consecutive times to be stable
- Flaky tests are bugs — quarantine, diagnose, fix, restore

### Step 4 — Release Sign-off

- [ ] All E2E journeys passing in staging
- [ ] Full regression suite green
- [ ] No quarantined tests in changed area
- [ ] New feature journeys added
- [ ] No accessibility violations
- [ ] Performance within range
- [ ] Rollback tested

**No sign-off if any item is red.**

### Step 5 — Log findings
- Bugs → `.claude/retrospectives/error-log.md`
- Every production bug that escaped gets an E2E test before fix is closed

## Bug Triage

| Severity | Action |
|----------|--------|
| Critical | Block release, notify manager |
| High | Block release |
| Medium | Fix this sprint |
| Low | Backlog |
