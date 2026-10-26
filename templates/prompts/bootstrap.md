---
description: "Bootstrap this repo with the agentic development pattern from the know-how repo"
argument-hint: "[path to know-how repo]"
---
Set up this repository with the agentic development pattern, using the templates in
`${1:-~/agentic-development-setup}/templates/`.

1. Copy `AGENTS.md`, `goal-and-requirements.md`, and `architecture.md` from that
   templates directory into this repo root, and `prompts/*.md` into `.pi/prompts/`.
2. Before filling anything, ask me for: the project's one-paragraph goal, the problem it
   solves, who it is for, its value in one line, 2-4 durable principles, current
   capabilities, explicit non-goals, and the stack (language, runtime, test runner,
   boundary-lint tool if any). Fill `goal-and-requirements.md` from my answers —
   not from guesses.
3. Fill `AGENTS.md` and `architecture.md` consistently with those answers. In
   `architecture.md`, record Decision #1 only if a real structural choice was made;
   otherwise leave the Decisions section with the template example removed and a note
   that decisions land as they are made.
4. Do not copy the playbook, case study, or any file referencing the know-how repo into
   this repo. The copied docs must be fully self-contained.
5. Stage the files and reply with one proposed Conventional Commit message
   (`docs: bootstrap ...`). Do not commit until I approve.
6. After I approve, propose the next two scaffold steps and wait: record the stack as
   `architecture.md` Decision #1, then scaffold the first module folder with its
   `SPEC.md`. Create neither until I ask.
