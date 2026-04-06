---
globs: []
---

# UI Style: Origami

Use this rule as a style reference. Keep it in library mode (`globs: []`) until selected for a project.

## Animation priority

**Motion is part of the system.** Prefer interfaces that **unfold, re-layer, and respond**—not static screens. Use animation for **orientation** (section enters, facet shifts), **feedback** (hover, press, success), and **data change** (chart series updates, KPI ticks). Keep durations **short-medium** (150-400ms typical), easing **crisp** (`ease-out`, custom cubic-bezier), and always respect **`prefers-reduced-motion`**.

## Concept

Treat the interface as **folded paper in space**: crisp creases, flat facets, and a sense that every surface could be unfolded into a single sheet. The mood bridges **craft discipline** (precision, restraint, negative space) with **trust** (structure, clarity, durable forms).

## Visual Language

- **Heavy origami**: favor **large folded planes** in layout (hero panels, section dividers, card faces) over tiny decorative corners. Sections can read as **stacked or interlocking modules** like modular origami units.
- **Crease grammar**: use **thin, high-contrast lines** (1px hairlines or 2px at most) to suggest fold lines; optional **secondary "valley" lines** (lighter or dashed) for depth without shadows.
- **Facets, not fluff**: backgrounds are **flat color fields** separated by folds; avoid noisy textures. If texture appears, keep it **extremely subtle** (fine paper grain at low opacity).
- **Geometry**: triangles, rhombuses, chevrons, and **polygonal silhouettes** for containers. Corners may be **cut or chamfered** (origami "tabs") instead of only rounded rectangles.
- **Depth without skeuomorphism**: imply depth with **overlapping planes** and **offset facets** (slight hue steps), not heavy drop shadows. At most **one soft, tight shadow** on primary actions if contrast requires it.

## Color

- **Paper-forward**: off-white, warm gray, or cool gray bases (`#f7f5f0`, `#f4f6f8`) as the "sheet."
- **Ink and trust**: deep indigo, slate, or rich black for text and primary structure.
- **Controlled accents**: a single **vermillion** or **indigo** accent for CTAs and key facets; optional **muted gold** for premium or "value" moments. Avoid rainbow gradients.
- **Facet shading**: differentiate adjacent planes with **2-4% lightness steps** or **shared hue, shifted saturation**--as if light hits one face of a fold.

## Typography (origami-inspired)

Type should feel **cut, folded, and engineered**--not calligraphic excess.

- **Primary (UI body)**: geometric humanist or neo-grotesque with **clear terminals and even rhythm**--e.g. **Inter**, **IBM Plex Sans**, or **Noto Sans**.
- **Display / headings**: choose faces with **angular or constructed character**--e.g. **Syne**, **Outfit**, **Space Grotesk** for a sharp, engineered feel.
- **Rules**: strong **size and weight hierarchy**; generous line-height; **avoid outline-only display type** unless used sparingly for hero words. **Letter-spacing**: slightly tight for large display, neutral for body.
- **Optional pairing**: a clean **serif** (e.g. **Noto Serif**, **Source Serif**) for quotes or editorial asides--use sparingly.

## Icons: code-generated, content-aware origami marks

Icons are **not** generic flat clipart. They are **generated or composed in code** (SVG, CSS clip-path, or canvas) so they stay **sharp, themeable, and aligned to the copy** they accompany.

### Generation principles

1. **Derive geometry from meaning**: map content to a small library of **primitives**--`triangle`, `kite`, `rhombus`, `trapezoid`, `chevron`, `ribbon`, `bird silhouette simplified to 3-5 polygons`. Favor **stacked facets** (layers = growth), **folded ribbons** (flow), **hexagonal units** (stability).
2. **Fold lines are part of the icon**: every icon includes **1-3 crease strokes** (or negative-space gaps) so it reads as **paper**, not a flat logo blob.
3. **Consistency contract**: fixed **grid** (e.g. 24x24 with 2px safe area), shared **stroke width**, shared **corner cut** angle (e.g. 15 or 30 degrees) across the set.
4. **Theming**: icons use **currentColor** or CSS variables for fills and strokes so they adapt to light/dark facets.
5. **Content hook**: when generating pages or sections, **tie icon variant to section keywords** (e.g. "savings" = ascending stacked triangles; "security" = interlocking folds; "location" = minimal **mountain** facet abstraction--geometric, not literal emoji).

### Implementation hints (for agents and devs)

- Prefer **inline SVG** with `<polygon>` / `<path>` built from documented coordinates, or small functions that emit points from angles.
- **CSS**: `clip-path: polygon(...)` for hero shapes and cards; `linear-gradient` with hard stops for **two-tone facets**.
- **Motion**: use **unfold** and **facet slide** animations liberally (rotate/translate child facets, clip-path reveals, staggered list entrance). Typical **200-400ms**, **ease-out**; **stagger** siblings by 30-60ms for panels and cards. Never bouncy or cartoon parody.

## Components

- **Buttons**: flat facet shapes; primary button reads as **one folded tab** (e.g. bottom edge or corner cut). Hover: **shift facet color** or **reveal a second plane**, not glow.
- **Cards**: parallelogram or **offset rectangle** shells; header strip as a **contrasting narrow facet**.
- **Data**: charts as **folded ribbons** or **triangular area segments**; axes as **crease lines**. Keep data legibility first.
- **Navigation**: underline or active state as a **small folded ribbon** under the label, not a pill unless the pill is faceted.

## Layout

- **Grid-first**, with **diagonal rhythm** allowed: occasional **full-bleed diagonal bands** that echo fold lines.
- **Whitespace** is intentional--generous negative space between sections is as important as content blocks.
- Align major edges to a **strict column grid**; origami chaos belongs in **controlled** decorative bands, not in misaligned text.

## Motion & animation

- **Default toolkit**: CSS `transform` / `opacity` on facets; **SVG stroke** or **path** transitions for crease emphasis; optional **view transitions** (where supported) for route or tab changes.
- **Patterns to use often**: unfold on expand (accordions, drawers); **facet swap** on hover for buttons; **crossfade** between menu or dashboard states; **number/count** tick for KPIs (subtle).
- **Charts**: animate **series draw** (line draw, bar grow) and **updates** so changes read as **refolding** data--aligned timing with card transitions.
- Avoid long elastic easing, confetti, and paper-crinkle metaphors in UI.

## Dashboards & charting

When building **dashboards, analytics, or admin UIs**:

- **Use a dedicated charting library**; do not rebuild axes, scales, legends, or interaction from scratch unless the scope is trivial.
- **Pick by stack** (choose one and theme it to this style):
  - **React**: **Recharts** or **Tremor** for dashboards; **Nivo** for richer visuals; **visx** when you need bespoke geometry aligned to origami facets.
  - **Vue**: **vue-chartjs** or **Apache ECharts** (`vue-echarts`).
  - **Angular**: **ngx-charts** or **ECharts** bindings.
  - **Framework-agnostic**: **Chart.js**, **ApexCharts**, or **Apache ECharts** (strong animation hooks and theming).
  - **Fully custom / artistic**: **D3.js** (higher effort--justify with unique facet-based visuals).
- **Style charts** like the rest of the UI: **flat fills**, **hairline grid/axes** (crease-like), minimal decoration; tooltip panels as **small facets**.
- **Motion**: enable library **tweened updates** for data changes; disable or shorten under **`prefers-reduced-motion`**.

## Avoid

- Heavy skeuomorphism (embossed metal, leather).
- Busy crumpled-paper textures and drop-shadow stacks.
- Over-rounded "bubble" UI that fights angular folds.
- Rainbow gradients and neon unrelated to brand.
- Raster origami clip art when **code-generated** facets are feasible.

## Imagery

- **Source**: use **[Unsplash](https://unsplash.com)** for all photographs (free under the Unsplash License).
- **Relevance over decoration**: every image must relate to the **project's domain and content**. Do not use generic stock scenery. A restaurant site gets food and interior shots; a fintech dashboard gets workspace or cityscape imagery; a portfolio gets craft and material close-ups.
- **Search strategy**: derive Unsplash search terms from the **page or section topic** (e.g. for an "About the team" section on a clinic site, search `medical team portrait`, not `random office`).
- **No broken links**: **NEVER fabricate or guess** an Unsplash photo ID or URL. To get a valid image:
  1. Use the **WebFetch** or **WebSearch** tool to search `unsplash.com/s/photos/<search-terms>` and extract a real photo URL from the results.
  2. Only embed URLs you have **verified exist** by fetching them.
  3. If you cannot verify a URL at build time, use a **CSS placeholder** (styled to this design system) instead of a potentially broken `<img>` tag.
- **URL format** (once verified): `https://images.unsplash.com/photo-<VERIFIED_ID>?w=<WIDTH>&q=80&auto=format`. Set `w` to the rendered width (e.g. `800`, `1200`, `1600`).
- **Style fit**: prefer images with **clean composition, restrained color, and visible structure**--photographs that feel like they could sit on a folded paper surface. Desaturate or tint in CSS if needed to match the paper/ink palette.
- **Lazy loading**: always add `loading="lazy"` and explicit `width`/`height` attributes (or `aspect-ratio` in CSS) to prevent layout shift.
- **Alt text**: every `<img>` must have a **descriptive, project-relevant** `alt` attribute. Never leave it empty or generic.
- **Fallback**: if no verified Unsplash image is available, use a **solid color facet placeholder** styled to the origami palette rather than a broken or mismatched image.
