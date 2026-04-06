---
globs: []
---

# UI Style: Material Design 3 (M3)

**Canonical reference:** [Material Design 3](https://m3.material.io) — Google’s current Material system. This file names **official M3 concepts only** so implementations stay aligned with the spec. Do **not** invent parallel token names (for example, do not replace `primary` with `brand` unless the codebase already maps them in one place).

## How to use this file

1. **Vocabulary:** Use the **role names** and **component variant names** exactly as written below when choosing colors, type roles, and components.
2. **Implementation:** On the web, prefer **Material Web** ([material-web](https://github.com/material-components/material-web)), **MDC Web** (legacy but documented), or framework Material libraries (**Angular Material**, **Material UI** for React with M3 theming) — or map the same **roles** to CSS custom properties. Do not mix M2-only patterns (e.g. “raised button” as the default) with M3 unless the library has not migrated.
3. **Conflicts:** If product branding requires different hues, change **seed / palette values** only — keep **role structure** (primary, surface, error, etc.).
4. **Figma:** If the project also uses Figma, Figma may override **layout and composition**; this file still governs **M3 semantics** (roles, elevation behavior, motion philosophy).

---

## Design principles (M3)

- **Personal:** Support adaptation (e.g. dynamic color on supported platforms); on the web, static tokens are acceptable if documented.
- **Expressive:** Color and shape are emphasized; avoid flat gray-only admin UIs unless the product brief says otherwise.
- **Accessible:** Meet contrast for text and interactive elements; respect motion and focus requirements below.

---

## Color system (semantic roles)

M3 assigns meaning to **roles**, not raw hex values. Implement as CSS variables or theme objects using these names.

### Core accent roles

| Role | Typical use |
|------|-------------|
| `primary` | Key actions, prominent components, active states |
| `on-primary` | Text/icons on `primary` |
| `primary-container` | Less emphasis than primary; tinted surfaces |
| `on-primary-container` | Text/icons on `primary-container` |
| `secondary` | Accents, filters, secondary prominence |
| `on-secondary` | On `secondary` |
| `secondary-container` | Secondary tinted surfaces |
| `on-secondary-container` | On `secondary-container` |
| `tertiary` | Contrasting accents, balance to primary/secondary |
| `on-tertiary` | On `tertiary` |
| `tertiary-container` | Tertiary tinted surfaces |
| `on-tertiary-container` | On `tertiary-container` |

### Surface roles (M3 “surface container” model)

Use **surface containers** for hierarchy instead of stacking arbitrary box-shadows.

| Role | Typical use |
|------|-------------|
| `surface` | Default background for components and screens |
| `on-surface` | Default text/icons on `surface` |
| `surface-variant` | Subtle differentiation (cards, rows) |
| `on-surface-variant` | Secondary text, supporting icons |
| `surface-dim` | Dark theme: dimmest surface level |
| `surface-bright` | Dark theme: brighter surface |
| `surface-container-lowest` … `surface-container-highest` | Stepped elevation of contained areas (pick consecutive steps; do not skip levels without reason) |
| `on-surface` / `on-surface-variant` | As above, on those surfaces |

### Utility / system roles

| Role | Typical use |
|------|-------------|
| `background` | Screen behind scrolling content |
| `on-background` | Text on `background` |
| `outline` | Borders, dividers (stronger) |
| `outline-variant` | Hairlines, subtle separators |
| `shadow` | Shadow color where shadows are used |
| `scrim` | Modals, bottom sheets backdrop |
| `inverse-surface` / `inverse-on-surface` | Snackbars, tooltips on inverse layer |
| `inverse-primary` | Action color on inverse surfaces |

### Error roles

| Role | Typical use |
|------|-------------|
| `error` | Error text, icons, critical strokes |
| `on-error` | On `error` |
| `error-container` | Error banners, inline alert backgrounds |
| `on-error-container` | Text on `error-container` |

### Fixed vs. dynamic (terminology only)

- **Dynamic color:** Derived from user wallpaper or seed (Android / some web demos). Optional for web.
- **Static scheme:** Designer-chosen seed; still uses the **same role names**.

**Do not** hallucinate roles like `neutral-500` as a replacement for `on-surface-variant` unless the design tokens file explicitly documents that mapping.

---

## Typography (M3 type scale)

M3 uses **five categories** with **three sizes** each: **Display**, **Headline**, **Title**, **Body**, **Label**. Use these **labels** in design docs and code comments.

### Standard scale (reference sizes — adjust per breakpoint)

Use one **variable font** or family with **Roboto** as the reference M3 face; acceptable substitutes: **Noto Sans**, system UI stacks that match weights.

| Style name | Approx size / line height (sp) | Typical weight | Use |
|------------|----------------------------------|----------------|-----|
| `display-large` | 57 / 64 | Regular | Rare hero |
| `display-medium` | 45 / 52 | Regular | Hero |
| `display-small` | 36 / 44 | Regular | Hero / marketing |
| `headline-large` | 32 / 40 | Regular | Page title |
| `headline-medium` | 28 / 36 | Regular | Section |
| `headline-small` | 24 / 32 | Regular | Subsection |
| `title-large` | 22 / 28 | Regular | Card title |
| `title-medium` | 16 / 24 | Medium | List heading, dialog title |
| `title-small` | 14 / 20 | Medium | Compact headings |
| `body-large` | 16 / 24 | Regular | Primary reading |
| `body-medium` | 14 / 20 | Regular | Default UI body |
| `body-small` | 12 / 16 | Regular | Captions, helper text |
| `label-large` | 14 / 20 | Medium | Button text, prominent labels |
| `label-medium` | 12 / 16 | Medium | Compact buttons, tabs |
| `label-small` | 11 / 16 | Medium | Overlines, badges |

**Rules**

- Do **not** invent new scale step names (`caption`, `subtitle`) **unless** they map clearly to `body-small` / `title-small` in the implementation.
- **Letter-spacing:** M3 often uses slightly negative tracking on large display styles; keep subtle.
- **Responsive:** Reduce display/headline sizes on small viewports; keep hierarchy order intact.

---

## Shape (corner system)

M3 uses **shape family** per component category: **none**, **extra-small**, **small**, **medium**, **large**, **extra-large**, **full**.

| Token (conceptual) | Typical radius (dp) | Notes |
|--------------------|---------------------|--------|
| `corner-none` | 0 | Tables, full-bleed media |
| `corner-extra-small` | 4 | Chips, small inputs |
| `corner-small` | 8 | Buttons, text fields |
| `corner-medium` | 12 | Cards, dialogs |
| `corner-large` | 16 | Large cards, sheets |
| `corner-extra-large` | 28 | FAB-like containers, featured cards |
| `corner-full` | pill | Chips, search bars |

**Rules**

- Apply shape consistently per component **class** (all filled buttons share one corner scale unless spec says otherwise).
- Do not mix arbitrary radii (e.g. 7px, 13px) without a documented token.

---

## Elevation and shadows (M3)

M3 de-emphasizes heavy shadows; **surface tint** and **surface container** steps convey depth, especially in dark theme.

- Prefer **tonal surface step** (`surface-container-low` → `highest`) over multiple shadow layers.
- **Elevation levels** (0–5) still exist in spec-compatible libraries: use library tokens rather than inventing `box-shadow` stacks.
- **Overlays:** `scrim` for modal backdrops; opacity per spec/library defaults (typically in the 32–50% range for scrims — follow component guidelines).

---

## State layers (interaction)

Interactive **surfaces** (buttons, list tiles, chips) use **state overlays** on the **container color**, not random darken filters.

Standard **opacity** guidance on the container (M3):

| State | Overlay opacity on container |
|-------|------------------------------|
| Hover | 8% (`0.08`) |
| Focus | 12% (`0.12`) |
| Pressed | 12% (`0.12`) |
| Dragged | 16% (`0.16`) |
| Disabled | Container at ~12% opacity **or** explicit `on-surface` at 38% for text/icon — follow library defaults |

**Focus:** Always show visible **focus rings** for keyboard users (outline or inset ring using `primary` or `secondary` — match library).

**Do not** use only `opacity: 0.5` on the whole component without distinguishing disabled vs. pressed.

---

## Motion

- **Emphasis:** Motion clarifies hierarchy and feedback; avoid gratuitous animation.
- **Duration (guideline):** Short UI feedback **200–300ms**; medium transitions **300–400ms**; large structural changes **400–500ms**.
- **Easing:** Standard **emphasized** and **decelerated** curves as in M3 spec (libraries expose `cubic-bezier` presets — use them).
- **Reduced motion:** Respect `prefers-reduced-motion: reduce` — replace motion with instant state change or fade only.

---

## Layout and density

- **Baseline grid:** 4dp / 4px spacing grid; common increments: 4, 8, 12, 16, 24, 32.
- **Touch target:** Minimum **48 × 48 dp** for primary interactive targets (visual element can be smaller if hit area extends).
- **Margins:** Screen edge margins typically **16–24** on mobile, **24+** on larger breakpoints.
- **Max content width:** Constrain reading width for long `body-large` text (roughly 60–75ch) for marketing pages.

---

## Icons

- Prefer **Material Symbols** (variable font) or **Material Icons** with a consistent style: **Outlined**, **Rounded**, or **Sharp** — **one style per product**, not mixed.
- Icons use `on-surface`, `primary`, or `on-primary` depending on container; inactive uses `on-surface-variant`.

---

## Components (M3 names and variants)

Use these **component** and **variant** names when building UI or reviewing PRs.

### Buttons

- **Filled button** — highest emphasis; container `primary`, label `on-primary`.
- **Filled tonal button** — medium emphasis; `secondary-container` / `on-secondary-container` (or `primary-container` / `on-primary-container` per theme).
- **Outlined button** — medium; border `outline`, label `primary`.
- **Text button** — lowest emphasis; label `primary`, no container fill.

**Avoid** labeling these “primary/secondary/destructive” **without** mapping to the M3 variant above.

### FABs

- **FAB** (small, normal, large), **extended FAB** — use for the **primary screen action** only; do not duplicate multiple FABs without spec.

### Chips

- **Assist**, **Filter**, **Input**, **Suggestion** — correct M3 chip types; use `surface-variant` / `outline` patterns per spec.

### Navigation

- **Navigation bar** (mobile bottom), **Navigation rail** (tablet side), **Navigation drawer** (modal or standard) — pick by width breakpoint, do not stack redundantly.

### Text fields

- **Filled** and **Outlined** text fields; supporting text uses `body-small` and `on-surface-variant`; error uses `error` roles.

### Cards

- **Elevated**, **Filled**, **Outlined** — pick one family per surface context; content uses `headline-*` for title, `body-*` for body.

### Dialogs and sheets

- **Basic dialog**, **Full-screen dialog**; **Standard bottom sheet**, **Modal bottom sheet** — use `scrim`, correct corner tokens on sheets.

### Lists

- **One-line**, **Two-line**, **Three-line** list items; dividers use `outline-variant`.

### Tabs

- **Primary** vs **Secondary** tabs (M3 distinction); indicators use `primary` or `secondary`.

### Snackbar

- **Inverse** surface pattern; one concise `body-medium` line + optional action.

### Menus

- **Dropdown menu** anchored to inputs or buttons; elevation/container per library.

### Progress

- **Linear** and **Circular** indicators; use `primary` track.

### Switches, checkboxes, radio

- Use M3 control artwork and states; selected states tie to `primary`.

---

## Light and dark themes

- Provide **both** `light` and `dark` color schemes as full role maps (not inverted filters).
- Dark theme: surfaces are **not** pure black; use `surface`, `surface-container-*`, and `surface-bright` steps.
- Images and hero media: optional subtle `scrim` gradient for text contrast using `on-surface` / `on-primary`.

---

## Accessibility (non-negotiable)

- Text contrast: WCAG-aligned contrast for `body` and `label` on each surface (use role pairs validated in design).
- Do not rely on color alone for errors; use icon + text.
- Focus order matches reading order; modals trap focus.
- Hit targets and motion rules as above.

---

## What agents must not do

- Do not rename M3 roles to ad-hoc names without a documented mapping table in the repo.
- Do not default to iOS-only patterns (huge blur nav bars, SF Pro as sole font) when this style is active unless explicitly requested **in addition** with clear separation.
- Do not use neon glow, glassmorphism, or brutalist overlaps as the **primary** language when implementing **m3-material** — those are different style files in this repo.
- Do not invent new button types (“ghost”, “link”) without mapping them to **text button** or **outlined button** behavior and colors.

---

## Quick implementation checklist

- [ ] Color CSS variables (or theme object) include **all** roles in the tables above that the app uses.
- [ ] Typography uses **M3 style names** mapped to utilities or classes.
- [ ] Corner tokens applied per component category.
- [ ] Buttons use M3 **filled / tonal / outlined / text** naming.
- [ ] Elevation expressed via **surface container** steps + library elevation where applicable.
- [ ] State layers and focus visible for interactive elements.
- [ ] Material Symbols / Icons consistent style.
- [ ] Light + dark schemes + `prefers-reduced-motion` handled.

---

## Official links

- [Material Design 3](https://m3.material.io) — foundations, styles, components.
- Material Web Components and framework docs — implementation details and token exports.
