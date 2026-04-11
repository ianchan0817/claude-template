# claude-template

A production-ready `.claude/` folder template that turns Claude Code into a coordinated engineering team — 3 agents, 12 workflow skills, and strict quality gates.

Inspired by [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) and [garrytan/gstack](https://github.com/garrytan/gstack).

---

## What this is

Most people use Claude Code as a single generic assistant. This template gives it structure.

Three specialist agents. Twelve workflow skills. Always-on rules. Shared context. A process that scales from solo to team.

Every skill encodes senior engineering discipline with anti-rationalization tables and verification gates. The manager orchestrates, the engineer builds, and the reviewer ensures nothing ships broken.

---

## The team

| Agent | Role |
|-------|------|
| `manager` | Orchestrates the department. Routes work to the right skill or agent. Runs daily executive summaries. Thinks in budget, capacity, and risk. Reports to you. |
| `engineer` | Full-stack implementation. Architecture, APIs, database, frontend, CI/CD, infrastructure. TDD with 100% coverage. Domain-driven design. Performance-measured. |
| `reviewer` | Code review, security audit, E2E sign-off, process improvement. Threat modeling (STRIDE). Error logging. Retrospectives. Evolves agent files when patterns repeat. |

---

## How it works

Every initiative follows this sequence:

```
Idea
 → /project:spec (define what + why)
 → /project:design (UI specs, if applicable)
 → /project:plan (architecture + task breakdown)
 → /project:build (engineer implements with TDD)
 → /project:review (code + security review)
 → /project:e2e (E2E sign-off)
 → /project:ship (land branch)
 → /project:retro (log + improve)
```

No skipping steps. The manager enforces the sequence.

---

## Slash commands

| Command | What it does |
|---------|-------------|
| `/project:spec` | Define what to build — use cases, RICE prioritization, acceptance criteria |
| `/project:plan` | Architecture design + task breakdown |
| `/project:design` | UI/component design specs, mobile review |
| `/project:build` | Incremental implementation with TDD |
| `/project:test` | Test strategy and coverage enforcement |
| `/project:review` | Pre-merge code review — critical issues first, then informational |
| `/project:security` | Security audit — threat model, OWASP Top 10, CVE check |
| `/project:e2e` | E2E quality assurance and release sign-off |
| `/project:ship` | Land a reviewed, signed-off branch |
| `/project:retro` | Sprint retrospective + agent improvement pass |
| `/project:daily-report` | Manager daily executive summary |
| `/project:investigate` | Root cause debugging — no fixes without diagnosis |

---

## Always-on rules

Applied across every agent, every session:

- **tech-stack** — languages, frameworks, databases, infrastructure (fill in before first session)
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
- Every error logged before it's fixed
- Recurring errors (2+) trigger an agent file update — the reviewer owns this

---

## Key patterns

Borrowed from the best in the space:

**From [agent-skills](https://github.com/addyosmani/agent-skills):**
- Anti-rationalization tables — every skill preemptively counters excuses for skipping steps
- Gated verification — require evidence (passing tests, clean builds), not "it seems right"
- Six core operating behaviors baked into the build skill

**From [gstack](https://github.com/garrytan/gstack):**
- "Boil the Lake" — AI makes completeness cheap, so always do the complete thing
- Atomic commits per fix in QA workflows
- Workflow-shaped skills over role-shaped agents

---

## Setup

Before your first session, fill in:

| File | What to add |
|------|------------|
| `.claude/rules/tech-stack.md` | Your languages, frameworks, databases, infrastructure |
| `CLAUDE.md` | Build commands for your project |

That's it. The AI derives status from `git log` and keeps decisions in `memory/progress.md`.

---

## Directory structure

```
your-project/
├── CLAUDE.md              — project identity + build commands
└── .claude/
    ├── agents/            — 3 specialist agents (manager, engineer, reviewer)
    ├── skills/            — 12 workflow skills (spec, plan, build, review, ship, etc.)
    ├── rules/             — 6 constraint files (tech-stack, code-style, testing, etc.)
    ├── memory/            — lean project memory (progress.md)
    ├── docs/adr/          — Architecture Decision Records
    └── settings.json      — tool permissions
```

No sprint trackers, no action item tables, no retrospective directories. The AI reads git history for status and updates a single memory file for decisions and context that git can't capture.

---

## Install

Copy the `.claude/` folder and `CLAUDE.md` into your project root:

```bash
git clone https://github.com/ianchan0817/claude-template.git
cp -r claude-template/.claude your-project/
cp claude-template/CLAUDE.md your-project/
```

Then fill in `tech-stack.md` and your build commands. You're ready.

---

## Settings

`.claude/settings.json` controls what Claude can and cannot do in your project.

Denied by default: `rm -rf *`, force push, `git reset --hard`, `DROP`/`truncate` on databases, reading `.env` files, decrypting secrets.

Adjust the allow list to match your actual toolchain (bun, pnpm, cargo, go, docker, etc. are already included).

---

## License

MIT
