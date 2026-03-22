# claude-template

A production-ready `.claude/` folder template that turns Claude Code into a coordinated team of specialists — each with a defined role, clear ownership, and the right tools.

---

## What this is

Most people use Claude Code as a single generic assistant. This template gives it an org chart.

Eleven specialist agents. Six slash commands. Always-on rules. Shared context. A process that scales from solo to team.

Every agent knows its job, who it escalates to, and what it never ships without. The CTO orchestrates the whole thing and reports to you daily.

---

## The team

| Agent | Role |
|-------|------|
| `cto` | Orchestrates the full department. Reviews product and engineering weekly. Runs the daily executive summary. Thinks in budget, capacity, and 30/60/90-day risk. |
| `product-manager` | Defines what to build and why. First-principles thinking. RICE prioritization. Use cases, feature specs, success metrics. Nothing gets built without a spec. |
| `ux-designer` | Mobile-first, human-centered design. Studies how great products work (Linear, Stripe, Airbnb, Duolingo). Component specs with every state. Handoff before implementation. |
| `architect` | Designs for SaaS, multi-tenant, global scale, millions of users. Covers microservices, DB schema by use case, Elasticsearch n-gram indexing, sync vs async, ETL pipelines. Writes ADRs. |
| `engineering-manager` | Owns the implementation layer. Breaks down tasks. Enforces 100% unit test coverage. Blocks any merge without tests and code review. |
| `backend-engineer` | Domain-driven, TDD-first. Big O analysis. Query performance, connection pooling, cache strategy. Integration documentation. Never ships untested code. |
| `frontend-engineer` | Modern frameworks, CSS management, bundle performance. XSS, CSP, CSRF. 100% coverage with Testing Library. Mobile-first always. |
| `qa-manager` | Owns E2E testing end-to-end. Playwright/Cypress. Diff-aware on feature branches. Nothing ships without E2E sign-off. Every production bug gets a test before the fix closes. |
| `devops-manager` | CI/CD, infrastructure-as-code, database ops, connection pool monitoring, SLOs, error budgets, incident response, post-mortems. |
| `security-manager` | STRIDE threat modeling, OWASP review, CVE audits, dependency scanning. Reviews anything touching auth, data, or external APIs. |
| `scrum-master` | Records every error before it's fixed. Runs retrospectives. Tracks action items. Rewrites agent files when patterns repeat — the agents evolve. |

---

## How it works

Every initiative follows this sequence:

```
Idea
 → CTO (product direction review)
 → product-manager (use cases + spec)
 → ux-designer (component specs)
 → architect (ADR + system design)
 → engineering-manager (task breakdown)
 → engineers (build + 100% tests)
 → code review
 → qa-manager (E2E sign-off)
 → ship
 → scrum-master (retro + error log)
```

No skipping steps. The CTO enforces the sequence.

---

## Slash commands

| Command | What it does |
|---------|-------------|
| `/project:plan` | Product direction review → engineering design → delegate to team |
| `/project:review` | Pre-landing code review — two-pass: critical issues then informational |
| `/project:qa` | E2E pass — diff-aware on feature branches, full suite on staging |
| `/project:ship` | Land a reviewed, QA-signed branch |
| `/project:retro` | Sprint retrospective + agent improvement pass |
| `/project:daily-report` | CTO daily executive summary |

---

## Auto-triggering skills

| Skill | Triggers when |
|-------|--------------|
| `triage` | Complex or ambiguous request — routes to the right agent silently |
| `debug` | Error, stack trace, or failing test shared |
| `explain` | "How does X work", "explain this", "what does this do" |

---

## Always-on rules

Applied across every agent, every session:

- **code-style** — naming, formatting, TypeScript strictness, import order
- **testing** — 100% coverage (statements, branches, functions, lines), TDD, no I/O in unit tests
- **api-conventions** — REST naming, response envelope, status codes, pagination, versioning
- **security** — input validation, secrets management, PII handling, auth/authz gates
- **ux-guidelines** — spacing scale, typography, mobile rules, interaction patterns

---

## Non-negotiables

- 100% unit test coverage on all new and modified code — CI blocks merge if not met
- Code review before every merge
- E2E sign-off before every release
- Security review for anything touching auth, data, or external APIs
- Every error logged to `.claude/retrospectives/error-log.md` before it's fixed
- Recurring errors (2+) trigger an agent file update — the scrum master owns this

---

## Project context

Before your first session, fill in:

| File | What to add |
|------|------------|
| `.claude/context/tech-stack.md` | Your languages, frameworks, databases, infrastructure |
| `.claude/context/team.md` | Who's on the team and what they own |
| `.claude/context/sprint.md` | Current sprint goals, in-progress work, blockers |
| `CLAUDE.md` | Build commands for your project |

The agents read these files to give project-specific answers instead of generic ones.

---

## What gets tracked

```
.claude/retrospectives/
  error-log.md          — every error, logged before it's fixed (ERR-NNN format)
  action-items.md       — open follow-ups, chased until closed
  agent-improvements.md — every time an agent file was updated from a pattern

.claude/decisions/      — Architecture Decision Records (ADR-NNN format)
.claude/product/        — feature specs, use cases, product decisions log
.claude/reports/        — daily CTO executive summaries
```

---

## Install

Copy the `.claude/` folder and `CLAUDE.md` into your project root:

```bash
git clone https://github.com/ianchan0817/claude-template.git
cp -r claude-template/.claude your-project/
cp claude-template/CLAUDE.md your-project/
```

Then fill in the three context files and your build commands. You're ready.

---

## Settings

`.claude/settings.json` controls what Claude can and cannot do in your project.

Denied by default: `rm -rf *`, force push, `git reset --hard`, `DROP`/`truncate` on databases, reading `.env` files, decrypting secrets.

Adjust the allow list to match your actual toolchain (bun, pnpm, cargo, go, docker, etc. are already included).
