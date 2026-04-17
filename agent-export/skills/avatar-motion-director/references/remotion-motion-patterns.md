# Remotion Motion Patterns

## Timeline keyframes

Use a single timeline of target states and interpolate from the current frame.

```ts
const avatarKeyframes = [
  {frame: 0, x: 0, y: 0, scale: 1, opacity: 1},
  {frame: 240, x: -8, y: -116, scale: 0.985, opacity: 1},
  {frame: 540, x: 2, y: 4, scale: 1, opacity: 1},
  {frame: 840, x: -10, y: -104, scale: 0.99, opacity: 1},
];

const frames = avatarKeyframes.map((k) => k.frame);
const x = interpolate(frame, frames, avatarKeyframes.map((k) => k.x), {
  extrapolateLeft: 'clamp',
  extrapolateRight: 'clamp',
  easing: Easing.bezier(0.22, 1, 0.36, 1),
});
```

## Idle drift

```ts
const idleX = Math.sin(frame / 45) * 1.5;
const idleY = Math.sin(frame / 28) * 2;
```

Apply idle drift on top of keyframed motion, not instead of it.

## Section-based movement

Map slides into sections first, then create section anchors.
This avoids overreacting to every individual slide.

Example:
- section 1: slides 2–4
- section 2: slides 5–7
- section 3: slides 8–10
- section 4: slide 11

## Presenter window sizing

For 1920x1080 presentations, start around 320–380px width for the avatar window.
Reduce scale before large repositioning if layout is crowded.

## Visual smoothing tips

- Use eased interpolation for long travel.
- Use spring only for entrance/settle moments.
- If motion feels robotic, add a slight scale shift (`±0.01`).
- If motion feels floaty, shorten the transition window or reduce idle drift.

## Troubleshooting

### Problem: movement still feels jumpy
- Check for hard `if/else` layout swaps.
- Ensure every property is interpolated from the same timeline.
- Increase transition duration.

### Problem: avatar distracts from content
- Move less often.
- Shrink the avatar 3–6%.
- Limit idle drift.

### Problem: avatar overlaps bullets
- Move section anchor earlier.
- Reserve the bullet-side panel as a no-fly zone.
