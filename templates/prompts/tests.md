---
description: "Write or update tests for a module, honoring its spec"
argument-hint: "[module or file]"
---
For ${1:-the module in question}: read its SPEC.md first, then the existing tests.

Write or update tests that cover the module's public surface and boundary rules as stated
in the spec — including one test per stated invariant where practical. Do not test
internals beyond the barrel surface, and do not manufacture coverage for a localized
change that the spec does not govern.

Use disposable fixtures with no production access. Report: tests added/changed, spec
invariants now covered, and any invariant you could not cover and why.
