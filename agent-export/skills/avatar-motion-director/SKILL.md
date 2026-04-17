---
name: avatar-motion-director
description: Smooth presenter-avatar motion design for Remotion, React video systems, and branded presentation videos. Use when an on-screen avatar or presenter window needs to move between zones without looking choppy, when slide-to-slide position changes feel jumpy, when you need motion paths/easing/section-based choreography, or when building presentation videos where the avatar should shift smoothly while avoiding overlap with content.
---

# Avatar Motion Director

Design avatar movement as choreography, not as a set of hard jumps.

## Core rules

- Move only at meaningful moments: section changes, emphasis beats, or explicit layout conflicts.
- Keep the avatar stable for 2–3 slides when possible.
- Use one continuous motion value per property (`x`, `y`, `scale`, `opacity`) instead of swapping layouts abruptly.
- Prefer eased interpolation or springs over instant position changes.
- Combine small position shifts with slight scale changes to make movement feel intentional.
- Keep the avatar out of headline and bullet zones.
- Add only subtle idle drift; the presenter should not float constantly.

## Recommended workflow

1. Define safe anchor zones for the avatar.
2. Group slides into motion sections rather than moving every slide.
3. For each section, choose a target `x/y/scale` state.
4. Blend between section states over a transition window of 18–36 frames.
5. Add a tiny idle offset during holds.
6. Reduce movement during dense-content slides.

## Safe anchor pattern

For widescreen presentation videos, start with 4 safe zones:
- lower-right
- upper-right
- lower-left
- upper-left

Default to the right side unless content forces a change.

## Implementation pattern in Remotion

Represent motion as timeline keyframes, then interpolate against the global frame.

Example shape:

```ts
const avatarKeyframes = [
  {frame: 0, x: 0, y: 0, scale: 1},
  {frame: 240, x: -8, y: -120, scale: 0.98},
  {frame: 540, x: 0, y: 6, scale: 1},
  {frame: 840, x: -10, y: -110, scale: 0.99},
];
```

Then interpolate each property from the full keyframe list. Do not switch by `if slideIndex === ...` unless the movement is wrapped in a smooth transition function.

## Motion guidance

### Good
- Drift 6–16px during hold states.
- Reposition over 24–32 frames.
- Scale within `0.96–1.02`.
- Fade slightly during handoff moments.

### Bad
- Teleporting between corners on exact slide boundaries.
- Large moves on every slide.
- Constant bobbing that distracts from the presentation.
- Crossing over title or bullet areas.

## Default choreography recipe

- Intro: off or hidden
- Slides 2–4: anchor upper-right
- Slides 5–7: drift to lower-right over ~28 frames
- Slides 8–10: drift to upper-right or upper-left depending on content density
- Conclusion: settle lower-right with minimal movement

## Idle motion

When the avatar is holding position, add tiny motion only:
- `y = sin(frame / 28) * 2`
- `x = sin(frame / 45) * 1.5`

Keep total idle drift under 3px unless the user explicitly wants more energy.

## Overlap avoidance

If the slide has a dense bullet panel on the right, move avatar to a left-side or top-safe zone.
If the slide has a hero image on the left, keep avatar right.
If both sides are busy, reduce avatar size before moving it.

## What to read next

If you need concrete Remotion implementation details or reusable code patterns, read `references/remotion-motion-patterns.md`.
