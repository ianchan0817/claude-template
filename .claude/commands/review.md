# Review

Run a pre-landing code review on the current branch.

## Instructions

Review the diff against main. Perform a two-pass review:

1. **Critical issues first** — bugs, security vulnerabilities, N+1 queries, race conditions, trust boundary violations, missing indexes, unhandled error paths, and test gaps.
2. **Informational** — code quality, naming, structure, and maintainability concerns.

Surface all critical findings and require resolution before the branch is merged. Informational items may be addressed at the author's discretion.

**Do not approve a merge with open critical issues.**
