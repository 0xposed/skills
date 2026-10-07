---
name: svelte-guidelines
description: Apply Svelte and SvelteKit conventions for component logic, server-safe state, component boundaries, and lightweight file organization.
---

# Svelte and SvelteKit guidelines

Use these conventions when writing or reviewing Svelte and SvelteKit code. First check the project's Svelte and SvelteKit versions, dependencies, scripts, and nearby patterns. Preserve the project's established syntax and tooling; avoid adding dependencies without a clear need.

Use `programming-guidelines` for shared principles on scope, dependencies, and file boundaries.

- For Svelte 5 component logic, props, events, data loading, and SSR-safe state, read [core-practices.md](references/core-practices.md).
- For file organization and component boundaries, read [component-structure.md](references/component-structure.md).
- For framework-agnostic Tailwind styling and class reuse, use the `tailwind-guidelines` skill.
- Prefer current Svelte syntax for new code, but do not convert existing components just to modernize them.

Keep changes localized and preserve existing behavior. Run project checks when the user requests verification.
