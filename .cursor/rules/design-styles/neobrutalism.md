---
globs: []
---

# UI Style: Neobrutalism

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion is playful and graphic.** Animate **hard-shadow offset** on press (shadow “sticks” then snaps back), **snappy** scale pops, and **bold color flashes** on success/error. Durations are usually **fast** (100–220ms) with **small overshoot** optional. Stagger **card entrances** for dashboards. Respect **`prefers-reduced-motion`** (skip overshoot; shorten shadows).

## Visual Language
- Playful, bold, and graphic with modern product clarity.
- Deliberately loud visual hierarchy.
- Strong personality over neutral minimalism.

## Color
- Bright, clashing, highly saturated colors.
- Clear foreground/background separation.
- Keep colors confident and simple.

## Typography
- Huge, bold sans-serif headings.
- Straightforward body text for readability.
- High weight contrast between heading and supporting text.

## Components
- Thick black borders around cards, inputs, and buttons.
- Hard shadows with visible offset.
- Large rounded corners or square corners used consistently.

## Layout
- Simple block composition with punchy spacing.
- Asymmetry is welcome if readability remains strong.
- Use obvious grouping and section boundaries.

## Motion & animation
- **Buttons/cards**: on press, **translate** opposite the shadow direction; on release, **spring** back.
- **Modals/toasts**: **slide in** with thick border; **no** feathery fades—keep edges crisp.
- **Charts**: **pop-in** bars, **bold legend** toggles; animation reads as **sticker motion**.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Libraries**: **Chart.js**, **Apache ECharts**, **ApexCharts** (bold defaults); **React** → **Recharts** / **Tremor** with **thick strokes** and **offset shadow** on chart cards (CSS).
- **Vue** → **vue-chartjs** / **ECharts**; **Angular** → **ngx-charts** or **ECharts**.
- **Custom** → **D3.js** for chunky, poster-like charts.
- Theme **grids** as strong lines; **palette** saturated; **animate** updates in **short snaps**.
- Honor **`prefers-reduced-motion`**.

## Avoid
- Subtle, low-contrast palettes and soft visual treatment.
