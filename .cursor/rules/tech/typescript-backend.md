---
globs: ["apps/backend/**/*.ts", "packages/**/*.ts"]
---

# TypeScript Backend Standards

## Strict Typing (Non-Negotiable)
- NEVER use `any` — define interfaces for every object shape
- Enable and respect `strictNullChecks` — explicit null handling everywhere
- Prefer interfaces over type aliases for object shapes
- Use discriminated unions for state management
- Use `as const` for literal objects

## Null/Undefined Handling (CRITICAL)
- NEVER use truthy checks (`if (value)`) for numbers or strings that can be `0` or `""`
- ALWAYS use explicit null checks: `value != null && value > 0`
- For optional numeric fields: parse, then check `!isNaN()` AND `> 0`
- When clearing optional fields, send explicit empty/null — never omit the field

## Function Design
- Maximum 30 lines per function — split longer functions
- Maximum 3-4 parameters — use an options object for more
- Early returns for guard clauses
- Pure functions where possible (no side effects)
- Single level of abstraction per function
- Avoid flag parameters — split into separate functions

## Error Handling
- Custom error classes extending a base `AppError`
- Fail fast with clear, specific error messages
- NEVER swallow exceptions silently — always log and re-throw or handle
- NEVER expose raw error messages/stack traces to API consumers
- Use try/catch at service boundaries, not deep inside logic

## Naming
- Files: `kebab-case.ts` (e.g., `product-publisher.ts`)
- Classes/Interfaces: `PascalCase` (e.g., `ProductPublisher`)
- Functions/Variables: `camelCase` (e.g., `calculateFinalPrice`)
- Constants: `SCREAMING_SNAKE` (e.g., `MAX_RETRY_ATTEMPTS`)
- Database columns: `snake_case` (e.g., `base_price`)

## Async/Await
- Always use async/await over callbacks or raw promises
- Always handle promise rejections
- Set timeouts on all external calls (HTTP, DB)
- Use `AbortController` for cancellable operations

## Imports
- Group: node builtins → external packages → internal modules
- Prefer named exports over default exports
- Import types separately with `import type { ... }`
