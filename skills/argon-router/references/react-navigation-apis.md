# React Navigation APIs

## Purpose

Use React bindings for links, router access, and route-activity UI state.

## `Link` vs `useLink`

- Prefer `Link` for standard anchor-like navigation.
- Use `useLink` only for custom interaction surfaces (buttons, cards, touch targets).
- `useLink` expects route to be registered in router known routes.

## `Link` Pattern

```tsx
import { Link } from '@argon-router/react';

<Link to={postRoute} params={{ id: 10 }} query={{ tab: 'comments' }}>
  Open post
</Link>;
```

## `useLink` Pattern

```tsx
import { useLink } from '@argon-router/react';

function PostCard({ id }: { id: number }) {
  const { path, onOpen } = useLink(postRoute, { id });
  return (
    <a href={path} onClick={(e) => { e.preventDefault(); onOpen({ params: { id } }); }}>
      Post {id}
    </a>
  );
}
```

## Router Hooks

- `useRouter()` returns router with store values already bound (good default).
- `useRouterContext()` returns raw router stores (use with `useUnit` for selective binding).
- `useIsOpened(routeOrRouter)` for active styles/visibility logic.
- `useOpenedViews(routeViews)` for custom renderers (stack/layer/animation).

## Guardrails

- All router hooks require `RouterProvider` above the component tree.
- Use `useIsOpened` for UI state, not for business-critical branching side effects.
- Keep custom renderers based on `useOpenedViews` declarative and side-effect free.
