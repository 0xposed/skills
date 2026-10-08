---
name: nodejs-server-guidelines
description: Apply lightweight Node.js server organization and Fastify practices when working on a Fastify server.
---

# Node.js server guidelines

Use this skill when creating or changing a Fastify server, or when a lightweight Node.js server task clearly benefits from its general organization guidance. For another server framework, follow that framework's conventions and use only the framework-agnostic guidance here; do not apply Fastify-specific route, plugin, or lifecycle rules. First inspect the project's runtime, module system, framework version, dependencies, scripts, and existing patterns. Bring independent technical judgment: do not copy a requested structure or example mechanically. Recommend the simplest approach that meets the real need, explain meaningful trade-offs, and distinguish what is needed now from what can wait.

Use `programming-guidelines` for shared principles on scope, dependencies, and file boundaries.

- For module and folder boundaries, read [architecture.md](references/architecture.md).
- For Fastify-specific routes, plugins, logging, errors, and lifecycle, read [fastify-practices.md](references/fastify-practices.md).
- Preserve existing choices unless there is a clear reason to change them. Avoid dependencies, folders, and layers without a concrete job.

Follow project instructions and scripts. Keep changes focused and do not expand scope with speculative edge cases.

## Examples

Examples use a fictional e-commerce app (catalog, products, cart, and checkout) for consistency. This context is illustrative, not a requirement for projects using the skill.

- **DON'T:** Add a service layer that only forwards one call:

  ```js
  app.get('/products/:id', async (request) => productService.getById(request.params.id));
  ```

- **DO:** Keep a genuinely simple handler direct; extract logic once it owns real behavior:

  ```js
  app.get('/products/:id', async (request, reply) => {
    const product = await catalog.getAvailableProduct(request.params.id);
    if (!product) return reply.code(404).send({ error: 'Product not found' });
    return product;
  });
  ```

  Here, `getAvailableProduct` owns catalog availability rules rather than merely forwarding a database call.
