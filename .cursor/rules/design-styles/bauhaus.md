---
globs: []
---

# UI Style: Bauhaus

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion is disciplined but essential.** Animate **geometric state changes**—slides along grid axes, **color-block** transitions, and clear **primary-color** feedback. Timing should feel **machine-precise** (often 120–280ms). Use stagger sparingly and **on-grid**. Respect **`prefers-reduced-motion`**.

## Visual Language
- Functional, geometric, and ordered.
- Form follows function.
- Use composition that feels engineered and clear.

## Color
- Primary palette focus: red, yellow, blue with black/white.
- Controlled color accents rather than full-spectrum palettes.
- Strong contrast and visual balance.

## Typography
- Clean sans-serif with geometric character.
- Clear hierarchy with disciplined type scale.
- Avoid decorative type effects.

## Components
- Basic geometric forms: circles, squares, triangles.
- Functional UI controls with minimal ornament.
- Visual consistency through repetition of shape language.

## Layout
- Grid-first design with strict alignment.
- Balanced composition and intentional whitespace.
- Predictable rhythm across sections.

## Motion & animation
- **Compose motion from primitives**: translate on X/Y aligned to the layout grid; **opacity** for layer changes; **rotate** only for clear metaphors (e.g. play, refresh).
- **Micro-interactions**: buttons and controls should **shift fill** or **translate 1–2px** on press; focus rings appear with **instant or near-instant** clarity.
- **Page and section**: optional **staggered block entrance** (rectangles sliding into register) on first paint—not decorative flourishes.
- **Charts**: animate **bar/segment growth** along one axis; keep easing **linear or ease-out**; no ornamental bounce.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Use a charting library**; theme it to **primary palette** (red/yellow/blue + black/white) and **strict geometry**.
- **Stack defaults**: **React** → **Recharts** or **Tremor**; **Vue** → **vue-chartjs** or **ECharts**; **Angular** → **ngx-charts**; **vanilla / multi-stack** → **Chart.js** or **Apache ECharts**; **deep custom** → **D3.js**.
- Prefer **rectilinear** chart types first (bars, stacked bars, simple lines); **grids and ticks** as clear structural lines.
- **Animate data updates** with short tweens; honor **`prefers-reduced-motion`**.

## Avoid
- Chaotic compositions and over-stylized textures.
