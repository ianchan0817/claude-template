# CLAUDE.md

## Agents

Route work to the right agent. Don't handle specialist work in the main session.

| Agent | Activate when |
|-------|--------------|
| `manager` | New initiative, cross-concern coordination, daily report |
| `engineer` | Build, test, deploy, architecture, DB, CI/CD |
| `reviewer` | Code review, security audit, E2E sign-off, retros |

---

## Slash Commands

| Command | What it does |
|---------|-------------|
| `/project:spec` | Define what to build — use cases, RICE, acceptance criteria |
| `/project:plan` | Architecture design + task breakdown |
| `/project:design` | UI/component design specs, mobile review |
| `/project:build` | Incremental implementation with TDD |
| `/project:test` | Test strategy and coverage enforcement |
| `/project:review` | Pre-merge code review |
| `/project:security` | Security audit — threat model, OWASP, CVEs |
| `/project:e2e` | E2E quality assurance and release sign-off |
| `/project:ship` | Land a ready branch |
| `/project:retro` | Sprint retrospective + agent improvement pass |
| `/project:daily-report` | Manager daily executive summary |
| `/project:investigate` | Root cause debugging |

---

## Rules

Constraints applied across every agent, every session. Fill in `tech-stack.md` before your first session.

| Rule | What it enforces |
|------|-----------------|
| `rules/tech-stack.md` | MUST use these languages, frameworks, and tools |
| `rules/code-style.md` | Naming, formatting, TypeScript strictness |
| `rules/testing.md` | 100% coverage, TDD, test co-location |
| `rules/api-conventions.md` | REST naming, response envelope, pagination, versioning |
| `rules/security.md` | Input validation, secrets, PII, auth/authz gates |
| `rules/ux-guidelines.md` | Spacing, typography, mobile rules, interaction patterns |

---

## Workflow

Every initiative follows this sequence — no skipping steps:

```
Idea → /project:spec (define what + why) →
/project:design (UI specs, if applicable) →
/project:plan (architecture + tasks) →
/project:build (engineer implements with TDD) →
/project:review (reviewer: code + security) →
/project:e2e (reviewer: E2E sign-off) →
/project:ship (land branch) →
/project:retro (log + improve)
```

---

## Non-Negotiables

- 100% unit test coverage on all new and modified code
- Code review before every merge
- E2E sign-off before every release
- Security review for any change touching auth, data, or external APIs
- Every error logged before it's fixed
- Recurring errors (2+) trigger an agent file update

---

## Project Memory

After every major task, update `.claude/memory/progress.md` with:
- What changed (1 sentence)
- Key decisions made
- What's next

AI SHOULD derive detailed status from `git log` — memory captures what git can't.

ADRs live in `.claude/docs/adr/ADR-NNN-title.md`.

---

## Build Commands

```bash
# Fill in your project's actual commands
# bun install
# bun dev
# bun test
# bun run build
```
