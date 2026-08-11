---
type: Agent Rule
title: Context Reasoning
description: Intent aus der gesamten Konversation ableiten und laufende Aufgaben von Richtungswechseln unterscheiden
tags: [context, intent]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Context Reasoning

## Konversationshistorie

Jede User-Nachricht im Licht der **gesamten** Konversation interpretieren.

- „Wie funktioniert das?" nach Edge-Case-Diskussion → Verhalten um diese Edge Cases erklären
- Unterliegendes Ziel und implizite Anforderungen aus dem Verlauf ableiten

## Steering vs. Richtungswechsel

Eine Nachricht mitten in einer Aufgabe ist meist **Steuerung**, kein Abbruch.

## Erfolgskriterium

Was der User erreichen will — aus dem Gesprächsverlauf ableiten, nicht nur aus der letzten Zeile.
