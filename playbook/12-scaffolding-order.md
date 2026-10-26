---
id: playbook-scaffolding-order
type: playbook
status: active
title: Scaffolding order — from empty directory to first commit
parent: playbook-spec
covers: [greenfield-order, deciding-what-to-build, artifact-triggers]
tags: [bootstrap, scaffolding]
---

## Rule

Scaffold in dependency order: **intent before structure, structure before code, and
every artifact appears when triggered — not upfront.** Each artifact exists to hold a
decision; creating it before the decision exists is ceremony.

## Deciding what to build

The goal doc is the decision procedure, not paperwork:

1. Write the **Problem** first — one concrete sentence about what hurts.
2. **Capabilities** are the smallest set that solves that problem. Anything you can't
   trace back to the Problem is a Non-goal.
3. **Non-goals** is where you quit. If it's empty, the scope isn't understood yet —
   don't scaffold past it.
4. If the honest Problem is "I want to learn X", write that; the pattern serves learning
   projects identically, and the Non-goals will save you from scope drift mid-project.

## The order

### Phase 0 — intent (no code yet)

1. `goal-and-requirements.md` — from `templates/`; fill it by answering its sections in
   order (Goal → Problem → Who → Value → Principles → Capabilities → Non-goals).
2. `AGENTS.md` — from `templates/`; the routing table and the invariants you already
   know. The Stack section stays a placeholder until step 4.
3. Commit: `docs: bootstrap {{name}}` — **history begins with intent, not code.**

### Phase 1 — structure (first code)

4. Choose the stack, then create `architecture.md` recording it as **Decision #1 with
   an enforceable Rule** — plus Drivers and a one-line Topology sketch. Not before:
   no real decision, no architecture doc.
5. First module folder per [[playbook-module-anatomy]]: folder + `SPEC.md` + public
   surface + tests in the stack's layout ([[playbook-language-mapping]]).

### Phase 2 — triggers (as they appear, never scheduled)

6. A second module with its own boundary → new folder + `SPEC.md`; the parent spec
   documents the dependency edge.
7. First cross-module flow → harness folder + its spec from
   `templates/e2e-SPEC.md` ([[playbook-test-specs]]).
8. A rule the templates didn't capture → refine this know-how repo
   ([[playbook-applying]]); the learning loop closes.

## What not to do

- No `architecture.md` before a real decision; no Decision #2 until a second real
  choice is made.
- No pre-built empty folder trees — a folder without a spec is a guess about a boundary
  nobody has made yet.
- No gates beyond what there is to gate: fast gates arrive with the first tests, the
  harness spec with the harness ([[playbook-workflow-loop]]).

## Source

- thinkrail `goal-and-requirements.md` — "describes the product as it is and changes
  with it": artifacts follow reality, never predictions.
- thinkrail layout — all 100 `SPEC.md` files sit beside the code they govern; none
  float in a docs-only folder created in advance.
