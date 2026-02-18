# React Native

## Purpose

Integrate Argon Router state with React Navigation UI in mobile apps.

## Package Set

Install:
- `@argon-router/react-native`
- `@argon-router/core`
- `@argon-router/react`
- `@react-navigation/native`
- `@react-navigation/stack`
- `@react-navigation/bottom-tabs`

Plus React Navigation peer deps (`react-native-screens`, `react-native-safe-area-context`).

## Core Model

- Argon Router manages route state and params.
- React Navigation renders screens and transitions.
- Navigation should be triggered via Argon route events (`route.open`), not direct `navigation.navigate`.

## Stack Navigator Pattern

```tsx
import { NavigationContainer } from '@react-navigation/native';
import { createArgonStackNavigator } from '@argon-router/react-native';
import { createRouteView, RouterProvider } from '@argon-router/react';

const StackNavigator = createArgonStackNavigator({
  router,
  routes: [HomeScreen, DetailsScreen],
});

export function App() {
  return (
    <RouterProvider router={router}>
      <NavigationContainer>
        <StackNavigator />
      </NavigationContainer>
    </RouterProvider>
  );
}
```

## Bottom Tabs Pattern

```tsx
import { createArgonBottomTabsNavigator } from '@argon-router/react-native';

const TabsNavigator = createArgonBottomTabsNavigator({
  router,
  routes: [HomeTab, SearchTab, ProfileTab],
});
```

## Guardrails

- Keep one source of truth for navigation: Argon routes and router units.
- Ensure all screen route views are registered in navigator route list.
- Keep `RouterProvider` above `NavigationContainer` in app root.
- Preserve type-safe params in `createRoute({ path })` and `route.open({ params })`.
