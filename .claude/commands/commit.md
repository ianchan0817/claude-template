# Ship

Land the current branch.

## Pre-conditions (must be true before shipping)
- [ ] Code review has been run and all critical issues resolved
- [ ] `qa-manager` E2E sign-off received
- [ ] 100% unit test coverage on new/modified code

## Instructions

1. Sync with main — rebase or merge, resolve any conflicts
2. Run the full test suite — confirm all tests pass
3. Bump VERSION and update CHANGELOG if the repo uses them
4. Commit any outstanding changes with a clear, descriptive message
5. Push the branch
6. Open or update the PR

**Do not ship a branch that has not passed code review and E2E sign-off.**
