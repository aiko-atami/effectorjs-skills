# Query Tracking

## Purpose

Map URL query parameters to typed feature flows.

## API Shape

`router.trackQuery({ parameters, forRoutes?, check? })` returns:
- `enter(payload)` to write query params.
- `entered(payload)` event when URL query matches schema.
- `exit({ ignoreParams? })` to clear query params.
- `exited` event when query leaves valid state.

`controls.trackQuery({ parameters, check? })` is also available (without `forRoutes`).

## Basic Pattern

```ts
import { z } from 'zod';

const postsFilterQuery = router.trackQuery({
  parameters: z.object({
    page: z.coerce.number().optional(),
    q: z.string().optional(),
  }),
  check: filtersApplyRequested,
  forRoutes: [postRoute],
});
```

## Wiring Pattern

```ts
import { sample } from 'effector';

sample({
  clock: filterChanged,
  fn: ({ page, q }) => ({ page, q }),
  target: postsFilterQuery.enter,
});

sample({
  clock: clearFilterClicked,
  target: postsFilterQuery.exit,
});
```

## Controls Pattern

```ts
const controlsFilters = controls.trackQuery({
  parameters: z.object({
    tab: z.enum(['overview', 'comments']).optional(),
  }),
});
```

## Best Practices

- Keep schemas minimal and close to feature boundaries.
- Use `forRoutes` to prevent global query reactions.
- Use `exit({ ignoreParams })` when preserving shared params.
