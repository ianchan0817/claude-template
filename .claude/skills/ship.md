---
description: Activated via /project:ship. Land the current branch — sync, test, version, commit, push, PR.
---

# Ship

Land the current branch.

## Pre-conditions (all must be true)
- [ ] Code review done, all critical issues resolved (`/project:review`)
- [ ] E2E sign-off received (`/project:e2e`)
- [ ] 100% unit test coverage on new/modified code
- [ ] Security review done for auth/data/API changes (`/project:security`)

## Process

1. Sync with main — rebase or merge, resolve conflicts
2. Run the full test suite — confirm all pass
3. Bump VERSION and update CHANGELOG if the repo uses them
4. Commit with a clear, descriptive message
5. Push the branch
6. Open or update the PR

**Do not ship a branch that has not passed review and E2E sign-off.**

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "It's a small change" | Small changes break production too |
| "Tests passed locally" | CI is the source of truth |
| "We can hotfix later" | Hotfixes skip process, compounding risk |
