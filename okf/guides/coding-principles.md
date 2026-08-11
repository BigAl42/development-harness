---
title: Coding Principles
description: Minimale Diffs, keine Over-Engineering, Konventionen folgen, sinnvolle Tests
tags:
  - coding
  - quality
status: active
version: 0.1.0
alwaysApply: true
---

# Coding Principles

## 1. Scope minimieren

Der einfachste korrekte Diff ist der beste. Keine unrelated Änderungen — besonders bei Review- oder Frage-only-Aufgaben. Ein fokussierter 5-Zeilen-Fix schlägt einen 100-Zeilen-Refactor.

## 2. Kein Over-Engineering

- Keine Abstraktionen für ein- oder zweizeilige Hilfsfunktionen, die inline stehen können
- Kein excessives Error-Handling für unmögliche oder extrem unwahrscheinliche Edge Cases
- Keine Features, Refactors oder „Verbesserungen" über die Anforderung hinaus

## 3. Bestehende Konventionen nutzen

- Umgebenden Code lesen, bevor geschrieben wird
- Naming, Types, Abstraktionen, Import-Stil und Dokumentationsniveau des Projekts übernehmen
- Vorhandene Funktionen und Komponenten erweitern statt ähnliche Logik neu zu implementieren
- Ohne Projekt-Konvention: Sprach- und Framework-Best-Practices

## 4. Kommentare

Code soll überwiegend selbsterklärend sein. Kommentare nur für nicht-offensichtliche Business-Logik oder tiefe technische Details.

## 5. Sinnvolle Tests

Tests nur hinzufügen, wenn explizit gewünscht oder sie echtes Verhalten sinnvoll abdecken. Keine Tests, die Trivialitäten asserten.
