---
title: Quality Gates vor Commit
description: Tests und Builds müssen vor dem Commit grün sein — generalisiert aus Projekt-Praxis
tags:
  - testing
  - ci
  - commit
status: active
version: 0.1.0
---

# Quality Gates vor Commit

Generalisierte Regel aus der event-pos-desktop-Praxis (`tests-vor-commit`). Projekt-spezifische Befehle im Ziel-Repo anpassen.

## Tests

- **Vor jedem Commit müssen alle relevanten Tests erfolgreich durchlaufen**
- Nicht committen, wenn Tests fehlschlagen oder übersprungen werden, um einen Commit zu erzwingen
- Das projektübliche Test-Kommando verwenden (z. B. `npm test`, `npm run test:all`, `cargo test`, `pytest`)

## Build

- Zusätzlich zu Tests muss ein **Produktions- oder Release-Build** mindestens einmal erfolgreich sein, bevor Änderungen als commit-fertig gelten
- Build-Fehler (TypeScript, Bundler, Linker, Compiler) sind zu beheben — nicht zu ignorieren
- Bei Full-Stack- oder Desktop-Apps: Frontend-Build **und** Backend/Native-Build verifizieren, wenn beide betroffen sind

## Pre-Commit-Hooks

- Wenn Husky oder andere Hooks vorhanden sind: deren Verhalten respektieren
- In CI-Umgebungen kann Hook-Deaktivierung (`HUSKY=0` o. Ä.) vorgesehen sein — die Pipeline übernimmt dann die Checks

## Neue Funktionalität

- Neue oder geänderte Features durch passende Tests abdecken
- Build-relevante Änderungen (Dependencies, Config, Toolchain) durch Build-Schritte verifizieren

## Projekt-Anpassung

Diese OKF-Regel ist ein **Template**. Konkrete Befehle gehören in projekt-spezifische Cursor Rules oder APM-Instructions im Ziel-Repo.
