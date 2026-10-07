# Fastify practices

Use the Fastify version already installed and follow its matching documentation. Most application code can stay direct and familiar. Pay attention to plugin encapsulation where it affects visibility of routes, hooks, or decorators; do not wrap every small module in a plugin.

## Routes and hooks

- Keep route registration direct and readable. Group routes by domain when that improves navigation; don't build a generic route registry for a handful of endpoints.
- Async route handlers and hooks should stay straightforward. Use hooks for behavior that belongs to a Fastify lifecycle stage and scope them to the routes that need them.
- Put request validation and response schemas on routes when they provide a useful contract and serialization. Reuse the project's existing schema approach; don't add another dependency without need.
- Keep handlers focused on HTTP input/output and simple orchestration. Extract business logic when it is complex or reused, and keep that code independent of Fastify where practical.
- Register shared plugins before their consumers. Respect encapsulation; use `fastify-plugin` only when a capability deliberately needs to cross a scope.

## Logging and errors

- Prefer Fastify's built-in Pino logger over a custom logger class when it meets the server's needs. Configure it at app creation if logging is needed; use `request.log` for request context and `app.log` for process-level events.
- Log useful structured context and pass errors as error objects. Avoid logging the same request or error at multiple layers.
- Fastify's default error handler may include an error's message in the response. Use it only when that output is appropriate for the application; otherwise add a small handler that returns safe public errors for unexpected failures while logging the original error server-side.
- Keep expected client errors simple to recognize. Add custom error types only when they clarify real application behavior.

## Startup and shutdown

- Keep startup easy to follow. Separate app creation from listening when that helps reuse or testing; otherwise avoid ceremony.
- Await startup and surface bind or plugin initialization failures. Log successful startup through the app logger.
- Close the Fastify instance and owned resources on shutdown when the server has resources that need cleanup. Put process signal handling at the process boundary; avoid adding a shutdown framework to a server that owns nothing beyond Fastify.
- Use Fastify lifecycle hooks such as `onClose` for resources whose lifetime belongs to a plugin.

## References

- [Fastify plugins](https://fastify.dev/docs/latest/Reference/Plugins/)
- [Fastify encapsulation](https://fastify.dev/docs/latest/Reference/Encapsulation/)
- [Fastify logging](https://fastify.dev/docs/latest/Reference/Logging/)
- [Fastify errors](https://fastify.dev/docs/latest/Reference/Errors/)
- [Fastify server](https://fastify.dev/docs/latest/Reference/Server/)
- [Node.js process signals](https://nodejs.org/api/process.html#signal-events)