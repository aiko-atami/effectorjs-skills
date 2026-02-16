# EffectorJS skill

Universal AI skill for designing, refactoring, and reviewing **Effector** state management with modern, scope-safe patterns.

This skill is intended for agent workflows (Codex, Claude Code, and similar runtimes that support skills from GitHub repositories).

## What This Skill Covers

- Effector model design with `createStore`, `createEvent`, `createEffect`
- Declarative orchestration with `sample`, `attach`, and `split`
- SSR and scope safety with `fork`, `allSettled`, `serialize`, `hydrate`
- React integration (`useUnit`, `Provider`)
- Solid and Vue integration references
- Anti-pattern detection and refactoring guidance
- Legacy-to-modern migration map (v23+ defaults)

## Target Version

- Default target: **Effector v23+**
- Legacy code is supported through migration guidance, but legacy APIs are not recommended as defaults.

## Repository Structure

```text
skills/effectorjs/
  SKILL.md
  agents/openai.yaml
  references/
    core-patterns.md
    react-ssr-scope.md
    solid-scope.md
    vue-scope.md
    anti-patterns-and-fixes.md
    legacy-migration-map.md
    checklists.md
```

## Install

Use `npx skills` to install this skill:

```bash
npx skills add aiko-atami/effectorjs-skills --skill effectorjs
```

## When to Use

Use this skill when you need to:

- Design a new Effector model from scratch
- Refactor imperative or fragile Effector logic
- Add/repair SSR scope isolation
- Review Effector code for risks and regressions
- Migrate legacy Effector patterns to modern v23+ style

## Example Prompts

- "Design an Effector model for a paginated product list with retry and optimistic updates."
- "Refactor this model to remove `watch` business logic and `getState` reads."
- "Make this React SSR flow scope-safe using fork/allSettled/serialize/hydrate."
- "Migrate legacy `forward/guard` chains to modern `sample`-based flows."
- "Review this Effector module and list regressions, anti-patterns, and missing tests."

## Notes

- The skill prioritizes deterministic, declarative dataflow.
- It encourages small atomic stores and explicit unit topology.
- It includes acceptance checklists for design, refactor, SSR, review, and migration tasks.
