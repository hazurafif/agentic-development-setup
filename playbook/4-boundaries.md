---
id: playbook-boundaries
type: playbook
status: active
title: Module boundaries — fractal, documented, and mechanized
parent: playbook-spec
covers: [module-boundaries, public-surface, dependency-edges, boundary-checks]
tags: [boundaries]
---

## Rule

Clear, fractal module boundaries are a top-priority requirement, and they are enforced by
machinery, not goodwill.

## Practice

1. **Every module and meaningful directory-level sub-module has a `SPEC.md`** stating
   responsibility, public surface, allowed dependencies, and forbidden reaches
   ([[playbook-doc-formats]], format #3).
2. **One public surface per module.** A sub-module exposes an `index.ts` barrel; siblings
   import through the barrel, never internals. Per-file imports are exceptions with a
   named reason (e.g. code-splitting).
3. **Dependency edges live in the parent spec.** The parent module's `SPEC.md` documents
   edges between its children; leaves don't each restate them.
4. **Mechanize the checks.** Pair each boundary rule with a script/gate:
   dependency-direction lint (`check:deps`), boundary conformance (`check:boundaries`),
   seam checks (`check:seams`), public-surface validation against enrolled specs
   (`check:spec-surface`). A rule without a gate is a suggestion.
5. **Boundary work is spec work.** A boundary change follows the spec-first rule
   ([[playbook-spec-graph]]); the checks in rule 4 verify the spec still matches the
   code.

## Source

- thinkrail `AGENTS.md` — "Module structure and boundaries" (fractal requirement, barrel
  rule, parent-spec edge rule, spec-first rule).
- thinkrail root `package.json` scripts — `check:deps`, `check:boundaries`,
  `check:seams`, `check:spec-surface` as PR/merge gates.
