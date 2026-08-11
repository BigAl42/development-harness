---
name: okf-rules
description: Apply when loading, authoring, or syncing OKF v0.2 knowledge bundles. Use when setting up agent context, writing OKF concepts, reviewing conformance, or mirroring OKF to APM instructions.
---

# OKF Rules Skill

Lädt und wendet übergreifende Regeln aus dem **OKF-v0.2**-Bundle `okf/` an.

## When to Use

- Agent-Kontext einrichten oder Regeln konsumieren
- OKF-Concepts schreiben oder migrieren (v0.2-Konformität)
- OKF-Quelldateien mit `.apm/instructions/` synchron halten
- Consumer-Projekt mit `BigAl42/development-harness` verbinden

## OKF v0.2 (Pflicht)

Vor jeder OKF-Änderung: [OKF v0.2 anwenden](/okf/guides/okf-v0.2-application.md) lesen.

- Jedes Concept braucht `type` im Frontmatter
- Bundle deklariert `okf_version: "0.2"` in `okf/index.md`
- Trust-Felder nutzen: `generated`, `verified`, `status`, `sources`

## Struktur

```
okf/
├── index.md              # okf_version: "0.2"
├── log.md
├── concepts/
├── guides/
└── reference/
```

## Workflow

1. `okf/index.md` → Version prüfen
2. Relevante Concepts laden (Trust-Signale beachten)
3. Bei Änderungen: OKF zuerst → `.apm/instructions/` → `apm install`
4. Mapping: `okf/reference/apm-mapping.md`

## Spec

https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md
