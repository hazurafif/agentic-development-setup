---
id: "submodule-{{name}}"
type: submodule-design
status: active
title: "{{name}} — {{one-line responsibility}}"
parent: "{{parent-spec-id}}"
depends-on: []
tags: []
---

## Responsibility

{{What this module does, in one paragraph. Why it exists as its own module. No
implementation detail.}}

## Boundary

- **Owns:** {{the surface and state this module is the single home of; public API entry
  points; files/state nothing else may write}}
- **Consumes:** {{modules and external tools it may call}}
- **Forbidden:** {{reaches that would blur the boundary: modules it must never import,
  state it must never write, concerns owned elsewhere}}

## Invariants

- {{A rule that must always hold, stated so it is enforceable or testable.}}

## Notes

{{Trade-offs, post-mortems, and pointers to related specs via [[wiki-link]].}}
