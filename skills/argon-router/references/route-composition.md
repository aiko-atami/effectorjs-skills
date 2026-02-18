# Route Composition

## Purpose

Compose routing behavior without duplicating route definitions.

## `chainRoute`

Use `chainRoute` to gate route opening behind async/sync preconditions.

```ts
import { chainRoute } from '@argon-router/core';
import { createEffect, sample } from 'effector';

const checkAccessFx = createEffect(async () => {
  // throw to reject
});

const protectedPostRoute = chainRoute({
  route: postRoute,
  beforeOpen: checkAccessFx,
});
```

Useful for auth checks, preload checks, or tenant guards.

## `group`

Use `group([routeA, routeB, ...])` to build one virtual route that is opened while any child route is opened.

```ts
import { group } from '@argon-router/core';

const authSectionRoute = group([signInRoute, signUpRoute]);
```

Use it for shared layout state or section-level side effects.

## `createVirtualRoute`

Use virtual routes for derived open/close flows not tied directly to path parsing.

```ts
import { createVirtualRoute } from '@argon-router/core';

const modalRoute = createVirtualRoute<{ id: string }, { id: string }>({
  transformer: (payload) => payload,
});
```

## Composition Order

1. Implement real route graph first.
2. Add `chainRoute` for guarded flows.
3. Add `group` for section state.
4. Add custom virtual routes last.
