---
name: programming-guidelines
description: Apply simple, maintainable programming principles when creating, changing, or reviewing code in any language, runtime, or framework. Use for general implementation decisions; use stack-specific skills for language and framework details.
---

# Programming Guidelines

Build the smallest clear solution that meets the current requirements. Prefer code that is straightforward to read, change, and extend when a real need appears.

## Understand the project first

- Check the relevant files, language/runtime versions, dependencies, scripts, and nearby patterns before choosing an approach.
- Preserve existing behavior and useful project conventions. Do not modernize, restructure, or replace working patterns without a concrete reason.
- Follow repository instructions and use its existing tools where they fit.
- Apply engineering judgment to proposed solutions: check that they fit the project's constraints and solve the actual problem. Call out concrete risks, contradictions, or unnecessary complexity, and recommend a simpler or safer option when appropriate instead of adopting a suggestion uncritically.

## Keep complexity proportionate

- Implement what the task needs now. Do not add speculative options, defensive branches, abstractions, folders, or layers for hypothetical future requirements.
- Add a dependency only when it materially solves the problem better than the existing platform or project tools.
- Keep functions, modules, and files focused. Split code when its size or mixed responsibilities make it hard to understand or change; keep small related code together when splitting it would only add navigation.
- This applies to pages, components, classes, scripts, and modules. Extract a focused responsibility when that gives it a clear purpose and makes the main flow easier to follow. Avoid splitting mechanically by line count or by one-file-per-function rules.
- When meaningful UI or control markup is repeated, extract it into a named reusable component and pass the changing content, state, or actions as props. For repeated non-UI logic, use an appropriate function or module instead. Do not create components for trivial one-line markup or merely to hide a repeated class string; use a shared class recipe for styling-only reuse.
- Name files and folders for the responsibility they own. Add a folder when it creates a useful boundary or makes related code easier to find, not just to impose a standard layout.
- When a folder contains modules intended for use outside that folder, expose them through an `index.ts` in the folder and keep its exports current as modules are added, renamed, or removed.

## Make changes easy to reason about

- Keep side effects and important boundaries visible. Validate data at trust boundaries and handle errors where the code can make a useful decision.
- Prefer direct control flow and clear names over clever or compressed code.
- Make the smallest coherent change that solves the task. Explain meaningful trade-offs when more than one approach is reasonable.
- Verify with the narrowest relevant project check when verification is needed; state what was and was not checked.

Use language-, framework-, and domain-specific conventions where they improve correctness or clarity. These general principles should guide the approach, not override a project's established requirements.

## Examples

Examples use a fictional e-commerce app (catalog, products, cart, and checkout) for consistency. This context is illustrative, not a requirement for projects using the skill.

- **DON'T:** Add a wrapper that only forwards arguments:

  ```ts
  function getCartTotal(items: CartItem[]) {
    return calculateCartTotal(items);
  }
  ```

- **DO:** Call the focused implementation directly, or extract a module when it owns a real responsibility:

  ```ts
  const total = calculateCartTotal(cartItems);
  ```
