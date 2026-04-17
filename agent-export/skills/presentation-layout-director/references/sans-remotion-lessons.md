# SANS Remotion Lessons

## What worked

### Brand inputs
Useful inputs for branded presentation generation:
- brand guidelines PDF
- branded PowerPoint template
- script text
- presenter/avatar source video

### Playback quality fix
The biggest rendering lesson from this workflow:
- the original avatar source looked fine alone
- the choppiness showed up inside the Remotion render path
- the best fix was not constant motion tweaking

The winning avatar pipeline was:
1. create an overlay-sized avatar asset
2. encode it with easier decode settings
3. use frequent keyframes
4. use that optimized asset inside the presentation render

A successful variant used:
- reduced overlay resolution
- H.264
- frequent keyframes (`-g 25`, `-keyint_min 25`, no scenecut)

### Motion lesson
Do not animate everything at once.
Better sequence:
1. fix avatar playback
2. test static avatar render
3. add motion back gradually

### Layout lesson
For mirrored presentation layouts, partial grid flipping caused confusion and overlap.
What worked better was a more literal mental model:
- define panel widths
- define explicit positions
- switch the entire side assignment intentionally

## User preference learned
The user preferred:
- branded presentations over generic styling
- live-server review before rendering
- more engaging layouts that do not feel repetitive
- avatar/content opposition for visual balance
- switching once by halves rather than excessive movement
- practical iteration over theoretical discussion

## Process lesson
When exploring presentation motion/layout changes:
- avoid large risky edits directly in a live file
- verify build health after structural JSX changes
- prefer one clear layout experiment at a time
- if the live server breaks, restore a known-good state first

## Transition patterns to keep

### Safe side-switch transition
- Move the avatar from one side to the other.
- Switch the content and visual panels accordingly.
- Keep it smooth and professional.
- Use it for structure changes.

### Section-based slide transition
- Change layout only at meaningful moments.
- Do not switch every slide.
- Use this to keep the presentation cleaner and less chaotic.

### Hero avatar transition
- Let the avatar zoom in for emphasis during a switch.
- Then let it settle into the new side.
- Prefer a controlled version rather than an overwhelming full-screen takeover.
