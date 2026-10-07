# Svelte and SvelteKit core practices

## Use reactivity for reactive values

- In Svelte 5 runes mode, use `$state` only for values that should update the template or other reactive computations. Use ordinary `const` and `let` for values that do not need reactivity.
- Use `$derived` for pure values computed from state or props. Treat props as changeable; derive values that should stay in sync with them.
- Treat `$effect` as an escape hatch for synchronizing with external systems or imperative browser APIs. Do not use it to copy state into other state when `$derived` or an event handler expresses the relationship. Return cleanup for listeners, subscriptions, timers, and external resources.
- Keep code compatible with the project's mode and version. Prefer runes for new Svelte 5 reactive code, while leaving legacy syntax in place until migration is in scope.

## Use Svelte's component API directly

- In TypeScript components, define a `Props` type or interface and read props with `$props()`. In JavaScript components, use the project's existing prop conventions.
- Use `$bindable()` only when the component intentionally offers a two-way binding contract.
- In new Svelte 5 code, use event attributes such as `onclick`. Expose component events as callback props when that keeps the component API clear. Follow existing legacy event syntax when editing a legacy component; do not migrate it incidentally.
- Use snippets and `{@render ...}` for caller-provided markup when they make a component API clearer. Use a component for markup with an independent responsibility, reusable behavior, state, or public contract. Preserve an established slot-based API unless migration is requested.
- Use `<svelte:window>` and `<svelte:document>` for declarative global event listeners when appropriate. Clean up imperative subscriptions and browser resources the component creates.

## Put work in the right SvelteKit layer

- Use `load` for route data that should participate in server rendering and navigation. Reserve `onMount` or browser effects for client-only work; do not fetch in `onMount` when the page needs the data for SSR.
- Use form actions for HTML form mutations when their progressive-enhancement behavior fits. Use endpoints or other APIs when the operation is a non-form API or has a separate client contract; do not force every mutation into one mechanism.
- Avoid mutating shared module state in `load` functions. Data fetching is normal; keep request-specific state within the request and return route data through the load result.

## Keep shared state safe under SSR

- Never keep request-specific user or page state in a mutable module singleton in a SvelteKit server process; concurrent requests can share it.
- Use page/layout data for route state, or context for state scoped to a component subtree. A `*.svelte.ts` module or module-level instance can suit client-only external integrations or intentionally shared state when it cannot leak request-specific data.
- When extracting stateful logic into `*.svelte.ts`, keep its job narrow and make external resource start/stop behavior explicit. Follow the project's existing lifecycle pattern.

## Handle collections by identity

- Use stable keys for lists whose items can change order, be inserted or removed, or carry per-item state. Prefer a stable item ID; avoid the array index when identity can change.
- Do not add a `{#key}` block just to force reactive recalculation. Prefer a derived value or an explicit keyed identity boundary when remounting is actually intended.