# Checklist

## Routing Graph

- All routes used in UI are registered in `createRouter({ routes })`.
- `createRouterControls` is used and initialized with history via `setHistory`.
- Base path behavior is verified when `base` is configured.

## React Wiring

- App root is wrapped with `RouterProvider`.
- Every screen is created through `createRouteView`.
- `createRoutesView` receives the full route view list.
- Parent views that own nested routes include `Outlet`.

## Navigation

- Route navigation uses `route.open(...)` or `useLink`.
- `useLink` targets exist in router known routes.
- Query changes use `trackQuery.enter/exit`, not manual string concatenation.

## Paths and Params

- Path syntax matches supported DSL rules.
- Params types match declared path token types.
- `+`, `*`, `?`, generic, and range usage is intentional and tested.

## Composition

- `chainRoute` is used only after base route opens work.
- `group` reflects section-level open state correctly.
- Virtual routes do not duplicate real path ownership.
