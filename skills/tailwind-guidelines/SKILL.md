---
name: tailwind-guidelines
description: Apply Tailwind-first styling across frameworks, including responsive utilities, CSS escape hatches, and cn class composition.
---
# Tailwind-first styling

## Default to Tailwind

- Use Tailwind utilities by default for layout, spacing, sizing, typography, color, borders, states, and responsive styling. Keep classes near the markup when that makes structure and styling easier to read.
- Use CSS when a rule is clearer as CSS, such as complex selectors or relationships, intricate keyframes, special pseudo-element styling, or an effect that is awkward to express with utilities. Prefer framework-scoped CSS for component-specific rules.
- Keep global CSS for global concerns such as Tailwind imports, fonts, theme tokens, resets, and shared base styles. Avoid moving ordinary component styles into separate CSS files without a reason.
- Use inline styles for runtime values such as measured positions or progress. Keep static styling in Tailwind or CSS.
- When a runtime value must affect a CSS-only rule, pass it through a CSS custom property; avoid generating utility names dynamically.

## Responsive styles

- For responsive values known in source code, use Tailwind breakpoint prefixes (`sm:`, `md:`, `lg:`) in markup or class maps. Tailwind breakpoints are mobile-first: unprefixed classes apply by default and prefixed classes apply at that breakpoint and above.
- Do not add a dependency just to express ordinary responsive layout. Use an existing runtime-responsive helper when a component API accepts responsive CSS values at runtime that cannot be represented cleanly as a finite set of Tailwind class choices.
- Avoid constructing Tailwind class names by concatenating fragments. Use complete class strings in markup or class maps so Tailwind can detect them at build time.

## Reuse class styles

When class strings repeat, decide whether the repeated styling represents a named visual choice:

- Use a small class map for a few semantic styles, such as text roles or page variants.
- Use the project's existing `cn` helper for conditional composition and Tailwind conflict resolution (typically `clsx` plus `tailwind-merge`). Do not introduce a second helper or duplicate that setup.
- Keep `cn` for conditional or caller-provided classes, especially where caller classes may override defaults. Do not wrap every static class string in it.
