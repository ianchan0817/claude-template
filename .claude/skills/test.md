---
description: Activated via /project:test. Test strategy, coverage enforcement, and test quality review. Ensures 100% coverage on all new and modified code.
---

# Test

Design the test strategy and enforce coverage.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "Tests slow down development" | Debugging without tests is 5x slower |
| "100% coverage is unrealistic" | AI makes completeness cheap — boil the lake |
| "I'll add tests later" | Later never comes. Tests written after code miss edge cases |
| "This code is too simple to test" | Simple code with bugs is still broken |

## Test Strategy

### Unit Tests (Engineer owns)
- Written before or alongside code (TDD)
- Co-located: `foo.test.ts` next to `foo.ts`
- Test names describe behavior: `should return zero when input is empty`
- One logical assertion per test
- No I/O — mock all external dependencies
- Arrange / Act / Assert structure

### Integration Tests (Engineer owns)
- Test against real implementations (real DB, real cache)
- No mocks for the system under test
- Each test seeds its own data and cleans up
- Run in CI against test environment

### E2E Tests (Reviewer owns via `/project:e2e`)
- Complete user journeys: UI → API → DB → UI
- Every production bug gets an E2E test
- No `sleep()` — use `waitFor`

## Coverage Requirements

| Metric | Required |
|--------|---------|
| Statement | 100% |
| Branch | 100% |
| Function | 100% |
| Line | 100% |

### What Must Be Tested
- Every public function and method
- Every branch (if/else, switch, ternary, early return)
- Every error path and thrown exception
- Every boundary (zero, null, empty, max, negative)
- Every state transition
- Every data transformation

### What Not to Test
- Framework internals
- Third-party library behavior
- Implementation details (private functions, internal state)
- Trivial getters/setters with no logic

## Process

### Step 1 — Audit current coverage
Run the test suite with coverage enabled. Identify gaps.

### Step 2 — Write missing tests
For each gap, write tests that describe expected behavior.

### Step 3 — Verify enforcement
Ensure CI config blocks merge below 100%:

```js
// vitest / jest
coverage: {
  thresholds: { statements: 100, branches: 100, functions: 100, lines: 100 }
}
```

## Verification Gate
- [ ] All tests passing
- [ ] 100% coverage on new/modified files
- [ ] No flaky tests
- [ ] CI enforcement configured
