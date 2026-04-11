---
description: Activated via /project:build. Incremental implementation with TDD. Thin vertical slices — implement, test, verify, commit, repeat. Borrowed from addyosmani/agent-skills.
---

# Build

Build in thin vertical slices. Each slice is testable and commitable on its own.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "I'll test everything at the end" | Compounding bugs are harder to isolate |
| "Let me build the whole feature first" | Big diffs are unreviable |
| "Tests slow me down" | Debugging without tests is slower |
| "I'll refactor later" | Technical debt compounds with interest |

## Core Operating Behaviors

1. **Surface assumptions explicitly** before acting
2. **Stop when confused** — name the confusion, don't push through
3. **Push back with concrete reasoning** — not "I think" but "because X"
4. **Enforce simplicity** over cleverness
5. **Maintain scope discipline** — no drive-by refactoring
6. **Verify with evidence** — passing tests, clean builds, runtime output

## Process

### Step 1 — Slice the work
Break the feature into thin vertical slices. Each slice:
- Delivers one testable behavior
- Touches at most ~5 files
- Can be committed independently
- Has its own tests

Order: risk-first. Build the hardest or most uncertain slice first.

### Step 2 — For each slice: Red → Green → Refactor

**Red** — Write the failing test that specifies the behavior
```
it('should return zero when input is empty', () => {
  expect(calculate([])).toBe(0)
})
```

**Green** — Write the minimum code to make it pass

**Refactor** — Clean up without breaking tests

### Step 3 — Verify before committing
- [ ] All tests pass
- [ ] No linting or type errors
- [ ] Coverage remains 100% on modified files
- [ ] The slice works in isolation

### Step 4 — Commit atomically
One slice = one commit. Clear message describing the behavior added.

### Step 5 — Repeat
Move to the next slice. After all slices:
- [ ] Full test suite passes
- [ ] 100% coverage on all new/modified code
- [ ] Self-review against engineer checklist
- [ ] Request review from `reviewer`

## Verification Gate
Each commit must have:
- Passing tests covering the new behavior
- No regression in existing tests
- Clean build with no errors
