# Codex skills

This repository contains the portable Codex skills maintained here. Keep machine-specific Codex settings, credentials, caches, plugins, and session data in the local Codex home; they do not belong in this repository.

## Skills in this repository

- `git-commit-message`: write commit messages in the project's established style.
- `interface-motion`: plan and implement purposeful, performant interface motion.
- `interface-vocabulary`: name UI components, patterns, layout concepts, and motion.
- `nodejs-server-guidelines`: keep lightweight Node.js and Fastify servers clear and proportionate.
- `programming-guidelines`: apply simple, maintainable programming principles across languages and frameworks.
- `svelte-guidelines`: apply Svelte and SvelteKit conventions with simple component boundaries.
- `tailwind-guidelines`: use Tailwind first, with responsive utilities and the shared `cn` helper.
- `typescript-guidelines`: keep TypeScript clear, accurately typed, and proportionate to the problem.

## Install

Install the skills globally for Codex with the Vercel Skills CLI:

```sh
npx skills add 0xposed/dotfiles --global --agent codex --skill '*' --yes
```

The Skills CLI accepts GitHub repositories as a source and supports global installation for Codex. To pull updates for installed skills, run `npx skills update`.
