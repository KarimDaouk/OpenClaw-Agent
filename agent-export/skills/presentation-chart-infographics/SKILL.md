---
name: presentation-chart-infographics
description: Add, refine, and animate chart-style infographics in Remotion or React-based presentation videos. Use when a presentation needs pie charts, bar charts, KPI strips, mini-bar charts, infographic suitability logic, flashy but readable chart entrances, whitespace-safe placement, per-slide chart decisions, or chart/background/layout integration for presenter-plus-slide videos.
---

# Presentation Chart Infographics

Build chart infographics as stage elements, not decorative stickers.

## Core rules

- Show infographics only on slides where they add meaning.
- Prefer chart types that match the slide topic:
  - pie for part-to-whole mixes
  - bar for comparisons or pressure levels
  - KPI strip for fast headline metrics
  - mini bars for compact feature/value comparisons
- Put charts in true whitespace or dedicated safe corners.
- If a layout is crowded, hide or relocate the infographic instead of forcing it.
- Keep title + chart minimal in tight spaces.
- If a chart becomes unclear after simplifying labels, change the chart type rather than leaving it ambiguous.
- Use separate background decisions for intro and main slide stages when needed.

## Proven workflow

1. Identify whether the slide is suitable for an infographic.
2. Pick a chart type from the slide topic, not by randomness.
3. Place the chart in safe whitespace.
4. Verify it does not overlap:
   - headline
   - bullets
   - presenter/avatar
   - major image/visual panel
5. If the generic overlay path fails, inject directly into the visible slide stage.
6. Animate the chart with a delayed entrance so it feels intentionally introduced.
7. Rebuild and verify in live preview.

## Suitability guidance

Good infographic candidates:
- purpose
- technical requirements
- capabilities
- training
- testing
- benefits / quality
- risks

Usually avoid or use sparingly:
- overview/title slide
- scope
- responsibilities
- process slides unless there is clear quantitative structure

## Chart selection guidance

### Pie chart
Use for:
- stack mix
- share distribution
- part-to-whole breakdowns

Requirements:
- keep visible labels
- use compact legend if needed
- if the legend makes the chart too cramped, switch to a bar chart

### Bar chart
Use for:
- risk pressure
- gains over baseline
- comparison across dimensions

Requirements:
- stagger rows slightly
- animate bar growth after the card enters

### KPI strip
Use for:
- 2 to 4 direct metrics
- slides where speed of reading matters more than analytical detail

Requirements:
- one short label per metric
- pop in late with bounce

### Mini bars
Use for:
- compact multi-category comparisons
- capability/value distribution

Requirements:
- short labels only
- use staggered rise animation

## Placement rules

- Favor top-left or top-right outer corners first.
- Keep cards compact in corner placements.
- If the corner is visually busy, move to a lower whitespace pocket only if the stage remains breathable.
- If a mirrored layout breaks the placement, define explicit per-layout coordinates.
- If a slide keeps failing through the generic overlay path, place the infographic directly inside the slide stage.

## Animation rules

Aim for a "fashionably late entrance":
- let the audience see the slide first
- then reveal the infographic with a deliberate beat

Recommended timing:
- delay infographic card entrance by roughly 18–24 frames
- reveal chart internals after the card lands

Currently retained active styles:
- **Swoop entrance**
  - delayed slide-in
  - overshoot
  - glow hit
  - glossy flash
- **Vault burst**
  - compressed hidden start
  - burst outward into view
  - stronger impact feel

Per-chart motion:
- pie: radial sweep, then labels slide in
- bar: rows stagger and bars sweep in
- mini bars: staggered vertical pop-up
- KPI strip: metric pop and bounce

## Named chart transitions

### Chart Hero Transition

Definition:
- the chart enters large in the center
- holds there briefly for emphasis
- then shrinks and resolves into its final corner or side placement

Use for:
- benefit slides
- final-value slides
- moments where the chart should briefly become the main focal point before settling back into the layout

Rules:
- let the chart feel intentionally featured, not accidental
- keep the center hold long enough to be noticed
- resolve cleanly into a real final placement
- keep the chart’s internal animation active during the hero moment when appropriate

## Debugging rules

If a chart is not visible:
1. Check whether the slide is actually eligible via suitability logic.
2. Check whether the selected chart type matches the configured data payload.
3. Check whether the placement exists for the current layout state.
4. Raise z-index only if placement is known-good.
5. If still invisible, stop guessing and place a temporary obvious test block.
6. If the test block also fails, inject directly into the slide stage instead of the overlay path.

If a chart is visible but bad:
1. Reduce labels first.
2. Reduce card size second.
3. Move to safer whitespace third.
4. Change chart type if meaning becomes unclear.

## Background integration

- The intro background and main slide background may need different assets.
- If the deck uses a dark slide background, keep chart cards readable with a darker translucent panel and controlled glow.
- When swapping backgrounds from PowerPoint assets, verify the main slide stage separately from the intro.

## What to read next

If working on stage choreography or presenter motion too, also read:
- `../presentation-layout-director/SKILL.md`
- `../presentation-transition-state-director/SKILL.md`
- `../avatar-motion-director/SKILL.md`
- `references/remotion-chart-lessons.md`
