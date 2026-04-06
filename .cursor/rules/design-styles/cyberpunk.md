---
globs: []
---

# UI Style: Cyberpunk

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion sells the HUD.** Use **fast** transitions, **glow pulses**, **scan-line** or **light sweep** accents, **glitch** (sparingly on headings), and **numeric tick-ups** for stats. Layer **idle** ambient motion (slow grid drift) only if it does not harm readability. **Always** gate intense effects behind **`prefers-reduced-motion`**.

## Visual Language
- High-tech, dystopian, and futuristic.
- Dense information UI with layered depth.
- Dark themes with high-energy accents.

## Color
- Neon pink, cyan, violet, electric blue, jewel tones.
- Predominantly dark base with bright highlights.
- Use glow effects deliberately for hierarchy.

## Typography
- Futuristic sans-serif or techno display faces.
- Optional glitch/distortion accents for headings only.
- Keep body text stable and readable.

## Components
- Holographic-looking panels, segmented controls, HUD-like cards.
- Fine lines, grid overlays, and scan elements.
- Strong hover/focus states for interactive elements.

## Layout
- Structured grids with layered informational modules.
- Dense but organized data presentation.
- Clear visual hierarchy is mandatory.

## Motion & animation
- **Interaction**: sub-200ms feedback on controls; **neon bloom** or **border flicker** on focus within tasteful limits.
- **Panels**: **slide + opacity** with slight **chromatic offset** optional; **data streams** can use **scrolling tickers**.
- **Charts**: **animated series reveal**, **pulsing highlights** on active series, **glow** on hover—keep **body text static** and readable.
- Provide a **calm mode** (reduced effects) when users prefer less motion.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Prefer libraries with strong theming + animation**: **Apache ECharts**, **ApexCharts**, or **Nivo** (neon-friendly); **React** → **Recharts** + custom CSS filters/glow wrappers.
- **Vue** → **ECharts**; **Angular** → **ECharts** or **ngx-charts** with custom styling.
- **Vanilla**: **ECharts** or **Chart.js** with plugin/custom canvas glow (measure performance).
- Map **palette** to neon accents on **dark canvas**; tooltips as **HUD panels**.
- **Animate** load and update; **disable or simplify** under **`prefers-reduced-motion`**.

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs. Images are free to use under the Unsplash License.
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. Match images to section topics--derive search terms from the page context.
- **URL format**: use `https://images.unsplash.com/photo-<PHOTO_ID>?w=<WIDTH>&q=80&auto=format` for optimized delivery. Set `w` to the rendered width needed.
- **Style fit**: prefer **dark, neon-lit, urban, or tech** photographs--night cityscapes, screens, circuits, moody lighting. Apply CSS `hue-rotate()`, `brightness()`, or overlay blends to push neon cyan/pink/violet tones.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` or `aspect-ratio` to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no suitable Unsplash image exists, use a **dark gradient panel** with neon accent borders rather than a mismatched stock photo.

## Avoid
- Soft pastel minimalism and low-contrast styling.
