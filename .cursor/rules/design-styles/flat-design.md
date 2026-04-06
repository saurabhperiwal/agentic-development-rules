---
globs: []
---

# UI Style: Flat Design

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion clarifies, not decorates.** Use **quick** (150–250ms) **opacity, slide, and scale** for feedback; **consistent easing** across components. Animate **lists** (enter/exit), **skeleton → content** swaps, and **chart redraws** so state changes are obvious. Respect **`prefers-reduced-motion`**.

## Visual Language
- Minimal, clean, two-dimensional interface treatment.
- Prioritize clarity, usability, and scalability.
- Remove unnecessary decorative effects.

## Color
- Solid, vibrant colors with clear semantic meaning.
- Strong contrast for readability.
- Limited palette with disciplined usage.

## Typography
- Legible sans-serif fonts with clear hierarchy.
- Weight and size define structure, not decorative effects.
- Keep copy concise and scannable.

## Components
- Simple buttons, cards, and controls with clean edges.
- Minimal shadows; use spacing and contrast for separation.
- Icons should be geometric and easily recognizable.

## Layout
- Grid-based structure with predictable alignment.
- Ample whitespace and straightforward flow.
- Keep interaction paths obvious.

## Motion & animation
- **Micro**: pressed states via **tint change** or **1–2% scale**; focus rings **instant**.
- **Macro**: page/section transitions **simple** (fade or short slide); avoid 3D flips and heavy parallax.
- **Data**: when values update, **tween numbers** and **morph bars/lines** subtly—flat color only.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Use a mainstream charting library** with flat theming: **Chart.js**, **Apache ECharts**, or **ApexCharts**; **React** → **Recharts** or **Tremor**; **Vue** → **vue-chartjs** / **ECharts**; **Angular** → **ngx-charts**.
- **Custom visuals**: **visx** or **D3.js** when you need unique flat geometry (justify the cost).
- **Charts** should match **solid fills**, **clear grids**, and **semantic colors**; tooltips **flat**, not glassy.
- Enable **tweened updates** where helpful; reduce motion per **`prefers-reduced-motion`**.

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs. Images are free to use under the Unsplash License.
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. Match images to section topics--derive search terms from the page context.
- **URL format**: use `https://images.unsplash.com/photo-<PHOTO_ID>?w=<WIDTH>&q=80&auto=format` for optimized delivery. Set `w` to the rendered width needed.
- **Style fit**: prefer **clean, well-lit, minimal-background** photographs. Simple compositions with solid or near-solid backgrounds integrate best with flat surfaces. Avoid busy textures or heavy bokeh.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` or `aspect-ratio` to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no suitable Unsplash image exists, use a **solid semantic-color block** rather than a mismatched stock photo.

## Avoid
- Skeuomorphic textures, heavy gradients, and visual clutter.
