---
globs: ["**"]
---

# Performance Standards

## Database Performance
- Profile queries before deploying (e.g., `EXPLAIN ANALYZE` in SQL databases)
- Index columns used in WHERE, JOIN, ORDER BY
- NEVER do N+1 queries — use JOINs, batch queries, or eager loading
- Always paginate list queries (LIMIT/OFFSET, cursor-based, or keyset)
- Use connection pooling — never create connections per request

## Caching
- Cache expensive or frequently-read data with appropriate TTLs
- Cache-aside pattern: check cache → miss → fetch from source → store in cache
- Set explicit TTLs — no infinite caches
- Invalidate caches when underlying data changes

## Async Processing
- Offload heavy/long-running work to background jobs or message queues
- Implement retry with exponential backoff for transient failures
- Dead letter handling for permanently failed jobs
- Use progress events or polling for long-running operations visible to users

## Frontend Performance
- Lazy load images and non-critical assets
- Code split routes and heavy components
- Debounce search inputs and frequent state updates
- Minimize unnecessary re-renders
- Core Web Vitals: LCP < 2.5s, INP < 200ms, CLS < 0.1

## API Performance
- Keep payloads small — only return needed fields
- Enable compression on responses (Gzip/Brotli)
- Set appropriate Cache-Control headers for cacheable resources
- Timeout all external HTTP calls — never wait indefinitely
- Consider chunked/streaming responses for large payloads
