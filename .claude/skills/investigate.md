---
description: Activated via /project:investigate or automatically on errors, stack traces, failing tests, "it's broken", "getting an error". Structured debugging — reproduce, isolate, diagnose, fix. No fixes without root cause.
---

# Investigate

Systematic debugging. No fixes without root cause.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "Let me just try something" | Random changes create new bugs |
| "It works on my machine" | Environment differences are bugs |
| "Let me restart and see" | Restart masks the root cause |

## Process

### Step 1 — Reproduce
Confirm the exact failure:
- Error message and stack trace
- Steps to reproduce
- Environment (local, staging, production)
- Since when? (git bisect if needed)

### Step 2 — Isolate
Narrow down where in the code the failure originates:
- Read the stack trace bottom-up
- Check recent changes: `git log --oneline -20`
- Binary search with `git bisect` if unclear

### Step 3 — Hypothesize
State the most likely root causes **before** diving into code:
1. [Most likely] — because...
2. [Second] — because...
3. [Third] — because...

### Step 4 — Diagnose
Read the relevant code. Check each hypothesis:
- Add targeted logging or breakpoints
- Check assumptions against actual state
- Verify data in DB, cache, or external service

### Step 5 — Fix
Make the **minimal** change that resolves the root cause:
- Don't patch symptoms
- Don't refactor while fixing
- Write a test that would have caught this

### Step 6 — Verify
- [ ] Fix resolves the original failure
- [ ] No regression in existing tests
- [ ] New test covers the bug

### Step 7 — Log
Record in `.claude/memory/progress.md` under Known Issues:
- What happened, root cause, resolution
- Remove entry once resolved

## Rules
- No fix without understanding the root cause
- No fix without a test
- Log the error before fixing it
