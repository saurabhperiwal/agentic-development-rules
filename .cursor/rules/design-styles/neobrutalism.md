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

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs (free under the Unsplash License).
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. Derive search terms from the page or section topic.
- **No broken links**: **NEVER fabricate or guess** an Unsplash photo ID or URL. Use **WebFetch** or **WebSearch** to search `unsplash.com/s/photos/<search-terms>` and extract a real, verified photo URL. If you cannot verify a URL, use a **CSS placeholder** instead of a potentially broken `<img>`.
- **URL format** (once verified): `https://images.unsplash.com/photo-<VERIFIED_ID>?w=<WIDTH>&q=80&auto=format`.
- **Style fit**: prefer **bright, graphic, punchy** photographs with bold subjects. Images should feel playful and confident. Apply CSS `saturate()` or `brightness()` to push vibrancy if needed. Pair with **thick borders** around image containers.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` or `aspect-ratio` to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no verified Unsplash image is available, use a **saturated color block** with the neobrutalist palette rather than a broken or mismatched image.

## Avoid
- Subtle, low-contrast palettes and soft visual treatment.
