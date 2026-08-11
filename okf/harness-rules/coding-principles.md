---
type: Harness Rule
title: Coding Principles
description: Minimale Diffs, keine Over-Engineering, Konventionen folgen, sinnvolle Tests
tags: [harness-rules, coding, quality]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Coding Principles

## 1. Scope minimieren

Einfachster korrekter Diff. Keine unrelated Änderungen.

## 2. Kein Over-Engineering

Keine Hilfsfunktionen für 1–2 Zeilen. Kein excessives Error-Handling. Keine ungefragten Features.

## 3. Konventionen

Umgebenden Code lesen. Naming, Types, Imports des Projekts übernehmen. Vorhandenes erweitern.

## 4. Kommentare

Nur für nicht-offensichtliche Business-Logik.

## 5. Tests

Nur wenn gewünscht oder sinnvolle Abdeckung.
