---
description: "Review the current diff against the owning spec and handoff rules"
argument-hint: "[diff range, default: branch vs base]"
---
Review the diff (`${1:-git diff @...HEAD plus uncommitted changes}`) as a handoff review:

1. Does the change move or blur a boundary, contract, or documented behavior? If the
   owning SPEC.md was not updated in the same range, flag it.
2. Subtraction pass: list avoidable abstractions, state owners, compatibility layers, and
   fallbacks the diff added; justify any that remain.
3. Audit new comments and suppressions (`@ts-ignore`, lint disables, `as any`): each needs
   a hazard-level reason or explicit approval.
4. If a replaced pattern still has old occurrences, list them.
5. Check user-facing claims (README) that the diff invalidates.

Report findings as a numbered list with file:line references; say "clean" per section when
nothing is found.
