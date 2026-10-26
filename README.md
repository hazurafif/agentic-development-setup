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
  12-scaffolding-order.md      greenfield: what to create first, in what order
  case-study-thinkrail.md      the evidence
templates/                     copy-paste skeletons for new projects (incl. e2e-SPEC.md)
```

## How to use it

1. **First time on a new project:** follow `playbook/12-scaffolding-order.md` — from
   empty directory to first commit in dependency order: decide what to build via the
   goal doc, then `AGENTS.md`, then the stack decision, then the first module.
   Automate the copying with the `bootstrap` prompt from `templates/prompts/`.
2. **Work a task:** follow `playbook/6-workflow-loop.md` — orient → spec → isolate →
   step/commit → verify → handoff review → merge.
3. **Different stack (e.g. Python):** translate the mechanics with
   `playbook/11-language-mapping.md`; the practices never change.
4. **Doubt a rule:** check its Source citation in the playbook doc, then
   `playbook/case-study-thinkrail.md` for the raw evidence.
5. **Learned a refinement:** bring it back here as a playbook change — the loop closes
   ([[playbook-applying]], step 8).

## Credits

Patterns distilled from [JetBrains/thinkrail](https://github.com/JetBrains/thinkrail)
(Apache-2.0). Short quotes are cited to their source files for study purposes.

## License

[MIT](LICENSE) — copy the templates freely; attribution appreciated but not required.
