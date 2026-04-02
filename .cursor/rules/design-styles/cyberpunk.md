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

## Avoid
- Soft pastel minimalism and low-contrast styling.
