---
name: nodejs-server-guidelines
description: Apply straightforward Node.js server conventions for lightweight organization, Fastify routes, startup, configuration, and logging.
---

# Node.js server guidelines

Use this skill when creating or changing a Node.js server. First inspect the project's runtime, module system, framework version, dependencies, scripts, and existing patterns. Bring independent technical judgment: do not copy a requested structure or example mechanically. Recommend the simplest approach that meets the real need, explain meaningful trade-offs, and distinguish what is needed now from what can wait.

Use `programming-guidelines` for shared principles on scope, dependencies, and file boundaries.

- For module and folder boundaries, read [architecture.md](references/architecture.md).
- For Fastify-specific routes, plugins, logging, errors, and lifecycle, read [fastify-practices.md](references/fastify-practices.md).
- Preserve existing choices unless there is a clear reason to change them. Avoid dependencies, folders, and layers without a concrete job.

Follow project instructions and scripts. Keep changes focused and do not expand scope with speculative edge cases.
