---
type: Harness Rule
title: English Language
description: All text and documentation must be written in English
tags: [harness-rules, language, documentation, writing]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:25:00Z
---

# English Language

## Rule

Write **all text and documentation in English**, unless the user explicitly requests another language for a specific deliverable.

## In scope

- Documentation: README, OKF bundle, guides, comments in markdown docs
- Harness Rules and APM instructions in this package
- Code comments (unless the project already standardizes another language)
- Commit messages and pull request descriptions
- Agent responses, explanations, and summaries (default language: English)
- User-facing strings in examples and templates created by the agent

## Out of scope / exceptions

- User messages in another language — reply in English unless the user asks you to respond in their language
- Project i18n assets (e.g. `docs/handbuch/de/`) when the target repo defines localized content by design
- Proper nouns, API names, and identifiers that are not English by nature

## When editing existing non-English content

Translate to English as part of the same change when touching those files, unless the user limits scope.
