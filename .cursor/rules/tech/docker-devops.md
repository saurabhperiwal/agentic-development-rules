---
globs: ["Dockerfile*", "docker-compose*", "run.sh", ".dockerignore"]
---

# Docker & DevOps Standards

## Dockerfile
- Multi-stage builds: separate build and runtime stages
- Pin base image versions (e.g., `node:20-alpine`, not `node:latest`)
- Copy package files first, install deps, then copy source (layer caching)
- Run as non-root user in production
- Add health checks: `HEALTHCHECK CMD curl -f http://localhost:PORT/health`
- Minimize image size: use alpine, remove dev dependencies

## Docker Compose
- Define all services with health checks and depends_on conditions
- Use named volumes for persistent data (database)
- Environment variables via `.env` file (not hardcoded)
- Set memory limits and restart policies
- Expose only necessary ports

## Shell Scripts
- Set `#!/bin/bash` and `set -euo pipefail`
- Check prerequisites before executing
- Provide clear error messages with suggested fixes
- Use colored output for status/error messages
- Support `--help` flag

## Observability
- Structured JSON logging (Winston/Pino)
- Log levels: DEBUG, INFO, WARN, ERROR
- Include: timestamp, service name, request_id, duration_ms
- No sensitive data in logs (passwords, tokens, PII)
- Health check endpoints: `/health` (liveness), `/health/ready` (readiness with deps)
