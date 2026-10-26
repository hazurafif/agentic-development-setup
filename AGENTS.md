# Agentic Development Setup

Personal know-how base for agentic software development: the distilled pattern of how
agent-first repositories structure goal docs, spec graphs, module boundaries, commit
discipline, and verification. Primary case study:
[JetBrains/thinkrail](https://github.com/JetBrains/thinkrail).

This repo practices the pattern it documents: docs carry frontmatter, cross-reference
through `[[wiki-links]]`, and this file routes instead of explaining.

## Read context proportionally

- For what this repo is and is not, read `goal-and-requirements.md`.
- For how the repo is organized and why, read `architecture.md`.
- For a specific practice — context routing, specs, doc formats, boundaries, commits,
  the working loop — read the numbered doc in `playbook/` that covers it.
- For the concrete evidence the patterns were distilled from, read
  `playbook/case-study-thinkrail.md`.
- To apply the pattern in another project, copy from `templates/`; never retype from prose.

## Updating the know-how

- A new pattern or refinement goes into exactly one numbered playbook doc; cross-link
  instead of restating. If two docs would repeat a rule, move it to the more general doc.
- Every normative rule cites its source (repo + path) so it can be re-verified when the
  source evolves.
- Boundary: this repo documents and provides templates. It does not host exercise
  projects or generated scaffolds ([[playbook-spec]]).
- Keep docs concise: rules and rationale, not narrative about how a pattern was learned.

## Conventions

- Conventional Commits with a scope (`docs(specs): ...`); imperative subject; body
  explains the why when it is not obvious.
- Markdown docs carry YAML frontmatter (`id`, `type`, `status`, `title`, `parent`,
  `covers`, `tags`) and `[[wiki-links]]`, mirroring the thinkrail spec-graph style.
