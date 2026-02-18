# React Web Integration

## Purpose

Render route-aware UI in React using `@argon-router/react`.

## Required Building Blocks

- `RouterProvider` provides router instance in tree.
- `createRouteView` maps route to component (optionally with layout).
- `createRoutesView` renders currently opened view chain.
- `Outlet` renders nested child route views.
- `Link` is the default navigation component.
- `useLink` builds href and open handler for custom interactions.

## Setup Pattern

```tsx
import {
  RouterProvider,
  createRouteView,
  createRoutesView,
} from '@argon-router/react';

const HomeView = createRouteView({ route: homeRoute, view: HomePage });
const PostView = createRouteView({ route: postRoute, view: PostPage });

const RoutesView = createRoutesView({ routes: [HomeView, PostView] });

export function App() {
  return (
    <RouterProvider router={router}>
      <RoutesView />
    </RouterProvider>
  );
}
```

## Link Pattern

```tsx
import { Link } from '@argon-router/react';

<Link to={postRoute} params={{ id: 10 }} query={{ tab: 'comments' }}>
  Open post
</Link>;
```

## Custom Link Pattern (`useLink`)

```tsx
import { useLink } from '@argon-router/react';

function PostCard({ id }: { id: number }) {
  const { path, onOpen } = useLink(postRoute, { id });
  return (
    <a
      href={path}
      onClick={(e) => {
        e.preventDefault();
        onOpen({ params: { id } });
      }}
    >
      Post {id}
    </a>
  );
}
```

## Fallback Pattern (`otherwise`)

```tsx
const RoutesView = createRoutesView({
  routes: [HomeView, PostView],
  otherwise: NotFoundPage,
});
```

## Nested Views Pattern

Parent view includes `Outlet` where child route view should render.

```tsx
function ProfileLayout() {
  return (
    <section>
      <h1>Profile</h1>
      <Outlet />
    </section>
  );
}
```

## Notes

- `useLink` throws if route is not present in router known routes.
- Keep one root `RouterProvider` per router tree.
- `Link` preserves browser default behavior for modifier keys and non-`_self` target.
