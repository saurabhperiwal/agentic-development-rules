---
globs: []
---

# UI Style: Glassmorphism

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion should feel like glass moving in space:** **blur/frost transitions**, **opacity + translate**, **scale** for depth, and **backdrop-filter** changes on hover. Keep motion **smooth but light** (often 200–350ms, **ease-out**). Charts and cards should **float** into place with soft staging. Respect **`prefers-reduced-motion`** (reduce blur animation and parallax).

## Visual Language
- Frosted glass layers over vibrant, blurred backgrounds.
- Light, airy, and modern with strong depth perception.
- Minimal composition with emphasis on translucent surfaces.

## Color
- Colorful gradient backgrounds with soft blur/bokeh.
- Foreground elements use translucency and low-opacity fills.
- Maintain enough contrast for readability and accessibility.

## Typography
- Clean, modern sans-serif typography.
- Strong text contrast against translucent layers.
- Keep hierarchy simple and elegant.

## Components
- Frosted cards, panels, dialogs, and floating controls.
- Subtle borders and inner highlights for glass edge definition.
- Buttons can use semi-transparent fills and light gradients.

## Layout
- Layered composition with clear z-depth ordering.
- Keep spacing generous to avoid visual clutter.
- Avoid overstacking too many translucent panels.

## Motion & animation
- **Panels**: fade/slide with **backdrop blur** settling; modals **scale in** slightly from ~0.96–1.
- **Hover**: **brighten edge highlight** and **lift** (translateY) subtly; avoid heavy shadows—use **layer separation**.
- **Charts**: **ease-in-out** data morphs; **crossfade** series; tooltip as **frosted popover**.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Libraries that theme well on layered UI**: **Apache ECharts**, **ApexCharts**, **Nivo** (semi-transparent fills), **Chart.js**; **React** → **Recharts** with **custom glass tooltip** containers.
- **Vue** → **ECharts** / **vue-chartjs**; **Angular** → **ngx-charts** or **ECharts** with translucent panels behind canvas/SVG.
- Place charts **inside frosted cards**; align **grid/tick** opacity with glass borders for cohesion.
- **Animate** load and updates; **simplify blur/parallax** when **`prefers-reduced-motion`** is set.

## Avoid
- Opaque heavy blocks that remove the glass effect.
