---
id: playbook-test-specs
type: playbook
status: active
title: Test specs — the harness is a module, coverage comes from specs
parent: playbook-spec
covers: [harness-spec, spec-derived-coverage, coverage-policy]
tags: [testing, specs]
---

## Rule

"Test spec" means two things, and a mature repo has both:

1. **The test harness gets its own `SPEC.md`** — it is a module like any other, with a
   Responsibility/Boundary ([[playbook-module-anatomy]]).
2. **What to test is derived from the owning module's spec** — its public surface and
   stated invariants — not from implementation details or coverage percentages.

## 1. The harness spec

Copy `templates/e2e-SPEC.md` into the harness folder when it appears. Sections, after
thinkrail's real `e2e/SPEC.md`:

- **Responsibility** — what the harness covers end to end.
- **Boundary** — Owns (runners, fixtures, helpers) / Consumes / Forbidden (no product
  runtime logic).
- **Execution model** — runner modes (unit, browser, live), how each is selected.
- **Isolation contract** — disposable fixtures, no production access, what a test may
  touch.
- **Credentials** — where tokens come from, what must never be logged.
- **Verification policy** — which suite is a commit gate, which runs once before
  handoff, which needs approval ([[playbook-workflow-loop]]).

## 2. Spec-derived coverage

1. Read the owning `SPEC.md` first ([[playbook-spec-graph]]); test **through the public
   surface** (the barrel), not internals.
2. Aim at **one test per stated invariant** where practical; boundary rules are the
   highest-value tests in the suite.
3. **Tag the spec when its surface is covered** — thinkrail marks 23 specs
   `tags: [public-surface-checked]`, making coverage a visible spec property.
4. **No manufactured coverage** for a localized change the spec does not govern;
   coverage theater is worse than an honest gap.

## Source

- thinkrail `e2e/SPEC.md` — Responsibility / Execution model / Isolation contract /
  Boundary / Verification policy sections; `e2e/workflows/SPEC.md` for a sub-harness.
- thinkrail `AGENTS.md` — "cover public surfaces and boundary rules with tests where
  practical, but do not manufacture coverage for a localized change".
