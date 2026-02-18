# Paths DSL

## Purpose

Define typed route paths and convert between URL string and params.

## Supported Parameter Syntax

- `/:id` string param
- `/:id?` optional string param
- `/:id+` non-empty array param
- `/:id*` zero-or-more array param
- `/:id<number>` numeric param
- `/:id<foo|bar>` union-like string literals
- `/:id{2,4}` bounded array segment count
- Combinations like `/:id<number>{1,3}?`

## Compile API

```ts
import { compile } from '@argon-router/paths';

const postPath = compile('/posts/:id<number>');

postPath.build({ id: 10 }); // '/posts/10'
postPath.parse('/posts/10'); // { path: '/posts/10', params: { id: 10 } }
```

## Validation Behavior

`createRoute({ path })` relies on path validation types and gives compile-time feedback for invalid token formats.

## Compatibility Conversion

Use `convertPath(path, 'express')` when migrating Express-like patterns to argon-router path syntax.
