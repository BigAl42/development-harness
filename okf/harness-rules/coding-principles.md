---
type: Harness Rule
title: Coding Principles
description: Minimal diffs, no over-engineering, follow conventions, meaningful tests
tags: [harness-rules, coding, quality]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:09:00Z
---

# Coding Principles

## 1. Minimize scope

Simplest correct diff. No unrelated changes.

## 2. No over-engineering

No helpers for 1–2 lines. No excessive error handling. No unrequested features.

## 3. Conventions

Read surrounding code. Match project naming, types, imports. Extend existing code.

## 4. Comments

Only for non-obvious business logic. Write comments in English (see [English Language](/harness-rules/english-language.md)).

## 5. Tests

Only when requested or when they add meaningful coverage.
