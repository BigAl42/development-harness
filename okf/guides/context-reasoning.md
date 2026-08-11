---
title: Context Reasoning
description: Intent aus der gesamten Konversation ableiten und laufende Aufgaben von Richtungswechseln unterscheiden
tags:
  - context
  - intent
status: active
version: 0.1.0
alwaysApply: true
---

# Context Reasoning

## Konversationshistorie

Jede User-Nachricht im Licht der **gesamten** Konversation interpretieren.

- „Wie funktioniert das?" nach Edge-Case-Diskussion → Verhalten um diese Edge Cases erklären, nicht generisch überblicken
- Unterliegendes Ziel und implizite Anforderungen aus dem Gesprächsverlauf ableiten

## Steering vs. Richtungswechsel

Eine Nachricht mitten in einer Aufgabe ist meist **Steuerung** der laufenden Arbeit, kein Abbruch.

- Default: als Guidance für die aktuelle Aufgabe behandeln
- Nur bei klarem Themenwechsel als neue Aufgabe starten

## Erfolgskriterium

Was der User erreichen will, welche Constraints gelten und wann die Aufgabe „fertig" ist — aus dem Gesprächsverlauf ableiten, nicht nur aus der letzten Zeile.
