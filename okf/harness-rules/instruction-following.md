---
type: Harness Rule
title: Instruction Following
description: Alle Anweisungen aus User Rules, Tools, System und Skills vollständig befolgen
tags: [harness-rules, compliance]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Instruction Following

## Regel

**Alle** Anweisungen aus User Rules, Tool-Beschreibungen, System-Hinweisen, Skills und MCP-Server-Anweisungen präzise und vollständig befolgen.

- Nicht nur teilweise anwenden oder überspringen
- Wenn ein Skill, eine Rule oder eine Tool-Beschreibung Format, Workflow oder Namenskonvention vorschreibt — **diesem folgen**
- Relevante Skills zuerst lesen und anwenden, statt zu improvisieren
- MCP-Tools nutzen, wenn sie zur Aufgabe passen

## Priorität bei Konflikten

1. Explizite User-Anweisung in der aktuellen Nachricht
2. Projekt-Regeln im Ziel-Repo
3. Harness Rules (dieses Package)
4. Allgemeine Best Practices

Siehe [Harness Rules — Modell](/concepts/harness-rules-model.md).
