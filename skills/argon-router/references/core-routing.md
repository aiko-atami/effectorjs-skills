# Core Routing

## Purpose

Build the minimal routing graph: routes, controls, router, navigation.

## Main Units

- `createRoute` from `@argon-router/core` creates path or pathless routes.
- `createRouterControls` creates `$path`, `$query`, `$history`, `$locationState`, `navigate`, `setHistory`, `back`, `forward`, `locationUpdated`, `trackQuery`.
- `createRouter` binds controls to routes and opens/closes routes by URL.

## Router Input Route Types

`createRouter({ routes })` accepts:
- path routes: `createRoute({ path: '/path' })`
- pathless route mapping: `{ path: '/path', route: somePathlessRoute }`
- nested routers: `anotherRouter`

## Minimal Setup Sequence

1. Declare route units.
2. Create controls.
3. Create router with route list and optional `base`.
4. Provide history adapter using `router.setHistory(...)`.

## Baseline Example

```ts
import {
  createRoute,
  createRouter,
  createRouterControls,
  historyAdapter,
} from '@argon-router/core';
import { createBrowserHistory } from 'history';

export const homeRoute = createRoute({ path: '/' });
export const postRoute = createRoute({ path: '/posts/:id<number>' });
export const modalRoute = createRoute<{ id: string }>();

export const controls = createRouterControls();

export const router = createRouter({
  routes: [
    homeRoute,
    postRoute,
    { path: '/modal/:id', route: modalRoute },
  ],
  controls,
});

router.setHistory(historyAdapter(createBrowserHistory()));
```

## Parent/Child Route Pattern

```ts
const profileRoute = createRoute({ path: '/profile/:id<number>' });
const profilePostsRoute = createRoute({
  path: '/posts',
  parent: profileRoute,
});
```

Opening `profilePostsRoute` opens parent route chain and keeps params synchronized.

## Navigation Patterns

- Route-centric navigation: `route.open({ params, query })`.
- Router-centric navigation: `router.navigate({ path, query, replace })`.

Prefer route-centric navigation from feature logic and router-centric navigation for cross-cutting redirects.

## Notes

- Router matches URL to routes via compiled path parsers.
- Route open flow supports `beforeOpen` effects for preconditions.
- `$isPending` comes from route open effect pending state.
- Dynamic extension is possible with `router.registerRoute(...)`.
- `router.ownRoutes` contains routes owned by this router only.
- Use `router.knownRoutes` to reason about route presence (for example with `useLink` constraints).
