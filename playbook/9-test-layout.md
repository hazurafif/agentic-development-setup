---
id: playbook-test-layout
type: playbook
status: active
title: Test layout — co-located units, a harness folder for flows
parent: playbook-spec
covers: [test-co-location, harness-folder, fixture-policy, live-test-naming]
tags: [testing, structure]
---

## Rule

Unit tests live **beside the code they cover**; tests that exercise cross-module behavior
live in a **top-level harness folder** that is itself a module ([[playbook-test-specs]]).
Fixtures are disposable and touch no production system.

## What goes where

| Test kind | Lives in | Runs |
| --- | --- | --- |
| Unit — one module's surface & invariants | co-located `*.test.ts` beside the source | fast gate, always free |
| Flow / E2E — cross-module, user-visible behavior | top-level `e2e/` harness folder | full suite once before handoff |
| Live — real providers, real tokens | same harness, `*.live.spec.ts` | only with explicit approval |

## Practice

1. **Co-locate unit tests** (`git.ts` → `git.test.ts`). They cannot be orphaned by
   refactors, and coverage gaps are visible in the tree.
2. **Harness folder at repo root** (`e2e/`): flat `*.spec.ts` flow files plus shared
   helpers; give it a `SPEC.md` like any module ([[playbook-module-anatomy]]).
3. **Name token-spending tests `*.live.spec.ts`** so tooling and humans can select around
   them — the fast gates never pick them up by accident.
4. **Fixtures are disposable**: no production access, no network, no shared mutable
   state; check them in beside the tests or under the harness, never generated ad hoc
   against real systems.
5. **Rename per stack freely** (`tests/`, `__tests__`) — the invariants are co-location,
   a spec-carrying harness folder, and explicit naming of expensive tests.

## Source

- thinkrail — co-located tests everywhere (`apps/desktop/src/*.test.ts`,
  `packages/server/src/git/git.test.ts`); `e2e/` with `agent.live.spec.ts`,
  `agent-naming.live.spec.ts` vs plain `*.spec.ts`.
- thinkrail `AGENTS.md` — "Verification": "Local tests use disposable fixtures and have
  no production access"; gate ordering and `e2e:full` approval rule.
