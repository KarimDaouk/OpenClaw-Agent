---
name: presentation-layout-director
description: Build, refine, debug, and iterate branded presentation video layouts in Remotion or similar React-based slide systems. Use when creating presenter-plus-slide videos, fixing slide/avatar overlap, switching layouts across sections, mirroring content and avatar positions, improving branded slide composition, debugging broken presentation live previews, or tuning presentation pacing and visual engagement.
---

# Presentation Layout Director

Design presentation videos as stage compositions, not just slides.

## Core rules

- Keep the presenter/avatar and the presentation content in clearly separated zones.
- When moving the avatar, also reconsider the content layout; do not move one and leave the other stranded.
- Prefer section-based layout changes over constant movement.
- Choose transitions from the meaning and pacing of the content, not from rigid positional rules like always switching at the midpoint.
- For live previews, make one structural change at a time and verify before layering more complexity.
- If the live server breaks, fix build health first before chasing design issues.
- Use explicit coordinates for mirrored layouts when grid logic starts causing overlap or partial off-canvas placement.
- Keep avatar size stable unless there is a strong reason to animate scale.
- When the embedded avatar video becomes choppy in renders, suspect the asset pipeline before suspecting the motion design.

## Proven workflow

1. Start with a stable branded baseline layout.
2. Verify avatar playback quality in a static position.
3. Add motion only after playback is confirmed smooth in rendered output.
4. Decide transitions from the script and presentation rhythm:
   - section change
   - key message emphasis
   - tone shift
   - dense vs. light information moments
5. If a left/right switch is needed, switch the whole stage logic:
   - avatar side
   - content side
   - visual panel side
   - alignment accents
6. Test changes on the live server before full renders.
7. Render short verification clips before committing to a full export.

## Layout guidance

### Default presenter-plus-slide composition
- Keep a dedicated avatar block anchored to one side.
- Keep the main content panel on the opposing side.
- Keep hero/image panels large enough to feel intentional, not like leftovers.
- Reserve margins so nothing touches the avatar card.

### Content-driven transition pattern
Do not treat transitions as fixed formulas.
Choose them from the script structure and the visual rhythm of the deck.

Good triggers for a stronger transition:
- new section or chapter
- big benefit statement
- tone shift
- workflow stage change
- recap or conclusion moment

Good triggers for a lighter transition:
- continuation of the same idea
- supporting detail after a major point
- dense content where readability matters more than motion

If a layout switch is used:
- mirror both content and visual blocks together
- keep the avatar fully outside the content block
- avoid partial mirrored math that leaves elements stacked or clipped
- prefer a safe side-switch or hero-avatar transition only when the content justifies it

### Avoid
- Moving the avatar while leaving text in the same place
- Letting content drift behind the avatar
- Frequent side switching without a clear narrative reason
- Complex nested JSX edits without validating the build after each structural change

## Debugging rules

### If the live server looks frozen
Check whether the app actually failed to build.
Look for JSX mismatches, unterminated expressions, or broken fragments before assuming the dev server died.

### If content overlaps after a layout switch
Do not keep tweaking small offsets forever.
Instead:
- define explicit widths for avatar, content, and visual panels
- assign explicit left/right coordinates
- make sure the total composition fits inside 1920px with margins

### If the avatar video is smooth in the source file but choppy in the final render
Try these in order:
1. Verify the avatar while static
2. Use an overlay-specific version of the avatar asset
3. Re-encode with easier decode settings and frequent keyframes
4. Keep the avatar source matched to the render pipeline

## What to read next
If you need the specific lessons learned from this SANS presentation workflow, read `references/sans-remotion-lessons.md`.
