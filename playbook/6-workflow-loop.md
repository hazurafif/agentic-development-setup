---
id: playbook-workflow-loop
type: playbook
status: active
title: The working loop — one task, end to end
parent: playbook-spec
covers: [task-loop, isolation, verification-order, handoff]
tags: [workflow]
---

## Rule

Every task runs the same loop. The loop is where the other playbook docs plug in.

## The loop

1. **Orient ([[playbook-context-routing]]).** Identify the task type; read the routed
   doc(s) only — the owning spec for boundary work, no full-repo map for localized work.
2. **Check the spec.** If the work touches a boundary, contract, or documented behavior,
   the owning `SPEC.md` is the source of truth — and if it's wrong, updating it is part
   of the task ([[playbook-spec-graph]]).
3. **Isolate.** Work on a branch; in agent-first setups prefer a git worktree per task so
   parallel agents and the user's checkout never collide.
4. **Plan → step → commit ([[playbook-commit-discipline]]).** Maintain a shared plan;
   each completed step becomes one conventional commit.
5. **Verify in order.** Iterate with the smallest relevant unit/focused target; run fast
   gates freely; run the full no-agent suite once before handoff; escalate suites that
   spend real tokens or long wall-time to the user for approval.
6. **Handoff review.** Review the task-scoped diff; run the subtraction pass; audit new
   comments and suppressions; update README/spec claims ([[playbook-commit-discipline]]).
7. **Merge and settle.** Squash-merge with the step trail preserved; delete the worktree;
   the spec graph now reflects the new state of the world.

## Why the order matters

Spec-before-code prevents the agent from inventing boundaries; isolation-before-work
prevents collisions; smallest-test-first prevents debugging through the full suite;
expensive-last prevents token burn during iteration.

## Source

- thinkrail `AGENTS.md` — "Verification" (gate ordering, escalation) and "Handoff
  hygiene"; `e2e/SPEC.md` (runner modes, isolation guarantees); README — worktree
  workspaces as the isolation model.
