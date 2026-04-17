---
name: presentation-transition-state-director
description: Design, debug, and implement presenter-plus-slide transition systems for Remotion or similar presentation videos. Use when adding or refining named transitions, moving an avatar/presenter relative to slide content, diagnosing bad stage choreography, fixing layout-state bugs, or enforcing context-driven motion rules where avatar and content must move together.
---

# Presentation Transition State Director

Treat presentation transitions as **layout state changes**, not one-off coordinate tweaks.

## Core rules

- Define the current stage state before changing anything.
- Define the destination stage state before animating anything.
- Move **avatar and content together** during transitions.
- Never treat a transition as avatar-only or content-only unless the user explicitly asks for that.
- Never assume a fixed left-to-right or right-to-left direction.
- Choose transition direction from the **current content/layout state** at that moment in the video.
- Do not use a transition as a disguised "return to home" move.
- After a transition, ensure both avatar and content have an explicit settled state.

## Required workflow

1. Identify the current layout state.
2. Name the destination layout state.
3. State what happens to:
   - avatar position
   - content position
   - scale changes
   - any temporary emphasis treatment
4. Implement the motion so the source and destination are both real states.
5. Verify the post-transition state is not a lingering blend.
6. Verify the avatar and content still make compositional sense after the move.

## Preferred state model

Use named stage states such as:

- `avatar-right / content-left`
- `avatar-left / content-right`
- `avatar-top-center / content-below`

For each named transition, think in this form:

- source state
- destination state
- transition window
- settled result

## Named transition guidance

### Hero side-switch transition

Use for a featured moment.

- Start from the **current** side/state.
- Perform the hero zoom/emphasis.
- Land in the **opposite valid side layout**.
- Move content with the avatar as part of the same stage change.

### Side-swap transition

Use for a clean mirrored handoff.

- Swap avatar side and content side together.
- Keep it simpler than the hero transition.
- Avoid adding fake emphasis if the purpose is structural rebalancing.

### Top-center transition

Use when the presenter should become the visual focal point.

- Move avatar to top center.
- Arrange content clearly beneath the avatar.
- Center the avatar relative to the lower content grouping, not just the frame.
- Ensure the exit from this state resolves into a valid paired side layout.

## Debug checklist

When a transition looks wrong, check these in order:

1. Did only the avatar move?
2. Did only the content move?
3. Did the transition resolve to a real settled state?
4. Did the implementation accidentally preserve a hidden default/home position?
5. Is the post-transition layout driven by explicit state, or by leftover interpolation?
6. Is the avatar centered relative to the content grouping or only to the frame?

## Implementation advice

- Prefer explicit state variables or state-phase logic over scattered one-off coordinates.
- If there are multiple transitions in one deck, model the sequence as a small layout state machine.
- Keep source/destination coordinates easy to inspect.
- When a transition exits a special state like top-center, explicitly choose one of the valid paired side outcomes.

## What to read next

If you need stronger motion choreography guidance, read:
- `../avatar-motion-director/SKILL.md`
- `../presentation-layout-director/SKILL.md`
