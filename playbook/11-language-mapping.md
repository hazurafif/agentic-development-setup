---
id: playbook-language-mapping
type: playbook
status: active
title: Language mapping — porting the mechanics to other stacks
parent: playbook-spec
covers: [python-mapping, stack-portability, invariants-over-mechanisms]
tags: [portability, python]
---

## Rule

The **practices** — spec graph, routing, boundary ownership, commit discipline, the loop
— are stack-agnostic. The **mechanics** shown in this playbook (`index.ts` barrels,
co-located `*.test.ts`, kebab-case) are thinkrail's TypeScript dialect. When porting:
keep the invariant, swap the mechanism, and record the ported mechanics in the new
repo's `AGENTS.md` Stack section.

## Python translation table

| Invariant (mechanic in this playbook) | Python mechanic |
| --- | --- |
| One public surface per module (`index.ts` barrel) | `__init__.py` re-exports + `__all__`; consumers `from package import Thing`, never `from package._internal import ...` — a leading underscore marks internals the way a non-exported file does |
| Mechanized boundary checks (`check:boundaries`) | [`import-linter`](https://import-linter.readthedocs.io) contracts — layered, independent, forbidden — wired into CI; `ruff` import rules as the lint layer |
| Co-located tests so they can't be orphaned | a `tests/` tree that **mirrors the package tree one-to-one** (`tests/server/git/test_runner.py` ↔ `server/git/runner.py`); co-location exists in Python but is non-idiomatic and leaks test files into packaging |
| Expensive tests explicitly selectable (`.live.spec.ts`) | registered pytest marker `@pytest.mark.live`; default invocation runs `-m "not live"`, CI runs live only with approval |
| kebab-case folders | snake_case packages/modules (PEP 8) — spec ids stay kebab (`submodule-server-git`): they are doc identifiers, not code |
| Disposable fixtures, no production access | pytest fixtures with `tmp_path` / `monkeypatch`; HTTP faked with `respx`/`responses`; real credentials never reach a test |
| Bun + Turbo workspaces | uv/pip workspaces, or a single package with submodule folders — the fractal shape is unchanged |
| Fast gates (lint, typecheck, unit) | `ruff check`, `mypy`/`pyright`, `pytest` — same ordering and escalation rules |

## What never changes

- The spec graph: `SPEC.md` placement beside the code, frontmatter, `[[wiki-links]]`,
  spec-first changes ([[playbook-spec-graph]], [[playbook-module-anatomy]]).
- `AGENTS.md` routing, goal and architecture doc formats ([[playbook-context-routing]],
  [[playbook-doc-formats]]).
- Conventional Commits, PR trails, handoff hygiene, subtraction pass
  ([[playbook-commit-discipline]]).
- The harness folder is a module with a spec ([[playbook-test-specs]]); expensive suites
  require approval ([[playbook-workflow-loop]]).

## Recording the port

During bootstrap ([[playbook-applying]]), the mapping lands as four decisions in the new
repo's `AGENTS.md`: the public-surface mechanism, the boundary-gate commands, the test
layout, and the live-test selection rule. Those four are the whole port; everything else
is copied as-is.

## Source

- Extrapolation, by design: thinkrail is a TypeScript-only repo, so this mapping derives
  Python mechanics from its *stated invariants* rather than from Python files in it.
  Marked as analogy, not citation — re-verify against current Python tooling when
  applying.
- Python community practice: PEP 8 naming; src-layout with a mirrored `tests/` tree
  (pytest documentation); import-linter contracts as the mechanized equivalent of
  `check:boundaries`.
