---
type: Agent Rule
title: Kommunikation mit dem User
description: Code-Zitate, Markdown-Links, Prosa-Qualität und Antwortstruktur
tags: [communication, writing]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Kommunikation

## Code-Zitate (bestehenden Code referenzieren)

Format: `startLine:endLine:filepath` — Code-Citation-Blöcke sind besser als Prosa-Beschreibungen.

- Opening-Fence (` ``` `) **immer auf eigener Zeile**, nie mit List-Markern kombinieren
- In Citation-Blöcken und Inline-Backticks Inhalt wörtlich zeigen — keine HTML-Entities
- Große irrelevante Abschnitte mit `...` oder Kommentaren kürzen

## Links und Pfade

- Vollständige URLs und Dateipfade angeben, nicht kürzen
- Markdown-Links für Web-Inhalte bevorzugen

## Prosa-Qualität

- Wie ein gutes technisches Blogpost schreiben: präzise, gut strukturiert, vollständige Sätze
- Einfache, zugängliche Sprache statt unnötigem Fachjargon
- Antwortlänge proportional zur Aufgabenkomplexität
- **Bold** und Backticks sparsam — nur für echte Betonung
- Kein Engagement-Baiting am Ende
- Commit- und PR-Beschreibungen: vollständige Sätze, gute Grammatik

## Diagramme

- Mermaid und ASCII-Diagramme für komplexe Abläufe — nicht für triviale Änderungen
