# CLAUDE.md

## Agent Team

Route work to the right agent. Don't handle specialist work in the main session.

| Agent | Activate when |
|-------|--------------|
| `cto` | New initiative, cross-team coordination, daily report |
| `product-manager` | Use cases, prioritization, feature specs |
| `ux-designer` | UI design, component specs, mobile review |
| `architect` | System design, ADRs, scalability, DB schema |
| `engineering-manager` | Task breakdown, code review, coverage enforcement |
| `backend-engineer` | API, domain logic, DB queries, cache, integrations |
| `frontend-engineer` | Components, state, CSS, bundle, security |
| `qa-manager` | E2E tests, release sign-off, bug triage |
| `devops-manager` | CI/CD, infra, DB ops, monitoring, SRE |
| `security-manager` | Auth, data privacy, threat modeling, CVEs |
| `scrum-master` | Error log, retros, action items, agent updates |

---

## Slash Commands

| Command | What it does |
|---------|-------------|
| `/project:plan` | Full planning sequence: product direction → engineering design → delegate |
| `/project:review` | Pre-landing code review |
| `/project:qa` | E2E pass for current branch or staging |
| `/project:ship` | Land a ready branch |
| `/project:retro` | Sprint retrospective + agent improvement pass |
| `/project:daily-report` | CTO daily executive summary |

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
Idea → product direction review → product-manager (spec) →
ux-designer (design) → architect (ADR) →
engineering-manager (tasks) → engineers (build + 100% tests) →
code review → qa-manager (E2E sign-off) → ship → scrum-master (retro + log)
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
