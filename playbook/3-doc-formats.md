---
id: playbook-doc-formats
type: playbook
status: active
title: Doc formats — the three skeletons worth copying
parent: playbook-spec
covers: [goal-doc-format, architecture-decisions, module-spec-format]
tags: [formats]
---

## Rule

Use proven skeletons instead of inventing structure per project. Three formats cover most
needs; each is copyable from `templates/`.

## 1. Goal doc — `goal-and-requirements.md`

Fixed sections: **Goal / Problem / Who it's for / Value / Principles / Capabilities /
Non-goals**. Key disciplines:

- Describes the product *as it is* and changes with it — "holds no versions or roadmap".
- **Non-goals is mandatory.** Scope is defined as much by refusal as by inclusion.
- Principles are durable decisions every feature must follow.

## 2. Architecture doc — `architecture.md`

Sections: **Drivers** (what forces the design) → **Topology** (an explicit dependency
graph, even ASCII) → **Decisions** (numbered). Key disciplines:

- Every decision carries an enforceable **Rule:** line, not just rationale.
  Example: *"Rule: `apps/web` depends on `contracts`, `locales`, ... only — never on
  `server`."*
- Decisions are numbered so specs and conversations can cite "Decision #10".
- The topology graph lists each package with a one-line responsibility and its allowed
  dependencies — this is the map the agent uses for navigation.

## 3. Module spec — `SPEC.md` per module

Sections: **Responsibility** (one paragraph) → **Boundary** → optional deep-dive sections.
The Boundary has three lists:

- **Owns:** the surface and state this module is the single home of.
- **Consumes:** modules and tools it may call.
- **Forbidden:** the reaches that would blur the boundary.

"Owns/Consumes/Forbidden" is the load-bearing idea: it converts a vague "keep modules
clean" into checkable statements.

## Source

- thinkrail `goal-and-requirements.md` — section list quoted above; the "no roadmap"
  sentence is verbatim policy.
- thinkrail `architecture.md` — 23 numbered decisions, each ending in a **Rule**.
- thinkrail `packages/server/src/git/SPEC.md` and `.github/SPEC.md` — boundary format;
  note even CI has a spec.
