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

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs (free under the Unsplash License).
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. Derive search terms from the page or section topic.
- **No broken links**: **NEVER fabricate or guess** an Unsplash photo ID or URL. Use **WebFetch** or **WebSearch** to search `unsplash.com/s/photos/<search-terms>` and extract a real, verified photo URL. If you cannot verify a URL, use a **CSS placeholder** instead of a potentially broken `<img>`.
- **URL format** (once verified): `https://images.unsplash.com/photo-<VERIFIED_ID>?w=<WIDTH>&q=80&auto=format`.
- **Style fit**: prefer images with **strong geometry, clear composition, and bold primary tones**. Flat, graphic photographs with visible structure work best. Apply CSS filters (contrast, saturation) if needed to align with the red/yellow/blue palette.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` or `aspect-ratio` to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no verified Unsplash image is available, use a **solid color block** in palette colors rather than a broken or mismatched image.

## Avoid
- Chaotic compositions and over-stylized textures.
