# Long-term Memory

## Presentation transition system

- Official named transitions currently in use:
  - **Hero side-switch transition**: a featured midpoint transition where the avatar performs a hero zoom and the stage settles with avatar/content on the opposite side.
  - **Side-swap transition**: a coordinated stage swap where the avatar placement and slide layout switch sides together without the hero zoom treatment.
  - **Top-center transition**: the avatar moves to the top center while the presentation content is arranged beneath it, with the avatar horizontally centered between the lower content blocks.
- Important preference: these transitions are **not** inherently left-to-right or right-to-left. Their direction and behavior should be chosen from the content layout and stage state at that moment in the video, not from a fixed rule.
- Durable motion rule: the avatar always moves depending on where the content is at that moment; transition choreography must be context-driven by the live layout.
