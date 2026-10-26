---
id: case-study-thinkrail
type: case-study
status: active
title: Case study — JetBrains/thinkrail (studied 2026-10)
parent: playbook-spec
covers: [evidence-thinkrail]
tags: [evidence, thinkrail]
---

Raw evidence behind the playbook rules. All paths are repo-relative to
https://github.com/JetBrains/thinkrail. Re-verify when citing normatively; the repo is
young and moves fast.

## What it is

"Agentic IDE that gets better every time you use it" — a thin host around the
[`pi`](https://github.com/earendil-works/pi) coding agent, built by JetBrains. Bun + Turbo
monorepo, TypeScript strict, React 19. The project treats its own development process as a
feature: specs, agent docs, and gates are first-class product artifacts.

## The numbers

| Artifact                        | Count / form                        |
| ------------------------------- | ----------------------------------- |
| `SPEC.md` files                 | 100 (packages, apps, e2e, .github)  |
| Architecture decisions          | 23 numbered, each with a Rule       |
| Agent prompt templates          | 5 (`.pi/prompts/`)                  |
| Root agent docs                 | `AGENTS.md`, `CLAUDE.md`, `goal-and-requirements.md`, `architecture.md`, `pi-compatibility.md` |

## Key files

- `AGENTS.md` — router ("Read context proportionally") + repo-wide invariants +
  verification + handoff hygiene. ~100 lines, no fluff.
- `goal-and-requirements.md` — Goal / Problem / Who it's for / Value / Principles /
  Capabilities / Non-goals; frontmatter `covers` lists 6 topics; "holds no versions or
  roadmap".
- `architecture.md` — Drivers → Topology (ASCII dependency graph of ~20 packages with
  one-line responsibilities) → 23 decisions with **Rule:** lines.
- `packages/server/src/git/SPEC.md` — leaf module spec example; Boundary = Owns /
  Consumes / Forbidden; dense invariants (timeout semantics, ref resolution rules).
- `.github/SPEC.md` — even the CI pipeline has a module spec with a Boundary.
- `packages/spec-graph/` — pi extension providing `spec_*` tools; the agent maintains the
  spec graph itself. `packages/spec-graph/tools/SPEC.md` +
  `packages/spec-graph/core/SPEC.md` split it further.
- `.pi/prompts/commit.md` — full text: *"Read the staged changes (`git diff --cached`)
  and write a Conventional Commits message. Use the type that fits (feat/fix/refactor/
  docs/test/chore) with scope `${1:-infer it from the files}`, an imperative subject under
  72 chars, and a short body explaining the why when it isn't obvious."*

## Commit history evidence (GitHub API, Oct 2026)

- Every merge commit is Conventional Commits with scope: `feat(locales): complete the
  Simplified Chinese catalog (#871)`, `fix(server): reject template names containing a
  colon (#797)`, `fix(web): close history search overlay on toggle and outside click (#796)`.
- PR #795 body preserves the full agent-session trail as ~20 step commits: `fix(server):
  ...` → `test(server): cover ...` → `Document that ...` → `Qualify ... in the store
  spec` → several refinement steps → `docs`/spec updates — then squash-merged.
- Hygiene is visible in history: commits named `Drop the rationale comment`,
  `Frame the colon rule as the NTFS alternate-data-stream case`, `test(locales): hold
  bundled translations to en.json and document the rule`.

## Verification gates (from AGENTS.md)

Fast, free: `check:deps`, `check:boundaries`, `check:seams`, `check:spec-surface`,
`lint`, `typecheck`, `test`. Full no-agent browser suite (`e2e`) once before handoff.
Live-agent suites: focused ones freely, complete `e2e:full` only with user approval
("spends real provider tokens"). `check:compiler` diffs a committed React-Compiler census
baseline — behavior regressions of tooling are gated too.

## Notable opinions worth stealing

1. "Specs are the durable home for intent... Comments are near-zero" — rationale has an
   address ([[playbook-spec-graph]]).
2. "Read context proportionally" — the router pattern ([[playbook-context-routing]]).
3. Owns/Consumes/Forbidden boundary lists ([[playbook-doc-formats]]).
4. Subtraction pass before handoff ([[playbook-commit-discipline]]).
5. Escalation of token-expensive suites ([[playbook-workflow-loop]]).
