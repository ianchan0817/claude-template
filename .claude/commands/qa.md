# QA

Run the E2E quality assurance pass for the current branch or environment.

## Context

Current branch:
```
$(git branch --show-current)
```

Files changed vs main:
```
$(git diff origin/main --stat 2>/dev/null | head -20)
```

## Instructions

**On a feature branch (default):**
Identify the routes and pages affected by the diff. Run the E2E suite against those areas using the project's configured headless browser framework (e.g. Playwright, Cypress).

**For staging sign-off:**
Run the full E2E suite against the staging environment with authenticated sessions as needed.

**For a specific flow:**
Use the headless browser framework directly — navigate, interact, screenshot, check console output.

After the QA pass, the `qa-manager` must:
- Document findings in the E2E test plan
- Log any bugs to `scrum-master` via `.claude/retrospectives/error-log.md`
- Sign off explicitly before the branch can be shipped
