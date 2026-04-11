---
description: Activated via /project:review. Pre-landing code review on the current branch. Two-pass — critical issues first, then informational.
---

# Review

Pre-merge code review. Find bugs, security holes, and quality issues before they ship.

## Context

Current branch:
```
$(git branch --show-current)
```

Diff against main:
```
$(git diff origin/main --stat 2>/dev/null | head -30)
```

## Process

### Pass 1 — Critical Issues
These block merge:

- **Bugs** — incorrect logic, race conditions, unhandled errors
- **Security** — injection, XSS, auth bypass, data leaks, missing validation
- **Performance** — N+1 queries, unbounded queries, missing indexes, blocking main thread
- **Trust boundaries** — client data trusted without validation, privilege escalation paths
- **Test gaps** — uncovered branches, missing error path tests, coverage below 100%

### Pass 2 — Informational
Author's discretion:

- Code quality — naming, structure, duplication
- Maintainability — function length, complexity, readability
- Consistency — style, patterns, conventions

## Review Checklist

### Correctness
- [ ] All use cases implemented and tested
- [ ] Edge cases handled
- [ ] Error paths explicit

### Security
- [ ] Auth enforced on protected routes
- [ ] Authorization at data layer
- [ ] Input validated, queries parameterized
- [ ] No XSS vectors

### Performance
- [ ] No N+1, no unbounded queries
- [ ] Indexes for hot query paths

### Coverage
- [ ] 100% on new/modified code
- [ ] Tests describe behavior, not implementation

### Maintainability
- [ ] Single responsibility
- [ ] No dead code
- [ ] Names are precise

## Output

Surface all critical findings with file, line, and explanation. Require resolution before merge.

**Do not approve a merge with open critical issues.**
