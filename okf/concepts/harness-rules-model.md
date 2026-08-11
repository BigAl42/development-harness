---
type: Reference
title: Harness Rules — Modell
description: Was Harness Rules sind, wie sie sich von Projekt-Regeln und Harness-Deploy-Targets unterscheiden
tags: [harness-rules, architecture, okf]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:20:00Z
---

# Harness Rules — Modell

## Drei Ebenen

```
┌─────────────────────────────────────────────────────────┐
│  1. Harness Rules (OKF)     okf/harness-rules/*.md      │
│     Portable, harness-agnostisch, versioniert           │
│     type: Harness Rule                                  │
└──────────────────────────┬──────────────────────────────┘
                           │ abgeleitet / gespiegelt
┌──────────────────────────▼──────────────────────────────┐
│  2. APM Instructions        .apm/instructions/*.md      │
│     Deploy-Primitive für alle Harnesses                 │
└──────────────────────────┬──────────────────────────────┘
                           │ apm install (pro Target)
┌──────────────────────────▼──────────────────────────────┐
│  3. Harness-Targets (generiert, nicht Source of Truth)   │
│     Cursor:  .cursor/rules/*.mdc                         │
│     Copilot: .github/instructions/                       │
│     Agents:  .agents/skills/                             │
└──────────────────────────────────────────────────────────┘
```

## Harness Rule vs. Projekt-Regel

| | Harness Rule | Projekt-Regel |
|---|--------------|---------------|
| **Gültigkeit** | Übergreifend, alle Projekte | Ein Repo / Domäne |
| **Ort** | `development-harness/okf/harness-rules/` | Zielprojekt (z. B. `.cursor/rules/`) |
| **Beispiel** | Coding Principles, Kommunikation | Kassensystem-Views, Tauri-Build |
| **Distribution** | APM-Package | Lokal im Projekt |

## Harness Rule vs. Cursor Rule

Eine **Cursor Rule** (`.mdc`) ist ein **Deploy-Target**, keine Definition.

- Definition: `okf/harness-rules/<name>.md` (OKF v0.2, `type: Harness Rule`)
- Ableitung: `.apm/instructions/<name>.instructions.md`
- Deploy: `apm install` schreibt `.cursor/rules/<name>.mdc` (nur wenn Cursor Target aktiv)

**Niemals** Harness Rules direkt als `.cursor/rules/` pflegen — das wäre Harness-spezifisch und nicht portabel.

## Priorität beim Konsum

1. Explizite User-Anweisung
2. Projekt-Regeln im Ziel-Repo
3. Harness Rules (dieses Package)
4. Allgemeine Best Practices

## Bezug

- [Harness Deployment](/reference/harness-deployment.md)
- [OKF v0.2 anwenden](/guides/okf-v0.2-application.md)
