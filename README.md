# Cursor Rules

A shared collection of [Cursor Rules](https://docs.cursor.com/context/rules) that guide AI-assisted coding across projects and teams. Clone this repo once and use it as the foundation for every project you work on.

## Structure

```
.cursor/rules/
├── general/        # Universal engineering best practices (language-agnostic)
├── tech/           # Language, framework, and tooling conventions
├── design-styles/  # Reusable visual style library (inactive by default)
└── project/        # Domain-specific rules for the current project
```

| Folder | What goes here | Globs | Change frequency | Reusable? |
|---|---|---|---|---|
| `general/` | Language-agnostic engineering principles | `["**"]` — always active | Rarely | Yes — copy to any project as-is |
| `tech/` | Per-language / framework / tool conventions | Scoped to file types (e.g., `*.ts`, `*.py`) | Occasionally | Yes — for projects on the same stack |
| `design-styles/` | Style library (`bauhaus`, `cyberpunk`, etc.) | `[]` (library mode, inactive) | Rarely | Yes — shared across UI projects |
| `project/` | Domain rules + active style selection | Scoped to project paths/UI paths | Often | No — unique per project |

## How It Works

Each `.md` file has a YAML frontmatter `globs` field that tells Cursor **when** to activate the rule:

```yaml
---
globs: ["apps/backend/src/api/**/*.py"]
---
```

When you open or edit a file matching the glob pattern, Cursor automatically injects the rule into the AI's context. The subfolder structure (`general/`, `tech/`, `design-styles/`, `project/`) is purely for human organization — Cursor scans all subdirectories recursively.

## Using This in Your Projects

### Option A: Copy into an existing project

Best when you want rules versioned alongside your project code.

```bash
# From your project root
git clone https://github.com/<org>/cursor-rules.git /tmp/cursor-rules
cp -r /tmp/cursor-rules/.cursor/rules/ .cursor/rules/
rm -rf /tmp/cursor-rules
```

Then customize `tech/` and `project/` (see [Adapting for Your Project](#adapting-for-your-project) below).

### Option B: Symlink from a shared local clone

Best when you want one copy of `general/` rules on your machine, shared across all projects. Changes to the shared clone propagate everywhere instantly.

```bash
# One-time: clone the shared rules repo somewhere central
git clone https://github.com/<org>/cursor-rules.git ~/cursor-rules

# In each project: symlink the general rules
mkdir -p .cursor/rules
ln -s ~/cursor-rules/.cursor/rules/general .cursor/rules/general
```

Then create `tech/` and `project/` folders locally in each project — these stay project-specific.

```
your-project/
└── .cursor/rules/
    ├── general/  → ~/cursor-rules/.cursor/rules/general  (symlink, shared)
    ├── tech/           # your stack-specific rules (local)
    └── project/        # your domain-specific rules (local)
```

### Option C: Git submodule

Best for teams who want a single source of truth for shared rules, version-pinned per project.

```bash
# Add as submodule
git submodule add https://github.com/<org>/cursor-rules.git .cursor/shared-rules

# Symlink general into the rules directory Cursor reads
mkdir -p .cursor/rules
ln -s ../shared-rules/.cursor/rules/general .cursor/rules/general
```

To pull updates:

```bash
git submodule update --remote .cursor/shared-rules
```

### Option D: Simple copy-paste (smallest teams)

Just copy the `general/` folder manually into your project's `.cursor/rules/` directory. Quick, no tooling required — but you'll need to copy again when shared rules are updated.

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

### `tech/` — Stack Conventions (examples included)

These are examples from a TypeScript/React/Postgres stack. Replace with rules for your stack.

| File | Covers |
|---|---|
| `api-routes.md` | RESTful design, HTTP methods, input validation, response format |
| `database.md` | Query safety, connection pooling, schema design, migrations |
| `docker-devops.md` | Dockerfile best practices, Docker Compose, shell scripts, observability |
| `react-frontend.md` | Component design, state management, type safety, accessibility |
| `typescript-backend.md` | Strict typing, null handling, function design, async/await, naming |

### `project/` — Domain-Specific (examples included)

These are examples from a WooCommerce e-commerce project. Replace with rules for your domain.

| File | Covers |
|---|---|
| `price-logic.md` | Price parsing, currency conversion, markup calculation |
| `scraping.md` | Anti-detection, Playwright best practices, data extraction |
| `woocommerce-api.md` | Product publishing pipeline, variation sync, image handling |
| `woocommerce-theme.md` | WordPress PHP standards, WooCommerce hooks, theme assets |
| `active-design-style.md` | Single source of truth for selected style in this project |

### `design-styles/` — Visual Style Library

All files in this folder use `globs: []` so they stay inactive until selected via `project/active-design-style.md`.

| File | Covers |
|---|---|
| `brutalism.md` | Raw, harsh, asymmetrical, intentionally rough interfaces |
| `neobrutalism.md` | Bold playful UI with thick outlines and hard shadows |
| `bauhaus.md` | Functional geometric composition and grid-driven hierarchy |
| `neumorphism.md` | Soft depth, tactile controls, subtle highlights/shadows |
| `retro-futurism.md` | Nostalgic future, vintage + sci-fi visual treatment |
| `cyberpunk.md` | Dark neon, high-tech layered interfaces |
| `glassmorphism.md` | Frosted translucent panels with depth and blur |
| `flat-design.md` | Minimal 2D UI with clean hierarchy and solid colors |

## Adapting for Your Project

### Step-by-step

1. **Copy** `.cursor/rules/` into your repo (use any method from [above](#using-this-in-your-projects)).
2. **Keep `general/` as-is** — these are language-agnostic and work for any stack.
3. **Replace `tech/`** — delete the example files and add rules for your stack:

   | Your stack | Example files you'd create |
   |---|---|
   | Python + Django | `python.md`, `django.md` |
   | Go + gRPC | `go.md`, `grpc.md` |
   | Rust + Actix | `rust.md`, `actix.md` |
   | Java + Spring Boot | `java.md`, `spring-boot.md` |
   | C# + .NET | `csharp.md`, `dotnet.md` |
   | C/C++ | `c-cpp.md` |
   | Angular + Node | `angular.md`, `node.md` |
   | React + Next.js | Keep existing `react-frontend.md`, `typescript-backend.md` |

4. **Replace `project/`** — delete the example files and add rules specific to your domain (payment logic, auth quirks, API integration gotchas, etc.).
5. **Pick one visual style** — set `.cursor/rules/project/active-design-style.md` with your selected style and matching style file.

### Using design styles in a project

Use this pattern to avoid conflicting style guidance:

1. Keep all style files in `.cursor/rules/design-styles/` with `globs: []` (library mode).
2. Keep a single active selector in `.cursor/rules/project/active-design-style.md`.
3. In `active-design-style.md`, set:
   - `STYLE_NAME` to one of:
     - `brutalism`
     - `neobrutalism`
     - `bauhaus`
     - `neumorphism`
     - `retro-futurism`
     - `cyberpunk`
     - `glassmorphism`
     - `flat-design`
   - `STYLE_FILE` to the matching file in `.cursor/rules/design-styles/`
4. Scope `active-design-style.md` globs to your UI files so style guidance appears during UI work.

Example:

```markdown
---
globs: ["**/*.tsx", "**/*.css", "**/components/**/*", "**/ui/**/*"]
---

# Active Design Style

- **STYLE_NAME:** `bauhaus`
- **STYLE_FILE:** `.cursor/rules/design-styles/bauhaus.md`
```

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
| `["**/Tests/**/*.cs"]` | Test files (.NET) |
| `["Dockerfile*", "docker-compose*"]` | Docker config files |
| `["**/*.proto"]` | Protocol Buffer files |

### Tips

- **Be specific with globs.** Broad globs mean the rule is injected more often, consuming context window. Scope tightly to where the rule actually matters.
- **Keep rules concise.** Each rule competes for context space. Prioritize the non-obvious — things the AI tends to get wrong or that encode hard-won project knowledge.
- **Use `project/` for bug-prone areas.** If a pattern has caused recurring bugs, document it as a rule so the AI doesn't repeat the mistake.
- **Don't duplicate language docs.** Rules like "use `async/await`" are less valuable than "always set a 90s timeout on external API calls because of upstream gateway timeouts."
- **Review periodically.** Remove rules that no longer apply. Stale rules waste context and can mislead the AI.
- **Keep `general/` in sync.** If your team improves a general rule, contribute it back to this shared repo so everyone benefits.
