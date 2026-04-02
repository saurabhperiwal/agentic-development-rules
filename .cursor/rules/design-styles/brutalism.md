---
globs: []
---

# UI Style: Brutalism

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion is loud and intentional**—not polished easing curves. Prefer **abrupt cuts**, **stepped** or **near-instant** transitions, **hard scroll** behavior where appropriate, and **marquee/ticker** patterns for emphasis. Animation should feel **raw and structural**, never “premium smooth.” Still provide a **`prefers-reduced-motion`** path that removes seizure-adjacent flicker and excessive movement.

## Visual Language
- Raw, stark, and intentionally rough composition.
- Prioritize function and structure over polish.
- Strong asymmetry and anti-pattern layouts are acceptable.

## Color
- High-contrast palettes with bold clashes.
- Avoid subtle gradients and soft transitions.
- Prefer flat blocks of color.

## Typography
- Large, heavy sans-serif display type.
- Hard hierarchy with oversized headings.
- Minimal decorative type treatments.

## Components
- Boxy cards, sharp corners, thick strokes.
- Elements can look intentionally unrefined.
- Strong visual boundaries between sections.

## Layout
- Irregular grids and unconventional alignment.
- Dense blocks mixed with exaggerated whitespace.
- Use scale contrast aggressively.

## Motion & animation
- **State changes**: use **0ms–120ms** cuts or **steps()** keyframes; avoid long ease-in-out polish unless parodying corporate UI.
- **Hover/focus**: **invert colors**, **thick border swap**, or **instant position jump**—visibly digital feedback.
- **Lists and feeds**: **hard repaints**, optional **blink** or **ticker** (keep accessibility in mind—offer reduced motion).
- **Charts**: **snap** new values into place or use **stepped** draws; thick strokes, no soft gradients unless ironic.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Use a charting library** and **brutalize the theme**: chunky bars, **high-contrast** fills, **thick axes**, minimal rounding.
- **Stack defaults**: **Chart.js** / **Apache ECharts** / **ApexCharts** for fast defaults; **React** → **Recharts** with heavy stroke widths; **custom** → **D3.js** for deliberately rough layouts.
- Prefer **bar, column, and big-number** tiles over fiddly sparklines unless density is required.
- **Animation**: default to **short or off**; stepped updates match the aesthetic. **Respect `prefers-reduced-motion`** (disable blink/marquee).

## Avoid
- Glossy polish, soft shadows, and delicate UI details.
