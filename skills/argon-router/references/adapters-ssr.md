# Adapters and SSR

## Purpose

Choose the right history adapter, wire router/controls safely, and initialize navigation in scoped environments.

## Adapter Selection

- `historyAdapter(history)` for primary pathname routing (`/users/1`).
- `queryAdapter(history)` for secondary flows encoded in query (`/app?modal=/login`).
- Custom adapter only for non-standard platforms or custom history engines.

## Typical Wiring

```ts
import { createBrowserHistory } from 'history';
import { createRouter, historyAdapter } from '@argon-router/core';

const router = createRouter({ routes: [homeRoute, profileRoute] });
router.setHistory(historyAdapter(createBrowserHistory()));
```

Do not pass raw history (`createBrowserHistory()`) directly into `setHistory`.

## Scoped Initialization (SSR/Tests)

```ts
import { allSettled, fork } from 'effector';
import { createMemoryHistory } from 'history';
import { historyAdapter } from '@argon-router/core';

const scope = fork();

await allSettled(router.setHistory, {
  scope,
  params: historyAdapter(createMemoryHistory({ initialEntries: ['/profile/10'] })),
});
```

## `createRouterControls` Notes

- `createRouter` already exposes controls (`navigate`, `back`, `forward`, `$path`, `$query`).
- Use standalone `createRouterControls` for advanced custom router composition.
- `setHistory` is mandatory before navigation; otherwise navigation units fail.

## Best Practices

- Keep a single adapter instance per router lifecycle.
- Use `replace: true` for frequent filter/query updates to avoid noisy history stacks.
- Prefer router/route API over direct history calls from feature code.
