---
globs: []
---

# UI Style: Retro Futurism

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion is part of the era fantasy:** **phosphor fade**, **subtle scanlines**, **CRT-style** flicker (very restrained), **neon tube** illuminate, and **sweep** transitions. Use **sound-free** UI metaphors only. Keep body copy **stable**; animate **chrome** around it. **Strongly** respect **`prefers-reduced-motion`** (disable flicker, reduce sweeps).

## Visual Language
- Nostalgic future aesthetic inspired by past-era visions.
- Mix vintage motifs with futuristic UI structure.
- Bold thematic atmosphere is part of usability.

## Color
- Either neon arcade palettes or warm vintage tones.
- High identity color schemes over neutral palettes.
- Use contrast to emphasize interactive elements.

## Typography
- Display fonts with retro/sci-fi influence.
- Keep body text legible and modern.
- Use stylized headings sparingly but confidently.

## Components
- References to analog controls and old hardware forms.
- Cards/panels can include texture, grain, or scanline effects.
- Icons may be pixel-inspired or poster-like.

## Layout
- Creative composition with overlaps and layered depth.
- Controlled asymmetry is acceptable.
- Preserve strong reading flow despite stylistic treatment.

## Motion & animation
- **Entrances**: **wipe** or **fade with horizontal band**; **title** can **glow on** once.
- **Interaction**: **button** gets **tube glow** pulse; **panels** **slide** with **slight overscan** optional.
- **Charts**: **line draw** like a **scope**; **bar grow** with **post glow**; **palette** matches neon/warm vintage lane.

## Dashboards & charting
When building **dashboards, analytics, or admin UIs**:
- **Libraries with stylable SVG/canvas**: **Apache ECharts**, **Nivo**, **Chart.js** (custom plugins), **ApexCharts**; **React** → **Recharts** + **CSS** scanline/glow wrappers; **custom** → **D3.js** for CRT-style paths.
- **Vue** → **ECharts**; **Angular** → **ECharts** / **ngx-charts** with heavy theming.
- Build **dashboard tiles** as **retro panels**; animate **series reveal** on load and **refresh**.
- **Disable** flicker/sweep and **shorten** all motion when **`prefers-reduced-motion`** is set.

## Avoid
- Bland generic UI that removes era-specific character.
