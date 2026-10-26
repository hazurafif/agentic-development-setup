---
id: playbook-spec-graph
type: playbook
status: active
title: The spec graph — living specs as ground truth
parent: playbook-spec
covers: [specs, frontmatter, wiki-links, spec-first, comments-policy]
tags: [specs]
---

## Rule

Intent lives in a connected graph of `SPEC.md` files beside the code, and the agent reads,
searches, and maintains it. Specs are the durable home for decisions, invariants,
trade-offs, and post-mortems — so intent survives the session.

## Structure

A hierarchy of small specs, each connected by frontmatter and links:

```
goal-and-requirements.md          (why the product exists)
  └─ architecture.md              (topology + numbered decisions)
       └─ module SPEC.md          (one per package/module)
            └─ submodule SPEC.md  (one per meaningful directory-level module)
```

Frontmatter identifies and connects every node:

```yaml
---
id: submodule-server-git
type: submodule-design
status: active
title: git — runner + worktree status/diff
parent: module-server
depends-on: [module-contracts]
tags: [public-surface-checked]
---
```

`[[wiki-links]]` reference other specs inline ([[playbook-doc-formats]] shows the doc
formats).

## Practice

1. **Spec-first changes.** A change that moves or blurs a boundary, contract, or
   documented behavior updates the owning spec first, in the same change as the code.
2. **Specs are living, not archival.** A decision that changes is rewritten in place;
   superseded text is deleted, not stacked in changelogs.
3. **Keep specs concise.** No restating code or another spec; describe responsibility,
   surface, and invariants — not implementation.
4. **Comments are near-zero.** Lint directives and rare one-line hazard notes only;
   rationale and narrative belong in the owning spec. When you would write a comment,
   ask which spec owns that fact.
5. **Give the agent spec tools when possible.** thinkrail ships a `spec-graph` pi
   extension exposing `spec_*` tools so the agent maintains the graph as part of its job;
   at minimum, prompt the agent to update the owning spec in the same change.

## Source

- thinkrail `AGENTS.md` — sections "Module structure and boundaries" and "Specs and
  comments"; 100 `SPEC.md` files across `packages/`, `apps/`, `e2e/`, `.github/`.
- thinkrail `packages/spec-graph/` — the `spec_*` tool extension.
