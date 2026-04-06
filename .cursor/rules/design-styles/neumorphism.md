---
globs: []
---

# UI Style: Neumorphism

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion is tactile and calm.** Animate **inset ↔ raised** shadow states, **soft press** depth, and **slow, gentle** opacity for focus changes. Durations often **200–400ms** with **smooth easing**—never hectic. Use subtle **skeleton shimmer** for loading. Charts should **ease** into new values, not snap. Respect **`prefers-reduced-motion`**.

## Visual Language
- Soft, tactile, and subtle 3D appearance.
- Surfaces feel gently raised or pressed.
- Calm visual mood with low visual noise.

## Color
- Monotone or near-monotone palette.
- Very subtle contrast between background and components.
- Use tints/shades rather than sharp color jumps.

## Typography
- Clean and understated.
- Medium weights over heavy display text.
- Maintain high readability despite soft visuals.

## Components
- Soft shadows (outer and inner) for depth cues.
- Rounded corners and pill-like controls.
- Inputs, cards, and toggles should feel physical.

## Layout
- Generous spacing and clean grouping.
- Keep interface density moderate to low.
- Preserve visual calm and consistency.

## Motion & animation
- **Controls**: on press, **inner shadow deepens** and element **translates 1px** “into” the surface.
- **Cards**: optional **slow float** on hover (very subtle) or **static** with only shadow shift—pick one system-wide.
- **Charts**: **soft tween** for bars/lines; avoid harsh jumps; keep **low-contrast** grid motion minimal.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- Prefer libraries where **fills and grids** can stay **soft** and **low-contrast**: **Chart.js** (rounded caps), **Apache ECharts** with muted theme, **React** → **Recharts** with **rounded** shapes and **pastel** series.
- **Vue** / **Angular**: **vue-chartjs**, **ngx-charts**—theme to **monotone** surfaces.
- **Custom**: **D3.js** only if you need neumorphic **custom shading** per segment (high effort).
- **Animate** updates gently; **flatten** motion under **`prefers-reduced-motion`**.

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs. Images are free to use under the Unsplash License.
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. Match images to section topics--derive search terms from the page context.
- **URL format**: use `https://images.unsplash.com/photo-<PHOTO_ID>?w=<WIDTH>&q=80&auto=format` for optimized delivery. Set `w` to the rendered width needed.
- **Style fit**: prefer **soft, muted, low-contrast** photographs that blend into the monotone surface. Use CSS `filter: saturate(0.5) brightness(1.05)` or similar to match the neumorphic palette. Images should feel embedded, not overlaid.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` or `aspect-ratio` to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no suitable Unsplash image exists, use a **soft-shadow inset placeholder** tinted to the surface color rather than a mismatched stock photo.

## Avoid
- Harsh borders, neon palettes, and heavy outlines.
