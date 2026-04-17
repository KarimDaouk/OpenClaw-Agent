# State Patterns

## Canonical paired states

Use these as mental defaults unless the project needs special variants.

### 1. Avatar right / content left
- Avatar occupies right presenter zone.
- Text/visual panels live left-of-center.
- Good default for balanced widescreen decks.

### 2. Avatar left / content right
- Mirrored version of the above.
- Use when the content benefits from switching emphasis sides.

### 3. Avatar top center / content below
- Avatar becomes the focal anchor.
- Lower content should be composed as one grouped unit.
- Good for emphasis, summaries, or speaker-led beats.

## Transition design pattern

For every transition, write this before coding:

- `from:` current state
- `to:` destination state
- `why:` structural or narrative reason
- `avatar:` path + end position
- `content:` path + end position
- `settled:` explicit final layout

Example:

```txt
from: avatar-top-center / content-below
to: avatar-right / content-left
why: resume side-led presentation after emphasis beat
avatar: top-center -> hero zoom -> right hold
content: below-grouped -> left presentation layout
settled: avatar-right / content-left
```

## Anti-patterns

Avoid these:

- Transition changes content but leaves avatar effectively unchanged
- Transition changes avatar but leaves content behind
- Transition has a visible move but settles into an old hidden default
- Transition direction is chosen from habit instead of current layout state
- Transition exits top-center without defining a real paired side state
