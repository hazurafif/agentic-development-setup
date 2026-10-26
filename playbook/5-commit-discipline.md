---
id: playbook-commit-discipline
type: playbook
status: active
title: Commit discipline — history as the agent's audit trail
parent: playbook-spec
covers: [conventional-commits, pr-trail, handoff-hygiene, subtraction-pass]
tags: [commits]
---

## Rule

Conventional Commits with a scope, imperative subject, and a body that explains the *why*.
History is the readable record of the agent session; treat it as part of the deliverable.

Format: `type(scope): imperative subject ≤72 chars` — types `feat/fix/refactor/docs/test/
style/chore`; scope = module or area (`feat(locales):`, `fix(server):`, `test(server):`,
`e2e:`). Body explains why when it isn't obvious.

## Practice

1. **Commit per logical step, not per session.** Small, single-purpose commits let a
   reviewer (human or agent) replay the work.
2. **Preserve the session trail in the PR.** When squash-merging, keep the per-step
   commits as the PR body's bullet trail — the merge commit then reads as the session log.
3. **Spec updates ride with the code.** A PR that changes behavior updates the owning
   spec and README claims in the same change; look for commits like `docs: record ... in
   the architecture` inside feature PRs.
4. **Handoff hygiene before done:**
   - Review the task-scoped diff (branch vs base) before opening the PR.
   - **Subtraction pass** on nontrivial work: remove avoidable abstractions, state owners,
     compatibility layers, fallbacks; justify what remains.
   - Never add `@ts-ignore`/lint-suppressions to pass a gate — treat the error as a design
     signal; suppression needs explicit user approval.
   - Migrate every occurrence when replacing a pattern, or name the intentional survivors.
5. **Expensive actions escalate.** Fast gates (lint, typecheck, unit) run freely; suites
   that spend real tokens or long wall-time need explicit approval.

## Source

- thinkrail `.pi/prompts/commit.md` — the commit-message prompt template.
- thinkrail GitHub history (Oct 2026) — e.g. PR #795 `fix(server): omit deleted project
  folders from Recent Projects`: 20+ step commits including `test(server):`, spec
  updates, and `docs:` commits, squash-merged with the trail in the body.
- thinkrail `AGENTS.md` — "Handoff hygiene" section (subtraction pass, suppression rule,
  README claim review, gate escalation for `e2e:full`).
