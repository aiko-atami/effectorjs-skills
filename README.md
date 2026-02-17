# Effector Ecosystem Skills

AI skills for tasks around **Effector** and related libraries.
This repository supports multiple skills using a consistent structure.

## Skill Catalog

| Skill | Focus | Target Version | Path |
| --- | --- | --- | --- |
| `effectorjs` | Architecture, refactoring, reviews, and SSR in Effector | Effector v23+ | `skills/effectorjs` |
| `patronum` | Patronum operator selection and usage in Effector projects | Patronum v2.x | `skills/patronum` |

## Install

Install via `npx skills`:

```bash
# Effector core skill
npx skills add aiko-atami/effectorjs-skills --skill effectorjs

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

## Repository Structure

```text
skills/
  effectorjs/
    SKILL.md
    README.md
    agents/openai.yaml
    references/...
  patronum/
    SKILL.md
    README.md
    agents/openai.yaml
    references/...
```
