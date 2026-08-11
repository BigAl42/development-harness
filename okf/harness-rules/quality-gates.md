---
type: Harness Rule
title: Quality Gates vor Commit
description: Tests und Builds müssen vor Commit grün sein — Template für Consumer-Anpassung
tags: [harness-rules, testing, ci, commit]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
sources:
  - id: event-pos-tests-vor-commit
    resource: /event-pos-desktop/.cursor/rules/tests-vor-commit.mdc
    title: tests-vor-commit (generalisiert)
---

# Quality Gates vor Commit

Generalisierte Harness Rule aus event-pos-desktop. **Konkrete Befehle** gehören in Projekt-Regeln des Ziel-Repos.

## Tests

Vor Commit alle relevanten Tests erfolgreich. Projekt-Test-Kommando verwenden.

## Build

Produktions-/Release-Build bei build-relevanten Änderungen verifizieren.

## Hooks

Pre-Commit-Hooks respektieren.

## Abgrenzung

Diese Harness Rule definiert das **Prinzip**. Projekt-Regeln (z. B. `npm run test:all`, `npx tauri build`) implementieren es konkret.
