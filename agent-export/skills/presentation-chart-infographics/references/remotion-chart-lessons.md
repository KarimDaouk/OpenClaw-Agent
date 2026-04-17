# Remotion Chart Lessons

## Durable lessons from the SANS presentation workflow

### 1. A chart that technically renders may still be functionally invisible
Common causes:
- wrong layout-state placement
- overlay path not landing where expected
- chart placed behind more dominant stage elements
- chart too subtle for the chosen background

When in doubt, use a brute-force visible test block before continuing.

### 2. If a pie chart loses its labels, it may stop making sense
A pie chart without readable labels often becomes decorative noise.
If the legend cannot fit cleanly:
- shorten labels
- reduce legend complexity
- or switch to a bar chart

### 3. Generic overlay systems are useful but not sacred
If one slide keeps failing:
- stop over-generalizing
- inject directly into the slide stage for that case
- treat the exception as valid stage choreography, not a failure

### 4. Whitespace-safe placement matters more than forcing chart consistency
It is better to:
- hide a chart on a crowded state
- move it to a different corner
- or use a different chart type
than to cram it into content space.

### 5. Use late entrances so infographics feel intentionally introduced
Charts should not appear at the same moment as the main slide unless explicitly desired.
A delayed reveal makes the audience notice the chart as a purposeful addition.

### 6. Flashy motion works when the chart still settles quickly
Good motion recipe:
- delayed entrance
- assertive slide-in
- overshoot
- glow hit
- short gloss flash
- stable hold after reveal

Do not keep the chart in constant motion once revealed.

### 7. Background swaps must be validated on the actual main slide stage
Changing only the intro background is not enough.
Always test:
- intro background
- main slide background
separately.

### 8. Selection logic and rendering logic must agree
If the selector returns one chart kind and the configured slide data expects another, runtime bugs appear.
Use the configured chart kind as the source of truth when rendering slide-specific chart data.

## Practical reusable patterns

### Suitable slide topics
- purpose
- technical requirements
- capabilities
- training
- testing
- benefits
- quality
- risks

### Less suitable slide topics
- overview/title
- scope
- responsibilities
- process (unless explicitly quantitative)

### Good chart-type defaults
- pie: part-to-whole mixes
- bar: comparisons / pressure / progression
- KPI strip: short metric callouts
- mini bars: compact distribution comparisons

### Named chart motion vocabulary
- **Chart Hero Transition**: chart enters large in the center, holds briefly, then shrinks and settles into its final placement
- **Swoop entrance**: delayed slide-in with overshoot, glow hit, and gloss flash
- **Vault burst**: compressed hidden start, then bursts outward into view
