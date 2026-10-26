---
id: templates-prompts
type: module-design
status: active
title: prompts — reusable agent prompt templates
parent: architecture
depends-on: []
tags: [templates]
---

## Responsibility

Prompt templates to copy into a project's `.pi/prompts/` (or the harness equivalent).
Adapted from JetBrains/thinkrail's `.pi/prompts/`.

## Boundary

- **Owns:** the template files in this directory.
- **Forbidden:** explanatory prose inside the templates; templates carry only the prompt
  itself.
