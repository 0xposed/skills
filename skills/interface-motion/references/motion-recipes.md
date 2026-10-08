# Motion recipes

Adapted in part from the motion guidance in [Emil Kowalski's skills repository](https://github.com/emilkowalski/skills/tree/main/skills/emil-design-eng); recipes have been rewritten and generalized.

These are decision cues, not copy-paste prescriptions. Use the project's framework, component API, styles, and motion preferences. Check keyboard, touch, and reduced-motion behavior where relevant.

- **Press feedback:** a subtle, quick state change can confirm activation. Do not make the user wait for it before the action takes effect.
- **Popover or menu:** connect the panel visually to its trigger when possible; use the trigger as the transform origin. Preserve the primitive's focus and dismissal behavior.
- **Modal:** coordinate the surface and backdrop so they read as one state change. Keep the dialog centered unless its design has a clear spatial origin.
- **Drawer or sheet:** enter and exit along a coherent path. If it can be dragged, track the pointer and allow the gesture to be interrupted or reversed.
- **Accordion:** animate height only when it improves orientation; content changes, reduced motion, and layout cost matter more than avoiding height animation at all costs.
- **Staggered entrance:** use sparingly for short, occasional groups. Never make content or controls wait for a decorative sequence.
- **Scroll reveal:** reserve for content where revealing adds meaning, usually editorial or promotional surfaces. Do not repeatedly animate everyday content as it enters and leaves view.
- **State transition:** use a crossfade, morph, or layout transition when it helps preserve the identity or location of changing content. Prefer an immediate change when animation obscures or slows the task.
