---
description: Testing standards — always active. 100% unit coverage required. Engineers own unit + integration. QA owns E2E.
---

# Testing Standards

## Coverage — Non-negotiable

| Metric | Required |
|--------|---------|
| Statement | 100% |
| Branch | 100% |
| Function | 100% |
| Line | 100% |

CI blocks merge if coverage drops below 100% on new or modified files. No exceptions without written justification approved by the engineering manager.

## Ownership

| Layer | Owner | Tool |
|-------|-------|------|
| Unit | Engineer | Jest / Vitest / pytest / go test |
| Integration | Engineer | Against real implementations, not mocks |
| E2E | QA Manager | Headless browser / E2E framework |

## Unit Test Rules

- Written before or alongside code (TDD) — never after
- Co-located with source: `foo.test.ts` next to `foo.ts`
- Test names describe behavior: `should return zero when input is empty`
- One logical assertion per test
- No I/O — mock or stub all external dependencies
- Each test sets up its own state — no shared mutable state between tests
- Arrange / Act / Assert structure

## Integration Test Rules

- Test against real implementations (real DB, real cache)
- No mocks for the system under test
- Each test seeds its own data and cleans up after
- Run in CI against a test environment, not production

## What Must Be Tested

- Every public function and method
- Every branch (if/else, switch, ternary, early return)
- Every error path and thrown exception
- Every boundary: zero, null, empty, max, negative
- Every state transition in stateful logic
- Every data transformation and computation

## What Not to Test

- Framework internals
- Third-party library behavior
- Implementation details (private functions, internal state)
- Trivial getters/setters with no logic

## E2E Rules (QA Manager)

- Every user journey tested end-to-end: UI → API → DB → UI
- Every production bug that escapes gets an E2E test before the fix is closed
- No `sleep()` — use `waitFor` and retry assertions
- Tests must pass 3 consecutive times before considered stable
- Flaky tests are quarantined and treated as bugs
