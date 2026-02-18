---
name: argon-router
description: Integrate and use argon-router in React web applications with Effector. Use when tasks involve creating routes and routers, wiring RouterControls/history, composing routes with chainRoute/group/createVirtualRoute, rendering views with RouterProvider/createRoutesView/Outlet, building links with useLink, and managing URL query state with trackQuery and @argon-router/paths.
---

# Argon Router

Use this skill to implement argon-router in React web apps with predictable Effector dataflow and typed paths.

## Workflow

1. Classify the task:
- `setup`: create route map, router, and controls.
- `ui`: connect router to React views, links, and outlet.
- `query`: track URL query state and sync enter/exit flows.
- `composition`: build derived/protected/virtual routes.
- `debug`: validate path/router wiring and route lifecycle.

2. Load only required references:
- Always start with `references/core-routing.md`.
- Add `references/react-web.md` for any React integration task.
- Add `references/paths-dsl.md` when working with route path syntax or parsing/building URLs.
- Add `references/query-tracking.md` when query params or filters are involved.
- Add `references/route-composition.md` when using auth guards, grouped states, or virtual routes.
- Add `references/examples.md` for copyable happy-path scaffolds.
- End with `references/checklist.md` before final output.

3. Build in this order:
- Define route units with explicit paths and params.
- Create router controls and initialize history adapter.
- Create router with known routes and optional base.
- Create React route views and wire `RouterProvider` + `createRoutesView`.
- Add link/navigation actions via route `open` and `useLink`.
- Add query trackers only when URL query behavior is required.
- Add route composition (`chainRoute`, `group`) after baseline routing works.

4. Produce output contract:
- Router topology: routes, router, controls, view mapping.
- Wiring snippets for navigation and query flows.
- Notes for params/path DSL used by each route.
- Validation checklist with expected lifecycle behavior.

## Defaults

- Target React web only (`@argon-router/react`).
- Use happy-path integration patterns.
- Keep route graph explicit and small before adding composition.
- Prefer declarative Effector links (`sample`, `attach`) over imperative glue code.

## Guardrails

- Initialize controls with `setHistory` before expecting route activation from URL changes.
- Ensure every route used by `useLink` is registered in `createRouter({ routes })`.
- Keep route paths deterministic; avoid ambiguous wildcard-heavy patterns unless required.
- Model query state through `trackQuery`, not ad-hoc parsing in components.
- Keep view rendering centralized in `createRoutesView` and `Outlet` composition.
