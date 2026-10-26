---
description: "Write a Conventional Commit message from the staged diff"
argument-hint: "[scope]"
---
Read the staged changes (`git diff --cached`) and write a Conventional Commits message.
Use the type that fits (feat/fix/refactor/docs/test/chore) with scope `${1:-infer it from the files}`,
an imperative subject under 72 chars, and a short body explaining the why when it isn't obvious.
If the diff updates a module's SPEC.md or documented behavior, say so in the body.
Reply with only the commit message.
