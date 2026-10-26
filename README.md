# agentic-development-setup

My go-to know-how base for **agentic software development**: the distilled pattern of how
agent-first repositories are structured — studied from
[JetBrains/thinkrail](https://github.com/JetBrains/thinkrail) and practiced on this repo
itself.

## Repo map

```
AGENTS.md                      agent entry point — routes, doesn't explain
goal-and-requirements.md       what this repo is and is not
architecture.md                organization + decision journal
playbook/                      the pattern, one topic per numbered doc
  1-context-routing.md         AGENTS.md as router
  2-spec-graph.md              living specs as ground truth
  3-doc-formats.md             the three doc skeletons
  4-boundaries.md              Owns / Consumes / Forbidden, mechanized
  5-commit-discipline.md       conventional commits + handoff hygiene
  6-workflow-loop.md           the end-to-end task loop
  7-applying-the-pattern.md    bootstrapping a new repo from the templates
  8-module-anatomy.md          module folder layout: SPEC.md + barrel + co-located tests
  9-test-layout.md             where tests live: co-located units + harness folder
  10-test-specs.md             the harness spec + spec-derived coverage
  11-language-mapping.md       porting the mechanics to Python & other stacks
  case-study-thinkrail.md      the evidence
templates/                     copy-paste skeletons for new projects (incl. e2e-SPEC.md)
```

## How to use it

1. **Start a new project:** follow `playbook/7-applying-the-pattern.md` — or just run
   the `bootstrap` prompt from `templates/prompts/` inside the new repo and let the agent
   copy and fill the templates from your answers.
2. **Work a task:** follow `playbook/6-workflow-loop.md`.
3. **Doubt a rule:** check its Source citation in the playbook doc, then the case study.

## Credits

Patterns distilled from [JetBrains/thinkrail](https://github.com/JetBrains/thinkrail)
(Apache-2.0). Short quotes are cited to their source files for study purposes.
