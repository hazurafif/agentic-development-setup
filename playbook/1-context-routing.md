---
id: playbook-context-routing
type: playbook
status: active
title: Context routing — AGENTS.md is a router, not a brain dump
parent: playbook-spec
covers: [agents-md, proportional-context, doc-layering]
tags: [context, agents-md]
---

## Rule

The agent entry document routes; it does not explain. `AGENTS.md` (or the harness
equivalent) holds only: a one-paragraph project identity, a task→document routing table,
and repo-wide invariants that apply to every task. Everything else lives in a dedicated
doc the router points to.

## Why

- Context is a budget. Front-loading every rule into the entry doc bloats every session
  with irrelevant context and invites drift between duplicated statements.
- The router keeps the entry doc stable while deep docs change freely.

## Practice

1. Layer docs by question type, then write the routing table:

   | Task asks about...           | Read                          |
   | ---------------------------- | ----------------------------- |
   | product goal, scope          | `goal-and-requirements.md`    |
   | structure, cross-module design | `architecture.md`           |
   | a boundary, contract, invariant | owning module's `SPEC.md`  |
   | a specific subsystem deep-dive | that subsystem's task doc   |

2. State invariance explicitly: "Localized work does not require unrelated specs or a
   full repository map."
3. Keep invariants in the router only when they are truly universal (dependency rules,
   safety rules). Everything conditional belongs in the scoped doc.

## Source

- thinkrail `AGENTS.md` — section "Read context proportionally": goal doc for product,
  `architecture.md` for topology, owning `SPEC.md` for boundary work, a dedicated
  `pi-compatibility.md` for pi upgrades.
