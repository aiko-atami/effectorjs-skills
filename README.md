# Effector Ecosystem Skills

- [effectorjs](#effectorjs)
- [effector-storage](#effector-storage)
- [patronum](#patronum)
- [argon-router](#argon-router)

## effectorjs

Skill for Effector v23+ architecture, modeling, refactoring, and SSR-safe patterns.

Use when you need to:
- Design stores/events/effects and declarative dataflow (`sample`, `attach`, `split`)
- Refactor anti-patterns and legacy usage
- Build scope-safe SSR/test flows (`fork`, `allSettled`, `serialize`, `hydrate`)

Docs:
- `skills/effectorjs/SKILL.md`
- `skills/effectorjs/README.md`

Install command:
```bash
npx skills add aiko-atami/effectorjs-skills --skill effectorjs
```

## effector-storage

Skill for persistence strategies with `effector-storage` v7.x and contract-aware storage flows.

Use when you need to:
- Choose adapters (`local`, `session`, `query`, `broadcast`, `memory`)
- Configure `persist` / `createPersist` with `clock`, `pickup`, `context`
- Handle validation and persistence lifecycle (`done` / `fail` / `finally`)

Docs:
- `skills/effector-storage/SKILL.md`

Install command:
```bash
npx skills add aiko-atami/effectorjs-skills --skill effector-storage
```

## patronum

Skill for selecting and applying Patronum operators in Effector projects.

Use when you need to:
- Pick the right Patronum operator for a dataflow task
- Apply practical operator recipes and caveats
- Migrate older Patronum usage to v2 shorthand

Docs:
- `skills/patronum/SKILL.md`
- `skills/patronum/README.md`

Install command:
```bash
npx skills add aiko-atami/effectorjs-skills --skill patronum
```

## argon-router

How-to skill for React web integration of `@argon-router/core`, `@argon-router/react`, and `@argon-router/paths`.

Use when you need to:
- Configure routes, router, and controls
- Build route views with `RouterProvider`, `createRouteView`, `createRoutesView`, `Outlet`
- Add typed path params and query tracking
- Compose routes via `chainRoute`, `group`, `createVirtualRoute`

Docs:
- `skills/argon-router/SKILL.md`
- `skills/argon-router/references/*`

Install command:
```bash
npx skills add aiko-atami/effectorjs-skills --skill argon-router
```
