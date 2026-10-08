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
- Treat simplicity, reuse, and abstraction as tradeoffs, not universal rules. Consider the project's expected lifespan, scope, timeline, business value, team and contribution model, expected flexibility, roadmap uncertainty, and likely integration costs. Minimal isolated features can make later integration and consistency expensive; abstractions bring upfront design and maintenance costs. Choose based on the likely costs over this project's life.
- For a fixed-term deliverable under a short deadline, favor reliable delivery and straightforward retirement over hypothetical long-term scale—not rushed, tangled code. Keep the implementation readable, coherent, and maintainable for its expected lifetime. For a long-lived product with recurring features or contributors, invest in boundaries when they reduce ongoing change and integration costs. A short lifespan does not excuse correctness, security, or operational requirements.
- Use the rule of three as a prompt to reassess repeated logic, not a fixed abstraction threshold. A known shared invariant or integration need can justify a boundary sooner, while similar-looking code may still need to remain separate when its behavior differs.
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

- **DON'T:** Keep each feature's rules buried in its route/storage code, then make checkout reach into those internals and duplicate the rules:

  ```ts
  app.post('/checkout', async (request, reply) => {
    const cart = await db.carts.findById(request.body.cartId);
    const lines = await Promise.all(cart.items.map(async (item) => {
      const product = await db.products.findById(item.productId);
      if (!product || product.stock < item.quantity) {
        throw new Error('Product unavailable');
      }
      return { productId: product.id, quantity: item.quantity, price: product.price };
    }));

    const order = await db.orders.create({ customerId: request.user.id, lines });
    await db.carts.clear(cart.id);
    return reply.code(201).send(order);
  });
  ```

- **DO:** When checkout is a real requirement, introduce a workflow boundary that coordinates the existing capabilities through their contracts:

  ```ts
  app.post('/checkout', async (request, reply) => {
    const order = await checkout.placeOrder({
      customerId: request.user.id,
      cartId: request.body.cartId
    });

    return reply.code(201).send(order);
  });

  async function placeOrder(input: PlaceOrderInput) {
    const quote = await cart.quote(input.cartId);
    const reservation = await inventory.reserve(quote.items);
    return orders.create({ customerId: input.customerId, quote, reservation });
  }
  ```

  `placeOrder` earns its boundary by owning a real cross-feature workflow; it is not a pass-through wrapper. Handle transaction, reservation, and retry semantics according to the application's actual guarantees. Do not create this layer before the integration need is real.
