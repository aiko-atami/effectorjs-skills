# Examples

## Example 1: Basic Router

```ts
import { createRoute, createRouter, createRouterControls } from '@argon-router/core';

export const homeRoute = createRoute({ path: '/' });
export const aboutRoute = createRoute({ path: '/about' });

const controls = createRouterControls();

export const router = createRouter({
  routes: [homeRoute, aboutRoute],
  controls,
});
```

## Example 2: Pathless Route Mapping + Dynamic Registration

```ts
const dialogRoute = createRoute<{ id: string }>();

const router = createRouter({
  routes: [
    homeRoute,
    { path: '/dialog/:id', route: dialogRoute },
  ],
});

router.registerRoute(createRoute({ path: '/settings' }));
```

## Example 3: Params + Link

```tsx
const postRoute = createRoute({ path: '/posts/:id<number>' });

function Card({ id }: { id: number }) {
  const { path, onOpen } = useLink(postRoute, { id });
  return <a href={path} onClick={(e) => { e.preventDefault(); onOpen({ params: { id } }); }}>Post {id}</a>;
}
```

## Example 4: Nested Route with Outlet

```tsx
const profileRoute = createRoute({ path: '/profile/:id<number>' });
const profilePostsRoute = createRoute({ path: '/posts', parent: profileRoute });

function ProfilePage() {
  return (
    <div>
      <h1>Profile</h1>
      <Outlet />
    </div>
  );
}
```

## Example 5: Routes View with Fallback

```tsx
const RoutesView = createRoutesView({
  routes: [HomeView, ProfileView],
  otherwise: NotFoundView,
});
```

## Example 6: Query Filters

```ts
const filters = router.trackQuery({
  parameters: z.object({
    q: z.string().optional(),
    page: z.coerce.number().optional(),
  }),
  forRoutes: [postRoute],
});

sample({
  clock: applyFilters,
  fn: ({ q, page }) => ({ q, page }),
  target: filters.enter,
});
```
