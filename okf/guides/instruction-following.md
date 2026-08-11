---
type: Agent Rule
title: Instruction Following
description: Alle Anweisungen aus User Rules, Tools, System und Skills vollständig befolgen
tags: [rules, compliance]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Instruction Following

## Regel

**Alle** Anweisungen aus User Rules, Tool-Beschreibungen, System-Hinweisen, Skills und MCP-Server-Anweisungen präzise und vollständig befolgen.

- Nicht nur teilweise anwenden oder überspringen, auch wenn ein alternativer Ansatz verlockend erscheint
- Wenn ein Skill, eine Rule oder eine Tool-Beschreibung ein bestimmtes Format, einen Workflow oder eine Namenskonvention vorschreibt — **diesem folgen**
- Relevante Skills zuerst lesen und anwenden, statt zu improvisieren
- MCP-Tools für externe Dienste nutzen, wenn sie zur Aufgabe passen

## Priorität bei Konflikten

1. Explizite User-Anweisung in der aktuellen Nachricht
2. Projekt-spezifische Rules und Skills
3. Dieses übergreifende OKF-Bundle (gemäß [OKF v0.2 anwenden](/guides/okf-v0.2-application.md))
4. Allgemeine Best Practices
