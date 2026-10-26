---
id: playbook-spec
type: module-design
status: active
title: playbook — the distilled agentic development pattern
parent: architecture
depends-on: []
tags: [playbook]
---

## Responsibility

Hold the distilled, normative pattern of agentic software development: how an agent-first
repo structures context routing, living specs, doc formats, module boundaries, commit
discipline, and the day-to-day working loop. One topic per numbered doc, every rule
traceable to evidence in [[case-study-thinkrail]].

## Boundary

- **Owns:** the rule statements and their rationale; the reading order between docs.
- **Consumes:** `architecture.md` for numbering and scope decisions;
  `playbook/case-study-thinkrail.md` for all source evidence.
- **Forbidden:** duplicating a rule across two docs; hosting evidence (paths, counts,
  commit excerpts) outside the case study; explaining templates (that is
  [[playbook-doc-formats]]' job).
