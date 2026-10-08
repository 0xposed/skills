---
name: interface-motion
description: Plan, implement, or improve purposeful motion in web interfaces. Use for animation, transitions, gestures, and motion performance; use interface-vocabulary for naming a UI or motion concept.
---
# Interface motion

Motion principles in this skill are adapted in part from [Emil Kowalski's design-engineering skill](https://github.com/emilkowalski/skills/tree/main/skills/emil-design-eng), then rewritten as framework-agnostic guidance.

Use this skill when motion is part of the requested web interface work. First inspect the project's framework, existing motion tools, tokens, and nearby patterns. Preserve them unless there is a clear reason to change.

## Decide before animating

- Identify what the motion communicates: feedback, state change, spatial relationship, continuity, or explanation. If it serves no clear purpose, leave the state change immediate.
- Consider frequency. Repeated actions should feel immediate; reserve longer or more expressive motion for infrequent moments.
- Choose the simplest tool that fits: CSS transitions for simple state changes; CSS animations for predetermined sequences; the Web Animations API or an existing motion library when programmatic control, gestures, springs, or coordinated layout changes need it. Do not add a dependency for a simple effect.
- Prefer animating `transform` and `opacity` when they express the effect well. This is a performance default, not a ban on other properties: height transitions, clipping, filters, and layout animation can be appropriate when brief and checked in context.

## Implement with care

- Keep motion consistent with the component's role and the project's existing timing and easing tokens. Treat reference values as starting points, not universal rules.
- Make enter and exit behavior coherent. Anchor menus and popovers to their trigger when the platform or component API exposes that relationship.
- For drag or gesture interactions, keep the element tracking the pointer, allow interruption and reversal, and settle from the current position. Prefer an existing accessible primitive or motion library over writing custom physics without a need.
- Respect `prefers-reduced-motion`. Reduce or remove nonessential movement while preserving useful state feedback and comprehension.
- Avoid animating every element, delaying interaction, or using `transition: all`. Gate hover-only motion for hover-capable pointers when touch behavior could be confusing.

## Verify the feel

Check the actual interaction when a browser or preview is readily available: entry, exit, repeated activation, interruption where relevant, narrow layouts, and reduced-motion behavior. If the animation's quality depends on timing or feel that cannot be judged from code, say what needs a visual check instead of claiming it is verified.

For common patterns, consult [motion recipes](references/motion-recipes.md). For a term or interaction name, use `interface-vocabulary`.

## Examples

Examples use a fictional e-commerce app (catalog, products, cart, and checkout) for consistency. This context is illustrative, not a requirement for projects using the skill.

- **DON'T:** Animate unrelated properties with an unbounded transition:

  ```css
  .add-to-cart { transition: all 300ms; }
  ```

- **DO:** Transition the property that communicates the interaction and respect reduced motion:

  ```css
  .add-to-cart { transition: transform 150ms ease; }
  .add-to-cart:active { transform: scale(0.97); }
  @media (prefers-reduced-motion: reduce) {
    .add-to-cart { transition: none; }
  }
  ```
