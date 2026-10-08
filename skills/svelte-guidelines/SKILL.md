---
name: svelte-guidelines
description: Apply Svelte and SvelteKit conventions for component logic, server-safe state, component boundaries, and lightweight file organization.
---

# Svelte and SvelteKit guidelines

Use these conventions when writing or reviewing Svelte and SvelteKit code. First check the project's Svelte and SvelteKit versions, dependencies, scripts, and nearby patterns. Preserve the project's established syntax and tooling; avoid adding dependencies without a clear need.

- Follow the active repository's established structure. If the user provides a separate project as an organizational reference, inspect it only when available and in scope; adapt useful structural patterns without importing its project-specific conventions as universal rules.

Use `programming-guidelines` for shared principles on scope, dependencies, and file boundaries.

- For Svelte 5 component logic, props, events, data loading, and SSR-safe state, read [core-practices.md](references/core-practices.md).
- For file organization and component boundaries, read [component-structure.md](references/component-structure.md).
- When meaningful Svelte UI markup is repeated—including controls with the same visual and behavioral contract—extract it into a focused component with typed props/callbacks. Keep semantically different controls separate even if they share a small class recipe; avoid wrapper components that only rename a native element.
- For framework-agnostic Tailwind styling and class reuse, use the `tailwind-guidelines` skill.
- Prefer current Svelte syntax for new code, but do not convert existing components just to modernize them.

Keep changes localized and preserve existing behavior. Run project checks when the user requests verification.

## Examples

Examples use a fictional e-commerce app (catalog, products, cart, and checkout) for consistency. This context is illustrative, not a requirement for projects using the skill.

- **DON'T:** Nest a component through folders that add no useful responsibility boundary:

  ```text
  src/lib/shop/catalog/products/cards/ProductCard.svelte
  ```

- **DO:** Follow the repository's existing domain structure:

  ```text
  src/lib/catalog/ProductCard.svelte
  src/lib/catalog/index.ts
  ```

  These e-commerce paths are illustrative, not a required layout. Inspect the project and use folders where they clarify ownership or match established conventions.
