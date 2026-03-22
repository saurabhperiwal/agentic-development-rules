---
globs: ["apps/backend/src/api/**/*.ts"]
---

# API Route Standards

## RESTful Design
- Use nouns not verbs: `/products` not `/getProducts`
- Plural form: `/products` not `/product`
- Hierarchical: `/products/{id}/variations`
- Max 2-3 levels of nesting

## HTTP Methods & Status Codes
- GET: retrieve (200), POST: create (201), PUT: full update (200), PATCH: partial (200), DELETE (204)
- 400: validation failed, 401: auth required, 403: forbidden, 404: not found, 409: conflict, 422: business rule violation
- 202 Accepted: for async operations (scraping, publishing)

## Input Validation (Non-Negotiable)
- Validate ALL inputs with Zod schemas
- Validate path params, query params, and body
- Reject early — don't let bad data reach the service layer
- Use `.nullable()` and `.optional()` correctly — they mean different things

## Route Handler Pattern
- Route handlers should be thin — extract logic into service functions
- Handler does: parse input → call service → format response
- NEVER put business logic or raw SQL in route handlers
- NEVER instantiate `new pg.Pool()` in route files — inject it

## Response Format
- Consistent shape: `{ success: true, data: ... }` or `{ success: false, error: ... }`
- Always include pagination metadata: `{ data, total, page, limit }`
- Filter sensitive fields before responding (no raw DB rows)

## Error Responses
- Return generic messages to client, log details server-side
- Include a `requestId` for debugging
- NEVER leak stack traces, SQL errors, or internal paths
