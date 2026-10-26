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
2. **`index.ts` barrel at each submodule root**; siblings import through it, never
   internals. Named exceptions are allowed where a barrel would defeat code-splitting or
   a library convention (thinkrail: `packages/ui`, `apps/web/src/panels`) — name them in
   the parent spec ([[playbook-boundaries]]).
3. **Create a submodule folder for a boundary, not a file count.** The trigger is a new
   publicly owned concept (own surface + own invariants), e.g. thinkrail's `git/`,
   `workspaces/`, `auth/` under `server/src/`.
4. **Dependency edges between siblings are documented in the parent module's spec**,
   not restated in each leaf.
5. **Naming:** kebab-case folders; spec ids follow the hierarchy
   (`module-server` → `submodule-server-git`).

## Source

- thinkrail `packages/server/src/git/` — the folder above, verbatim.
- thinkrail `AGENTS.md` — "Module structure and boundaries" (fractal requirement, barrel
  rule + named exceptions, parent-spec edge rule).
