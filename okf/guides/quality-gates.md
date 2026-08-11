---
type: Agent Rule
title: Quality Gates vor Commit
description: Tests und Builds müssen vor dem Commit grün sein — generalisiertes Template
tags: [testing, ci, commit]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
sources:
  - id: event-pos-tests-vor-commit
    resource: /event-pos-desktop/.cursor/rules/tests-vor-commit.mdc
    title: tests-vor-commit (event-pos-desktop)
---

# Quality Gates vor Commit

Generalisierte Regel aus event-pos-desktop. Konkrete Befehle im Ziel-Repo anpassen.

## Tests

- Vor Commit alle relevanten Tests erfolgreich
- Projekt-Test-Kommando verwenden (`npm test`, `cargo test`, etc.)

## Build

- Produktions-/Release-Build mindestens einmal erfolgreich bei build-relevanten Änderungen

## Pre-Commit-Hooks

- Hooks respektieren; in CI ggf. deaktiviert

## Neue Features

- Passende Test-Abdeckung; Build-Änderungen verifizieren

**Hinweis:** Konkrete Befehle gehören in projekt-spezifische Rules im Zielprojekt.
