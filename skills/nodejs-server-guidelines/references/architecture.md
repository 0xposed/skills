# Server architecture and organization

## Guiding principle

Start with the smallest structure that keeps the server understandable and correct. Keep related code together when that makes it easier to follow. Add a file, folder, abstraction, or defensive path when it solves a real problem: the code is difficult to scan, responsibilities change independently, or a boundary has an actual lifecycle or reuse need. Avoid creating many places to look for a small change.

## Start with the actual server

A very small server may be one file:

```text
src/
  server.ts
```

That file can create the app, register a few routes, and start listening. Split it only when setup, routes, or lifecycle become difficult to follow, or when app construction needs to be reused independently from process startup.

A modest server might grow to:

```text
src/
  server.ts
  config.ts
  routes/
    health.ts
    accounts.ts
```

- `server.ts` composes the application and starts it. If a separate app factory makes tests, reuse, or startup clearer, extract it; do not make `app.ts` and `server.ts` mandatory.
- `config.ts` reads and validates runtime settings. Split it into a `config/` folder only when distinct groups of settings make that easier to navigate.
- `routes/` contains HTTP endpoint definitions and their request/response handling. Keep a few simple routes together if a folder and separate files add no clarity.

## Use names that match the responsibility

Folder names are conventions, not architecture by themselves. Explain the job a folder does before adding it, and do not put unrelated types of code together just because one folder name is familiar.

- `services/` is an overloaded name. In many applications it means operations or business capabilities used by routes or other callers. It is not a mandatory layer, and a one-line wrapper around each route is not a useful service.
- For HTTP, UDP, and WebSocket server implementations, `transports/` or `server/` describes the protocol/runtime role more clearly than `services/`. In a new project, prefer the more precise name. If an existing codebase already uses `services/` consistently for runtime capabilities, the name is understandable and does not need to be changed just for terminology.
- A bridge that coordinates transports is application/runtime orchestration. Keep a single bridge beside the server composition if that is easiest to find; group it only if several related modules justify a folder.
- Fastify plugins are a registration mechanism, not a required `plugins/` directory. Keep a few registrations in app setup; create a folder only when several plugin modules are easier to manage separately.

For example, a server with multiple protocols might grow like this:

```text
src/
  server.ts
  routes/
    health.ts
  transports/
    http.ts
    websocket.ts
    udp.ts
  bridge.ts
```

Here, `transports/` owns the protocol-facing server components, while `bridge.ts` connects them. This layout is only useful when the application actually serves multiple protocols. For an ordinary HTTP API, start with `server.ts` and add route or service modules as the code needs them.

## When to separate application operations

If routes or other entry points share a meaningful operation, or a handler becomes hard to understand because it contains business rules, extract that operation into a module. A `services/` folder can then hold those operations, named around their domain or responsibility. In a new project, keep business operations and transport/runtime components in separate folders when both exist. If only one category exists, create only that folder.

Do not add repository layers, custom error hierarchies, logger wrappers, dependency containers, or folders for anticipated future scale. Add them when a current requirement makes the simpler structure hard to maintain.

## Framework changes

When changing frameworks, preserve useful application boundaries but use the new framework's APIs where they materially help. Do not copy framework-specific wrappers mechanically or invent a new architecture just because the framework changed.