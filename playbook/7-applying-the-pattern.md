---
id: playbook-applying
type: playbook
status: active
title: Applying the pattern — bootstrapping a new repo
parent: playbook-spec
covers: [bootstrap-new-repo, template-copy-policy, external-references]
tags: [bootstrap]
---

## Rule

A new repo receives the pattern by **copying templates and never referencing this
know-how repo from its durable context**. An agent's routing must only target in-repo
files; cross-repo references rot on other machines, trip approval prompts, and confuse
sessions that lack the external path.

## Bootstrap procedure

1. **Copy the set** from `templates/`: `AGENTS.md`, `goal-and-requirements.md`,
   `architecture.md`, and `prompts/` into the new repo's `.pi/prompts/`. They are
   self-contained by design — copied together, their `[[wiki-links]]` resolve.
2. **Fill the goal doc first.** The `goal-and-requirements.md` placeholders force the
   decisions that everything else inherits (Goal, Problem, Who it's for, Non-goals).
   Answer them with the user before touching code.
3. **Grow specs fractally.** No `SPEC.md` files at zero modules; add the first module
   spec when the first meaningful module appears, using `templates/SPEC.md`. Do not
   over-spec a small repo — boundaries are documented where they exist.
4. **Commit conventionally from commit #1** ([[playbook-commit-discipline]]); the
   history is the audit trail from day one.
5. **Run the loop** ([[playbook-workflow-loop]]) for all subsequent work.

## What not to do

- **No `[[wiki-links]]` from the new repo into this repo.** Spec graphs are per-repo;
  the copied `AGENTS.md` already carries the distilled rules the agent needs.
- **Do not copy the playbook or case study into the new repo.** They are the training
  material for you, not runtime context for its agents. When in doubt, you consult the
  playbook; the repo runs on its own `AGENTS.md` + specs.
- **One exception — the bootstrap prompt.** `templates/prompts/bootstrap.md` names this
  repo's path, but it is a manual, one-shot tool: it runs once, copies files, and leaves
  no external reference behind.
- **A human-facing pointer is fine.** One README line crediting/linking this repo is
  acceptable — it is for people, not for the agent's routing table.

## Source

- thinkrail `AGENTS.md` — "Read context proportionally" implies self-containment: every
  routed path is inside the repo; nothing routes outside the checkout.
- thinkrail ships bundled workflows/skills *inside* the product rather than referencing
  external repos — the same containment principle, one level up.
