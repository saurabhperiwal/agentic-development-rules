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

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs. Images are free to use under the Unsplash License.
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. Match images to section topics--derive search terms from the page context.
- **URL format**: use `https://images.unsplash.com/photo-<PHOTO_ID>?w=<WIDTH>&q=80&auto=format` for optimized delivery. Set `w` to the rendered width needed.
- **Style fit**: prefer **vintage-toned, atmospheric, era-evoking** photographs--analog tech, retro interiors, neon signs, space-age architecture. Apply CSS `sepia()`, `hue-rotate()`, or grain overlays to push the retro mood.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` or `aspect-ratio` to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no suitable Unsplash image exists, use a **textured gradient panel** with era-appropriate grain rather than a mismatched stock photo.

## Avoid
- Bland generic UI that removes era-specific character.
