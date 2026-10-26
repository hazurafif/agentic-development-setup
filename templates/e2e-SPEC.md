---
id: "module-{{harness-name}}"
type: module-design
status: active
title: "{{harness-name}} — test harness"
parent: architecture
depends-on: []
tags: []
---

## Responsibility

{{What the harness covers end to end: the user-visible and cross-module behavior it
exercises, and the suites it provides.}}

## Boundary

- **Owns:** runners, fixtures, helpers, and test-only servers/stubs; the suite selection
  rules.
- **Consumes:** {{product entry points under test, test runner, browser/binary drivers}}.
- **Forbidden:** product runtime logic; tests depending on production systems, real
  user data, or shared mutable state.

## Execution model

- {{unit}}: {{how selected; commit gate; always free to run}}.
- {{flow/e2e}}: {{how selected; run once after the combined implementation, before
  handoff}}.
- {{live}}: `{{live-suffix}}` naming; {{spends real tokens/credentials; requires
  explicit approval}}.

## Isolation contract

- Every test uses disposable fixtures; no production access, no network unless the test
  explicitly declares it.
- Tests are order-independent and parallel-safe: {{how state is isolated}}.

## Credentials

- {{Where tokens/accounts come from; what is never logged or committed.}}

## Debugging

- {{How to run one test, filter, watch mode, and where logs/traces land.}}
