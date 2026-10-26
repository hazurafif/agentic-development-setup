---
id: goal-and-requirements
type: goal-and-requirements
status: active
title: Agentic development know-how — goal and scope
covers: [product-goal, product-audience, product-principles, product-capabilities, product-non-goals]
tags: [product, scope]
---

## Goal

Be the single go-to reference for practicing agentic software development: the distilled,
reusable pattern of how agent-first repositories are structured — goal docs, spec graphs,
module boundaries, commit discipline, verification, and the working loop — ready to apply
to any project via copy-paste templates.

## Problem

Agent output quality is bounded by repo scaffolding, but the knowledge of what good
scaffolding looks like is scattered: it lives in exemplary repos (like thinkrail), blog
posts, and chat sessions that evaporate. Re-deriving it per project wastes time and
produces inconsistent structure.

## Who it's for

Me, working with coding agents (`pi` and similar) on any repository — as the reference I
open before starting a project, and the source I copy templates from.

## Value

- **One place.** The pattern is written down once, with evidence, instead of living in
  bookmarks and memory.
- **Actionable.** Every practice ends in a template under `templates/` that can be copied
  into a new project in minutes.
- **Evidence-based.** Normative rules cite the source repo and file they were distilled
  from, so they can be re-verified as sources evolve.

## Principles

- **Distill, don't copy.** Patterns are stated as rules with rationale and a source
  citation; the case study holds the raw evidence.
- **Practice what it preaches.** This repo uses the same frontmatter, wiki-links, routing
  `AGENTS.md`, and commit discipline it documents.
- **Templates over prose.** To apply the pattern, copy a file; prose explains, templates
  ship.
- **Concise docs.** Rules and rationale only; no restating between docs.

## Capabilities

- `playbook/` — numbered, one-topic-per-doc pattern guides (context routing, spec graph,
  doc formats, boundaries, commit discipline, working loop).
- `playbook/case-study-thinkrail.md` — the annotated teardown the patterns come from.
- `templates/` — copy-paste skeletons: `AGENTS.md`, `goal-and-requirements.md`,
  `architecture.md`, module `SPEC.md`, prompt templates.

## Non-goals

- Not a project itself: no exercise apps, tools, or generated scaffolds live here.
- Not a tool installation or configuration guide for any specific agent harness.
- Not an implementation of spec tooling (like thinkrail's `spec_*` pi extension) — that is
  documented as a pattern, not built here.
- Not a general prompt-engineering collection; only repo-structure prompts that support
  the documented workflow.
