---
description: Activated via /project:security. Security audit — threat modeling, OWASP Top 10, dependency CVE check. Run on any change touching auth, data, or external APIs.
---

# Security

Find problems before attackers do.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "We'll add security later" | Vulnerabilities in production don't wait |
| "It's just an internal API" | Internal APIs get exposed. Assume breach. |
| "No one will find this" | Attackers use automated scanners |

## Process

### Step 1 — Threat Model (STRIDE)

```markdown
## Threat Model: [Feature]

### Assets — What are we protecting?
### Trust Boundaries — Where does data cross from trusted to untrusted?
### Threats
| Category | Threat | Likelihood | Impact | Mitigation |
|----------|--------|-----------|--------|-----------|
| Spoofing | | H/M/L | H/M/L | |
| Tampering | | | | |
| Repudiation | | | | |
| Info Disclosure | | | | |
| Denial of Service | | | | |
| Elevation of Privilege | | | | |
```

### Step 2 — Code Review (OWASP Top 10)

**Authentication & Authorization**
- [ ] Auth enforced on all protected routes
- [ ] Authorization at the data layer
- [ ] Session tokens with proper expiry and rotation
- [ ] Password hashing: bcrypt or argon2

**Input Validation**
- [ ] All user input validated and sanitized
- [ ] SQL: parameterized queries only
- [ ] File uploads: MIME by content, size limited, filename sanitized
- [ ] Output encoded to prevent XSS

**Data Handling**
- [ ] PII minimized and documented
- [ ] Encrypted at rest and in transit
- [ ] No secrets in code, logs, or error messages
- [ ] No PII in URLs, logs, or analytics
- [ ] Data retention policy applied

**Client-Side**
- [ ] No `dangerouslySetInnerHTML` without `DOMPurify`
- [ ] No `eval`, `new Function`, dynamic execution
- [ ] User URLs validated for safe scheme
- [ ] CSP configured, no `unsafe-eval`
- [ ] No sensitive data in `localStorage`

**Dependencies**
- [ ] `npm audit` / `pip audit` — no critical/high CVEs
- [ ] Versions pinned and reviewed

### Step 3 — Severity Classification

| Severity | Action |
|----------|--------|
| Critical | Block release, notify manager immediately |
| High | Must fix before release |
| Medium | Fix next sprint |
| Low | Document and monitor |

**Never approve a release with open Critical or High findings.**

## Output
Document findings with severity, affected file/line, and recommended fix. Log to `.claude/memory/progress.md` under Known Issues.
