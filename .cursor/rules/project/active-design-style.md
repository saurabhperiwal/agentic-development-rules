---
globs: [
  "**/*.html",
  "**/*.css",
  "**/*.scss",
  "**/*.sass",
  "**/*.less",
  "**/*.tsx",
  "**/*.jsx",
  "**/*.vue",
  "**/*.svelte",
  "**/*.astro",
  "**/components/**/*",
  "**/ui/**/*",
  "**/styles/**/*",
  "**/pages/**/*",
  "**/app/**/*"
]
---

# Active Design Style (Project Source of Truth)

This file defines the single design style to follow for this project.

## Selected Style
- **STYLE_NAME:** `origami`
- **STYLE_FILE:** `.cursor/rules/design-styles/origami.md`

## Rules of Use
- Apply the selected style to all new UI and UX decisions.
- Keep visual, spacing, and component choices consistent with `STYLE_FILE`.
- If a request conflicts with this style, ask before changing direction.
- Do not mix multiple design styles unless explicitly requested.
- When proposing alternatives, keep one option in the active style.

## How to Change Style
1. Change `STYLE_NAME`.
2. Update `STYLE_FILE` to the matching file in `.cursor/rules/design-styles/`.
3. Keep old style notes in commit history, not in this file.

## Allowed Values for STYLE_NAME
- `brutalism`
- `neobrutalism`
- `bauhaus`
- `neumorphism`
- `retro-futurism`
- `cyberpunk`
- `glassmorphism`
- `flat-design`
- `origami`
