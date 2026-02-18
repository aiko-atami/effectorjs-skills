# Core Routing

## Purpose

Build the minimal routing graph: routes, controls, router, navigation.

## Main Units

- `createRoute` from `@argon-router/core` creates path or pathless routes.
- `createRouterControls` creates `$path`, `$query`, `navigate`, `setHistory`, `back`, `forward`.
- `createRouter` binds controls to routes and opens/closes routes by URL.

## Minimal Setup Sequence

1. Declare route units.
2. Create controls.
3. Create router with route list and optional `base`.
4. Provide history adapter using `router.setHistory(...)`.

## Baseline Example

```ts
import { createRoute, createRouter, createRouterControls } from '@argon-router/core';

export const homeRoute = createRoute({ path: '/' });
export const postRoute = createRoute({ path: '/posts/:id<number>' });

export const controls = createRouterControls();

export const router = createRouter({
  routes: [homeRoute, postRoute],
  controls,
});

// At app bootstrap: router.setHistory(browserHistoryAdapter)
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
