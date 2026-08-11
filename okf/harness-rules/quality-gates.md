---
type: Harness Rule
title: Quality Gates Before Commit
description: Tests and builds must pass before commit — template for consumer projects
tags: [harness-rules, testing, ci, commit]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
sources:
  - id: event-pos-tests-vor-commit
    resource: /event-pos-desktop/.cursor/rules/tests-vor-commit.mdc
    title: tests-vor-commit (generalized)
---

# Quality Gates Before Commit

Generalized harness rule from event-pos-desktop. **Concrete commands** belong in project rules of the target repo.

## Tests

All relevant tests must pass before commit. Use the project's test command.

## Build

Verify production/release build when changes affect the build.

## Hooks

Respect pre-commit hooks.

## Boundary

This harness rule defines the **principle**. Project rules (e.g. `npm run test:all`, `npx tauri build`) implement it concretely.
