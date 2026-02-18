# Lazy Views and Layouts

## Purpose

Structure React route views for code-splitting and shared layout composition.

## `createLazyRouteView`

Use for route-level code splitting:

```tsx
import { createLazyRouteView } from '@argon-router/react';

const ProfileView = createLazyRouteView({
  route: profileRoute,
  view: () => import('./ProfilePage'),
  fallback: () => <div>Loading...</div>,
});
```

Notes:
- Lazy module must default-export React component.
- `fallback` is optional; defaults to empty fragment.
- Works with `children` and `layout` similarly to `createRouteView`.

## `withLayout`

Use to apply one layout to multiple route views:

```tsx
import { withLayout, createRouteView, createRoutesView } from '@argon-router/react';

const RoutesView = createRoutesView({
  routes: [
    ...withLayout(MainLayout, [
      createRouteView({ route: homeRoute, view: HomePage }),
      createRouteView({ route: aboutRoute, view: AboutPage }),
    ]),
  ],
});
```

## When to Use

- `layout` option in `createRouteView`: one-off layout.
- `withLayout`: repeated shared layout across route group(s).
- `createLazyRouteView`: heavy screens or low-frequency routes.

## Guardrails

- Stabilize route graph first, then apply lazy/layout optimizations.
- Keep lazy fallback minimal and deterministic.
- Avoid deep nested layout wrappers unless there is a clear UI boundary.
