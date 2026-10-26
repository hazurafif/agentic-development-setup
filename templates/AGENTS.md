# {{Project name}}

{{One paragraph: what this is, built around/with what, and the one thing that makes it
coherent.}}

## Read context proportionally

- For the product's goal, principles, capabilities, and non-goals, read
  `goal-and-requirements.md`.
- For system topology, cross-module decisions, and repo-wide structure, read
  `architecture.md`.
- For work governed by or touching a module boundary, contract, invariant, or documented
  behavior, read the owning `SPEC.md` first.
- Localized work does not require unrelated specs or a full repository map.

## Module structure and boundaries

- Every package and meaningful directory-level sub-module has a `SPEC.md` stating its
  responsibility, public surface, allowed dependencies, and forbidden reaches.
- A sub-module exposes an `index.ts` barrel as its only public surface; siblings import
  through the barrel, never internals.
- Dependency edges between sibling sub-modules live in the parent module's `SPEC.md`.
- A change that moves or blurs a boundary updates the owning spec first, in the same
  change as the code.

## Repo-wide invariants

- {{Rule that applies to every task: dependency directions, state ownership, error
  policy, naming.}}

## Specs and comments

Specs are the durable home for intent, decisions, invariants, trade-offs, and
post-mortems. Keep them concise and never restate code or another spec. Comments are
near-zero: rationale and narrative belong in the owning spec.

## Verification

- Iterate with the smallest relevant unit or focused target.
- Fast gates ({{lint / typecheck / unit}}) run freely and often.
- {{Full suite}} runs once after the combined implementation, before final handoff.
- {{Expensive / token-spending suites}} require explicit user approval.

## Stack

{{Runtime · language · framework · key libraries, one line.}}
