---
description: API design conventions — always active for backend engineers and architects
---

# API Conventions

## URL Design
- RESTful resource naming: plural nouns, kebab-case (`/user-profiles`, not `/userProfile`)
- No verbs in URLs — the HTTP method is the verb
- Nested resources max 2 levels deep: `/tenants/:id/users`, not deeper
- API versioned from day one: `/v1/`, `/v2/`
- Tenant ID never in the URL — in JWT claim or request header

## Request / Response Shape

Always return a consistent envelope:

```json
// Success
{ "data": { ... }, "meta": { "page": 1, "total": 100 } }

// Error
{ "error": { "code": "VALIDATION_FAILED", "message": "...", "fields": { ... } } }
```

Never mix — success responses never have `error`, error responses never have `data`.

## HTTP Status Codes

| Status | When |
|--------|------|
| 200 | Successful GET, PATCH, PUT |
| 201 | Successful POST that creates a resource |
| 204 | Successful DELETE (no body) |
| 400 | Malformed request (bad JSON, wrong types) |
| 401 | Not authenticated |
| 403 | Authenticated but not authorized |
| 404 | Resource not found |
| 409 | Conflict (duplicate, stale version) |
| 422 | Validation failure (well-formed but invalid data) |
| 429 | Rate limited |
| 500 | Unexpected server error |

Never use 200 for errors. Never use 400 for validation — that's 422.

## Pagination

Cursor-based for all list endpoints:

```json
{
  "data": [...],
  "meta": {
    "next_cursor": "eyJpZCI6MTAwfQ==",
    "has_more": true,
    "limit": 20
  }
}
```

Default limit: 20. Max limit: 100. Never return unbounded lists.

## Authentication
- JWT bearer token in `Authorization: Bearer <token>` header
- Token contains: `sub` (user ID), `tenant_id`, `roles`, `exp`
- Refresh tokens: HttpOnly, Secure, SameSite=Strict cookies
- Token expiry: access 15min, refresh 30 days

## Rate Limiting
- Per tenant, not per IP
- Headers returned: `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset`
- 429 response includes `Retry-After` header

## Idempotency
- All POST endpoints that create resources accept `Idempotency-Key` header
- Duplicate requests with same key return the original response (cached 24h)
- PUT and DELETE are naturally idempotent

## Errors
- Machine-readable `code` field (SCREAMING_SNAKE_CASE)
- Human-readable `message` field
- Field-level errors in `fields` object for validation failures
- Never expose stack traces, DB errors, or internal paths in API responses

## Versioning
- Breaking changes require a new version (`/v2/`)
- Non-breaking additions (new fields, new endpoints) are backward compatible
- Deprecate before removing: add `Deprecation` header, give 6 months notice
- Maintain N-1 version in production at all times
