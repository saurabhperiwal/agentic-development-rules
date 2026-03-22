# Cursor Rules

A shared collection of [Cursor Rules](https://docs.cursor.com/context/rules) that guide AI-assisted coding across projects. Copy this into any repo's `.cursor/rules/` directory and customize for your team.

## Structure

```
.cursor/rules/
├── general/        # Universal engineering best practices
├── tech/           # Language, framework, and tooling conventions
└── project/        # Domain-specific rules for the current project
```

| Folder | What goes here | Globs | Change frequency | Reusable? |
|---|---|---|---|---|
| `general/` | Language-agnostic engineering principles | `["**"]` — always active | Rarely | Yes — copy to any project as-is |
| `tech/` | Per-language / framework / tool conventions | Scoped to file types (e.g., `*.ts`, `*.py`) | Occasionally | Yes — for projects on the same stack |
| `project/` | Business logic, third-party integration quirks, domain rules | Scoped to project paths | Often | No — unique per project |

## How It Works

Each `.md` file has a YAML frontmatter `globs` field that tells Cursor **when** to activate the rule:

```yaml
---
globs: ["apps/backend/src/api/**/*.ts"]
---
```

When you open or edit a file matching the glob pattern, Cursor automatically injects the rule into the AI's context. The subfolder structure (`general/`, `tech/`, `project/`) is purely for human organization — Cursor scans all subdirectories recursively.

## Current Rules

### `general/` — Language-Agnostic Best Practices

All files use `globs: ["**"]` — they apply to every file regardless of language or framework.

| File | Covers |
|---|---|
| `architecture.md` | SOLID principles, clean architecture layers, separation of concerns, design patterns |
| `git-workflow.md` | Conventional commits, branching strategy, pre-commit checklist |
| `performance.md` | DB performance, caching strategies, async processing, frontend & API perf |
| `security.md` | Injection prevention, auth, input validation, secrets management |
| `testing.md` | Testing pyramid, Arrange-Act-Assert pattern, naming, edge cases |

### `tech/` — Stack Conventions

| File | Covers |
|---|---|
| `api-routes.md` | RESTful design, HTTP methods, input validation, response format |
| `database.md` | Query safety, connection pooling, schema design, migrations |
| `docker-devops.md` | Dockerfile best practices, Docker Compose, shell scripts, observability |
| `react-frontend.md` | Component design, state management, type safety, accessibility |
| `typescript-backend.md` | Strict typing, null handling, function design, async/await, naming |

### `project/` — Domain-Specific

| File | Covers |
|---|---|
| `price-logic.md` | Price parsing, currency conversion, markup calculation, WooCommerce price sync |
| `scraping.md` | Anti-detection, Playwright best practices, data extraction, error handling |
| `woocommerce-api.md` | Product publishing pipeline, variation sync, image handling, stale references |
| `woocommerce-theme.md` | WordPress PHP standards, WooCommerce hooks, theme assets, SEO |

## Adapting for Your Project

### Quick start

1. Copy this `.cursor/rules/` folder into your repo.
2. Keep `general/` as-is — these are language-agnostic and work for any stack (Python, .NET, Go, Rust, Java, C/C++, JS/TS, etc.).
3. In `tech/`, keep what matches your stack, delete the rest, and add new files for your languages/frameworks.
4. Delete everything in `project/` and write rules for your own domain.

### Writing a new rule

Create a `.md` file in the appropriate folder with this template:

```markdown
---
globs: ["src/payments/**/*.py"]
---

# Payment Processing Rules

## Section Name
- Rule one
- Rule two
```

### Glob patterns

| Pattern | Matches |
|---|---|
| `["**"]` | All files (use for `general/` rules) |
| `["**/*.ts", "**/*.tsx"]` | All TypeScript/React files |
| `["**/*.py"]` | All Python files |
| `["**/*.go"]` | All Go files |
| `["**/*.rs"]` | All Rust files |
| `["**/*.java"]` | All Java files |
| `["**/*.cs"]` | All C# / .NET files |
| `["**/*.c", "**/*.cpp", "**/*.h"]` | All C/C++ files |
| `["**/*.test.*", "**/*.spec.*"]` | Test files (JS/TS ecosystem) |
| `["**/test_*.py", "**/*_test.go"]` | Test files (Python / Go) |
| `["Dockerfile*", "docker-compose*"]` | Docker config files |

### Tips

- **Be specific with globs.** Broad globs mean the rule is injected more often, consuming context window. Scope tightly to where the rule actually matters.
- **Keep rules concise.** Each rule competes for context space. Prioritize the non-obvious — things the AI tends to get wrong or that encode hard-won project knowledge.
- **Use the `project/` folder for bug-prone areas.** If a pattern has caused recurring bugs (e.g., price handling edge cases), document it as a rule so the AI doesn't repeat the mistake.
- **Don't duplicate language docs.** Rules like "use `async/await`" are less valuable than "always set a 90s timeout on external API calls because of upstream gateway timeouts."
- **Review periodically.** Remove rules that no longer apply. Stale rules waste context and can mislead the AI.
