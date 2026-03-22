---
description: Security rules — always active across all engineers and agents. Non-negotiable baseline.
---

# Security Rules

These apply to every line of code, every agent, every review. Security is not a checklist at the end — it is a constraint from the start.

## Authentication & Authorization
- Authentication enforced on every protected route — no exceptions
- Authorization checked at the **data layer**, not just the route layer
- Never trust client-provided identity — always validate from the JWT or session
- Privilege escalation: verify the requesting user has rights to act on the target resource, not just the endpoint

## Input Validation
- Validate and sanitize all user input at the boundary — before it touches business logic
- Parameterized queries only — no string interpolation in SQL
- File uploads: validate MIME type by content (not extension), size limit enforced, filename sanitized
- Never `eval()`, `new Function()`, or `exec()` with user-controlled input

## Secrets
- No secrets in code, config files, logs, or error messages — ever
- Secrets managed via a secrets manager (not `.env` files committed to the repo)
- Rotate secrets on engineer offboarding and suspected compromise
- API keys scoped to minimum required permissions

## Data Protection
- PII identified, documented, and minimized — collect only what's needed
- PII encrypted at rest and in transit
- No PII in URLs, logs, or analytics events
- Data retention policy enforced — delete what you no longer need
- Tenant data isolation verified at the DB layer (RLS), not just the application

## Web Security (Frontend)
- No `dangerouslySetInnerHTML` without `DOMPurify` sanitization
- User-supplied URLs validated for safe scheme (`https?://` only)
- CSP header configured — no `unsafe-eval`
- `SameSite=Strict` on all auth cookies
- No sensitive data in `localStorage`

## Dependencies
- `npm audit` / `pip audit` / `cargo audit` run in CI
- No merge with known Critical or High CVEs in the dependency tree
- Dependency versions pinned and reviewed on update

## Code Review Security Gates
Any change touching the following **requires `security-manager` review** before merge:
- Authentication or session management
- Authorization logic or role/permission changes
- Data access patterns (new queries, new tables, new APIs)
- File upload or processing
- External API integrations
- Infrastructure or deployment configuration
- Cryptographic operations
