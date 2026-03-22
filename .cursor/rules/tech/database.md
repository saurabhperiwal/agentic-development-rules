---
globs: ["**/db/**/*.ts", "**/services/**/*.ts", "**/routes/**/*.ts"]
---

# Database Standards

## Query Safety
- Parameterized queries ONLY — never concatenate user input into SQL
- Use `EXPLAIN ANALYZE` to verify query plans before deploying complex queries
- Avoid `SELECT *` — specify columns explicitly
- Always use `LIMIT` for list queries (pagination)

## Connection Management
- Use connection pooling (`pg.Pool`) — never create pools inside functions
- Pool should be a singleton, injected into services
- Set connection timeouts and idle timeouts
- Close connections properly on shutdown

## Schema Design
- Use `UUID` primary keys (not serial integers)
- `snake_case` for all column names
- `TIMESTAMP DEFAULT NOW()` for `created_at`, `updated_at`
- Add `NOT NULL` constraints where appropriate
- JSONB for flexible structured data (with GIN indexes if queried)

## Data Integrity
- Foreign keys with proper `ON DELETE CASCADE` or `SET NULL`
- Unique constraints for business-key combinations
- Use transactions for multi-table writes that must be atomic
- Validate data at application level AND database level

## Performance
- Index columns used in WHERE, JOIN, ORDER BY
- Composite indexes for multi-column queries
- Partial indexes for filtered queries (e.g., `WHERE status = 'active'`)
- Monitor and remove unused indexes (they slow writes)
- Use JOINs over N+1 queries

## Migrations
- All schema changes through versioned migration files
- Migrations must be idempotent (`IF NOT EXISTS`, `ADD COLUMN IF NOT EXISTS`)
- Never modify existing migrations — create new ones
- Test migrations on a copy before running on production
