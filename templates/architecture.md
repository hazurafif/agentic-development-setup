---
id: architecture
type: architecture-design
status: active
title: "{{Project name}} — top-level architecture"
parent: goal-and-requirements
covers: ["{{decision-topics}}"]
tags: [architecture]
---

## Drivers

{{The forces that shape the design: runtime, team, constraints.}}

## Topology

{{ASCII dependency graph: one line per package/module with a one-line responsibility and
its allowed dependencies.}}

```
{{apps/example}}   {{responsibility}}   ── depends on ─▶ {{packages/...}}
```

## Decisions

1. **{{Decision name}}.** {{What was decided and the essential why.}} **Rule: {{the
   enforceable rule, stated so a check could verify it}}.**
