---
okf_version: "0.2"
---

# BigAl42 Development Harness

Portable **Harness Rules** as an OKF v0.2 bundle. APM derives instructions and deploys to harness targets (Cursor, Copilot, …).

# Concepts

* [Harness Rules — Model](concepts/harness-rules-model.md) - Harness rules vs. project rules vs. deploy targets

# Harness Rules

* [Agent Principles](harness-rules/agent-principles.md) - Foundation of all harness rules
* [English Language](harness-rules/english-language.md) - All text and documentation in English
* [Instruction Following](harness-rules/instruction-following.md) - Follow all instructions completely
* [Rules Precedence](harness-rules/rules-precedence.md) - Conflict order across AGENTS, OKF, and harness
* [Communication](harness-rules/communication.md) - Code citations, prose, links
* [Coding Principles](harness-rules/coding-principles.md) - Scope, conventions, tests
* [Context Reasoning](harness-rules/context-reasoning.md) - Intent from conversation history
* [Session and Tenant Empty State](harness-rules/session-tenant-empty-state.md) - Error vs empty tenancy; no fake first-run
* [Quality Gates](harness-rules/quality-gates.md) - Tests/build/optional OKF before commit (template)

# Guides

* [Applying OKF v0.2](guides/okf-v0.2-application.md) - OKF spec + harness rules workflow
* [OKF Consume and Maintain](guides/okf-consume-and-maintain.md) - Read/update in-repo project OKF
* [OKF Changelog](guides/okf-changelog-log.md) - Maintaining `okf/log.md`
* [OKF Baseline Capture](guides/okf-baseline-capture.md) - Bootstrap project OKF
* [OKF Update After Architecture Change](guides/okf-update-after-architecture-change.md) - Post-change checklist
* [Rule Layering](guides/rule-layering.md) - Pattern A (overview) vs Pattern B (OKF + AGENTS)

# Reference

* [Harness Deployment](reference/harness-deployment.md) - OKF → APM → targets
* [OKF → APM Mapping](reference/apm-mapping.md) - File mapping
* [OKF v0.2 In-Repo Layout](reference/okf-v0.2-in-repo-layout.md) - Project domain catalog layout
* [OKF Bundle Checklist](reference/validators/okf-bundle-checklist.md) - Validator checklist
* [Health Check Tiers](reference/health-check-tiers-ietf.md) - Liveness vs readiness
* [Pre-Deploy Data Snapshot](reference/pre-deploy-data-snapshot.md) - Backup gate before risky deploys
* [Templates](reference/templates/AGENTS-hard-rules.md) - AGENTS.md, OKF cursor rule, push opt-in
* [Extractions](reference/extractions/README.md) - Learnings from consumer projects
