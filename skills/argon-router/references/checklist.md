# Checklist

## Routing Graph

- All routes used in UI are registered in `createRouter({ routes })`.
- Pathless routes are registered via `{ path, route }`.
- `createRouterControls` is used and initialized with history via `setHistory`.
- Base path behavior is verified when `base` is configured.

## React Wiring

- App root is wrapped with `RouterProvider`.
- Every screen is created through `createRouteView`.
- `createRoutesView` receives the full route view list.
- `createRoutesView({ otherwise })` is configured when no-match fallback is required.
- Parent views that own nested routes include `Outlet`.
- `Link` is used for standard navigation; `useLink` only for custom interactions.
- `useRouter`/`useRouterContext` choice is explicit (bound values vs raw stores).
- `useIsOpened` is used only for UI state.

## Navigation

- Route navigation uses `route.open(...)` or `useLink`.
- `useLink` targets exist in router known routes.
- Query changes use `trackQuery.enter/exit`, not manual string concatenation.
- `trackQuery` variant is selected intentionally: `router.trackQuery` (with optional `forRoutes`) vs `controls.trackQuery` (without `forRoutes`).
- `replace: true` is used for high-frequency query/filter writes.

## Paths and Params

- Path syntax matches supported DSL rules.
- Params types match declared path token types.
- `+`, `*`, `?`, generic, and range usage is intentional and tested.

## Composition

- `chainRoute` is used only after base route opens work.
- `group` reflects section-level open state correctly.
- Virtual routes do not duplicate real path ownership.

## Adapters and SSR

- Router is initialized via `setHistory` before route activity is expected.
- `setHistory` receives adapter instances (`historyAdapter(...)` / `queryAdapter(...)`), not raw history.
- Adapter choice is intentional: `historyAdapter` for pathname, `queryAdapter` for query-based subnavigation.
- SSR/tests initialize history in scope via `allSettled(..., { scope, params })`.

## Lazy and Layout

- `createLazyRouteView` is used for heavy or infrequent screens.
- Lazy modules export default component and fallback UI is defined when needed.
- Shared layout is applied with `withLayout` when multiple route views reuse one shell.

## React Native

- Navigation is driven by Argon route events (`route.open`), not `navigation.navigate`.
- Navigator integration (`createArgonStackNavigator`/`createArgonBottomTabsNavigator`) receives full route view list.
- `RouterProvider` wraps app tree with `NavigationContainer` for shared router context.
