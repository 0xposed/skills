---
name: interface-vocabulary
description: Identify and distinguish names for UI components, interaction patterns, layout concepts, visual effects, and motion. Use when someone describes an interface element or effect but does not know its term.
---
# Interface vocabulary

The motion terminology and lookup approach are adapted in part from [Emil Kowalski's animation-vocabulary skill](https://github.com/emilkowalski/skills/tree/main/skills/animation-vocabulary), with additional UI and layout terms.

Translate the user's description into the common interface term they can use in design or engineering discussion.

- Lead with the best matching term and a plain-language definition.
- If terms are easy to confuse, give one or two alternatives and the practical distinction.
- Treat the glossary as a helpful shared vocabulary, not a closed standard. If no entry fits, say so and offer the closest established term without inventing jargon.
- Keep answers brief. Naming a pattern does not require prescribing its implementation.

Use [the glossary](references/glossary.md) for UI and motion terms. This skill names patterns; investigating how a particular existing effect was implemented is a separate task.

## Examples

Examples use a fictional e-commerce app (catalog, products, cart, and checkout) for consistency. This context is illustrative, not a requirement for projects using the skill.

- **DON'T:** Treat a term as a required implementation:

  ```text
  “This product quick-view is a modal, so it must use a portal and a specific library.”
  ```

- **DO:** Name the pattern, then describe implementation separately:

  ```text
  “The product quick-view is a modal dialog: it temporarily blocks interaction
  with the catalog until dismissed. It can use a native dialog or an accessible
  dialog primitive, depending on the app's needs.”
  ```
