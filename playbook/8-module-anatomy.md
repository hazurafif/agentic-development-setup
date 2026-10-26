---
id: playbook-module-anatomy
type: playbook
status: active
title: Module anatomy — what goes in a module folder
parent: playbook-spec
covers: [module-folder, submodule-when, barrel-placement, spec-placement]
tags: [structure]
---

## Rule

A module is a folder that owns a boundary, and the folder shape repeats **fractally** at
every level: module root and submodule folder carry the same three things — a `SPEC.md`
beside the code, an `index.ts` barrel as the only public surface, and sources with
co-located tests.

## The shape (real example: thinkrail `packages/server/src/git/`)

```
packages/server/              module root
  SPEC.md                     module spec (id: module-server)
  src/
    git/                      submodule folder — one owned boundary
      SPEC.md                 submodule spec (id: submodule-server-git)
      index.ts                barrel: the submodule's ONLY public surface
      git.ts                  internals — siblings never import these directly
      refs.ts
      git.test.ts             tests co-located beside what they cover
      gitExec.test.ts
```

## Practice

1. **`SPEC.md` sits at the root of every module and submodule folder**, next to the code
   it governs — not in a central docs folder ([[playbook-spec-graph]]).
2. **The barrel sits at the submodule root.** Placement is this doc's concern; the
   one-public-surface rule and its named exceptions (`packages/ui`,
   `apps/web/src/panels`) are owned by [[playbook-boundaries]].
3. **Create a submodule folder for a boundary, not a file count.** The trigger is a new
   publicly owned concept (own surface + own invariants), e.g. thinkrail's `git/`,
   `workspaces/`, `auth/` under `server/src/`.
4. **Dependency edges between siblings are documented in the parent module's spec**,
   not restated in each leaf.
5. **Naming:** follow the language's convention — kebab-case in TypeScript, snake_case in
   Python ([[playbook-language-mapping]]); spec ids keep the kebab hierarchy
   (`module-server` → `submodule-server-git`) since they are doc identifiers, not code.

## Source

- thinkrail `packages/server/src/git/` — the folder above, verbatim.
- thinkrail `AGENTS.md` — "Module structure and boundaries" (fractal requirement, barrel
  rule + named exceptions, parent-spec edge rule).
