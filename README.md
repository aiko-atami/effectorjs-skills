# Effector Ecosystem Skills

AI skills for tasks around **Effector** and related libraries.
This repository supports multiple skills using a consistent structure.

## Skill Catalog

| Skill | Focus | Target Version | Path |
| --- | --- | --- | --- |
| `effectorjs` | Architecture, refactoring, reviews, and SSR in Effector | Effector v23+ | `skills/effectorjs` |
| `effector-storage` | Persistence adapter selection, sync semantics, and contract-aware storage wiring | effector-storage v7.x | `skills/effector-storage` |
| `patronum` | Patronum operator selection and usage in Effector projects | Patronum v2.x | `skills/patronum` |

## Install

Install via `npx skills`:

```bash
# Effector core skill
npx skills add aiko-atami/effectorjs-skills --skill effectorjs

# Effector Storage skill
npx skills add aiko-atami/effectorjs-skills --skill effector-storage

# Patronum skill
npx skills add aiko-atami/effectorjs-skills --skill patronum
```

## Skills

### `effectorjs`

Use when:
- Designing models (`createStore`, `createEvent`, `createEffect`)
- Building declarative dataflow (`sample`, `attach`, `split`)
- Working with SSR/scope (`fork`, `allSettled`, `serialize`, `hydrate`)
- Refactoring anti-patterns and migrating legacy APIs

Documentation:
- `skills/effectorjs/README.md`
- `skills/effectorjs/SKILL.md`

### `patronum`

Use when:
- Choosing the right Patronum operator for a task
- Applying practical recipes in Effector code
- Explaining signatures, caveats, and overload behavior
- Migrating legacy Patronum usage to v2 shorthand

Documentation:
- `skills/patronum/README.md`
- `skills/patronum/SKILL.md`

### `effector-storage`

Use when:
- Choosing storage adapters (`local`, `session`, `query`, `broadcast`, `memory`, etc.)
- Wiring `persist` / `createPersist` with `clock`, `pickup`, `context`, and `keyPrefix`
- Validating persisted data with contracts and handling `done` / `fail` / `finally`
- Designing SSR-safe fallback behavior with tools like `either` and `async`

Documentation:
- `skills/effector-storage/SKILL.md`
