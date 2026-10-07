# Svelte component and file organization

## Keep files focused

- Keep route files focused on route data and page composition. Extract behavior or UI when it is reused, independently meaningful, or too complex to follow inline.
- Organize shared code by domain or technical responsibility. Avoid broad catch-all folders and do not create component files solely to shorten markup.
- Keep page-specific components near their route. Put genuinely shared UI under the project's established shared UI location.
- Extract shared state or complex reactive logic to a focused `*.svelte.ts` module when that makes its lifecycle and callers easier to understand. See [core-practices.md](core-practices.md) for SSR safety and state rules.

## Choose the right reuse boundary

- Keep one-off markup inline. Repeated styling alone is not a reason to extract a Svelte component; share class recipes or class maps instead, following the `tailwind-guidelines` skill.
- Make a Svelte component when meaningful markup, behavior, accessibility semantics, state, lifecycle, or a distinct public contract benefits from its own name and props.
- Do not extract a component only to shorten a template. Also avoid keeping a component inline when that makes its behavior or responsibility hard to understand.