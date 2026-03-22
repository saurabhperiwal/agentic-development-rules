---
globs: ["**"]
---

# Security Standards

## Injection Prevention
- Parameterized queries ALWAYS — no string concatenation for SQL, LDAP, OS commands
- Use your language/framework's built-in parameterization (prepared statements, ORMs)
- NEVER interpolate user input into query strings, shell commands, or templates

## Authentication & Authorization
- Validate tokens/sessions on every request (signature, expiry, audience)
- Check permissions server-side on EVERY endpoint — never trust the client
- Use non-guessable resource IDs (UUIDs over sequential integers)
- Deny by default — whitelist allowed operations

## Input Validation
- Validate ALL user input at the API boundary using schema validation
- Sanitize URLs before making external requests (SSRF prevention)
- Limit request body size
- Rate limit all public-facing API endpoints

## Secrets Management
- NEVER hardcode secrets, API keys, or passwords in source code
- Use environment variables or a secret manager
- Encrypt sensitive data at rest
- Rotate credentials regularly

## Error Handling
- NEVER expose stack traces in production responses
- Log errors with context server-side, return generic messages to clients
- Don't leak internal paths, database names, or infrastructure details

## Session & Cookies
- HttpOnly, Secure, SameSite attributes on all cookies
- CSRF protection on state-changing operations
- Session timeout and renewal

## Dependencies
- Keep dependencies updated (check for known vulnerabilities / CVEs)
- Remove unused packages
- Audit before adding new dependencies
