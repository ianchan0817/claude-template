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

## Project Context

Agents read these files for project-specific context:

- `.claude/context/tech-stack.md` — languages, frameworks, tools
- `.claude/context/team.md` — who's on the team and what they own
- `.claude/context/sprint.md` — current sprint goals and status

**Fill these in before your first session.**

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
- Every error logged to `.claude/retrospectives/error-log.md` before it's fixed
- Recurring errors (2+) trigger an agent file update

---

## Build Commands

```bash
# Fill in your project's actual commands
# bun install
# bun dev
# bun test
# bun run build
```
