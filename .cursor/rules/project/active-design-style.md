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

This file defines the design source and style rules for this project.

## Design Source

- **SOURCE:** `figma` or `style-file`
- **FIGMA_FILE_KEY:** `<your-file-key>`
- **FIGMA_PAGES:** `*`
- **TOKEN_LOCATION:** `.env` in project root (`FIGMA_ACCESS_TOKEN`)

When `SOURCE` is `figma`, the agent must fetch and inspect the Figma file before building any UI. When `SOURCE` is `style-file`, the agent uses only the style file below.

## Setup (Figma mode)

Ensure a `.env` in the project root contains:

    FIGMA_ACCESS_TOKEN=figd_xxxxxxxxxxxx
    FIGMA_FILE_KEY=<your-file-key>

Do not commit this file. Add `.env` to `.gitignore`.

## Rules of Use

### When SOURCE is `figma`
- **Figma is the single source of truth** for layout, spacing, colors, typography, and component structure.
- Before building any UI screen, **fetch the corresponding Figma frame** using the Figma skill and inspect its structure, dimensions, colors, and text styles.
- The fallback style file (below) provides guidance only for decisions the wireframe does not cover (animation, charts, icon generation, motion preferences).
- If Figma and the fallback style file conflict, **Figma wins**.
- Do not invent layout, spacing, or color choices when the Figma frame provides them.

### When SOURCE is `style-file`
- Apply the selected style to all new UI and UX decisions.
- Keep visual, spacing, and component choices consistent with `STYLE_FILE`.
- If a request conflicts with this style, ask before changing direction.
- Do not mix multiple design styles unless explicitly requested.
- When proposing alternatives, keep one option in the active style.

## Figma Extraction Checklist

When implementing a screen or component from Figma, extract and follow:

1. **Layout** -- frame dimensions, grid columns, gutters, padding, alignment.
2. **Spacing** -- exact gaps between elements from bounding box data.
3. **Colors** -- fills on rectangles, text, backgrounds; map to CSS variables.
4. **Typography** -- font family, weight, size, line-height, letter-spacing from TEXT nodes.
5. **Component structure** -- identify repeated patterns and implement as reusable components.
6. **Hierarchy** -- mirror the Figma layer tree as DOM nesting unless semantics require otherwise.
7. **States** -- frames suffixed `hover`, `active`, `disabled`, `empty` define interaction states.
8. **Responsive** -- multiple frames at different widths define breakpoint references.

## Fallback / Primary Style

- **STYLE_NAME:** `origami`
- **STYLE_FILE:** `.cursor/rules/design-styles/origami.md`

In `figma` mode, use only for: animation patterns, chart theming, icon generation, and decisions where the Figma file is silent.
In `style-file` mode, this is the primary design system.

## How to Change

1. Set `SOURCE` to `figma` or `style-file` depending on the project.
2. Update `FIGMA_FILE_KEY` when the design file changes.
3. Change `STYLE_NAME` / `STYLE_FILE` to switch the style aesthetic.
4. Keep old values in commit history, not in this file.

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
