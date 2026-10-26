---
id: architecture
type: architecture-design
status: active
title: Know-how repo — organization and decisions
parent: goal-and-requirements
covers: [repo-organization, doc-numbering, template-policy]
tags: [architecture]
---

## Topology

```
AGENTS.md                    agent entry point: routes to the right doc, holds conventions
goal-and-requirements.md     what this repo is and is not
architecture.md              this file: organization + decision journal
playbook/                    the pattern, one topic per numbered doc
  SPEC.md                    boundary of the playbook module itself
  1..6-*.md                  the distilled practices
  case-study-thinkrail.md    raw evidence with source file paths
templates/                   copy-paste skeletons; zero explanatory prose
```

## Decisions

1. **Playbook is one module with numbered docs.** Numbering (`1-context-routing.md`,
   `2-spec-graph.md`, ...) makes the set scannable and gives a stable citation target
   ("playbook doc 3"). A topic that outgrows its doc becomes its own module with a
   `SPEC.md`, not a longer doc. **Rule: one topic per playbook doc; cross-link, never
   restate.**
2. **Templates are dumb.** `templates/` holds pure skeletons with `{{placeholders}}` and
   no explanation — the playbook explains, templates ship. **Rule: explanatory prose never
   lives in a template.**
3. **Evidence lives in the case study, not the playbook.** Playbook docs state distilled
   rules; file paths, counts, and commit examples from thinkrail live in
   `playbook/case-study-thinkrail.md` so rule docs stay short.
4. **The repo eats its own dog food.** Frontmatter, `[[wiki-links]]`, routing `AGENTS.md`,
   and Conventional Commits apply to this repo, so the pattern is visible in situ.
