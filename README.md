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
  case-study-thinkrail.md      the evidence
templates/                     copy-paste skeletons for new projects
```

## How to use it

1. **Start a new project:** copy `templates/goal-and-requirements.md`,
   `templates/AGENTS.md`, and `templates/architecture.md` into the repo; give each module
   a `SPEC.md` from `templates/SPEC.md`; drop `templates/prompts/` into `.pi/prompts/`.
2. **Work a task:** follow `playbook/6-workflow-loop.md`.
3. **Doubt a rule:** check its Source citation in the playbook doc, then the case study.

## Credits

Patterns distilled from [JetBrains/thinkrail](https://github.com/JetBrains/thinkrail)
(Apache-2.0). Short quotes are cited to their source files for study purposes.
