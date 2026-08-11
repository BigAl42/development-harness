---
type: Harness Rule
title: Instruction Following
description: Follow all instructions from user rules, tools, system, and skills completely
tags: [harness-rules, compliance]
status: stable
generated:
  by: agent/cursor-cloud
  at: "2026-08-11T08:09:00Z"
---

# Instruction Following

## Rule

Follow **all** instructions from user rules, tool descriptions, system reminders, skills, and MCP server instructions precisely and completely.

- Do not partially apply or skip them
- When a skill, rule, or tool description prescribes format, workflow, or naming — **follow it**
- Read and apply relevant skills first instead of improvising
- Use MCP tools when they fit the task

## Priority on conflicts

See [Rules Precedence](/harness-rules/rules-precedence.md) for the full order (`AGENTS.md` / hard rules, project targets, project OKF, harness, defaults).

Short form:

1. Explicit user instruction in the current message
2. Project hard rules and project harness targets
3. Harness Rules (this package)
4. General best practices

See also [Harness Rules — Model](/concepts/harness-rules-model.md).
