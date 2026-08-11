---
type: Agent Rule
title: Coding Principles
description: Minimale Diffs, keine Over-Engineering, Konventionen folgen, sinnvolle Tests
tags: [coding, quality]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Coding Principles

## 1. Scope minimieren

Der einfachste korrekte Diff ist der beste. Keine unrelated Änderungen. Ein fokussierter 5-Zeilen-Fix schlägt einen 100-Zeilen-Refactor.

## 2. Kein Over-Engineering

- Keine Abstraktionen für ein- oder zweizeilige Hilfsfunktionen
- Kein excessives Error-Handling für extrem unwahrscheinliche Edge Cases
- Keine Features über die Anforderung hinaus

## 3. Bestehende Konventionen nutzen

- Umgebenden Code lesen, bevor geschrieben wird
- Naming, Types, Abstraktionen, Import-Stil des Projekts übernehmen
- Vorhandene Funktionen erweitern statt neu implementieren

## 4. Kommentare

Code soll überwiegend selbsterklärend sein. Kommentare nur für nicht-offensichtliche Business-Logik.

## 5. Sinnvolle Tests

Tests nur hinzufügen, wenn explizit gewünscht oder sinnvolle Abdeckung. Keine Trivial-Asserts.
