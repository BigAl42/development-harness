---
type: Playbook
title: OKF v0.2 anwenden
description: Verbindliche Regeln zum Erstellen, Pflegen und Konsumieren von OKF-v0.2-konformen Knowledge Bundles in diesem Harness.
tags: [okf, spec, authoring, conformance]
status: stable
generated:
  by: agent/cursor-cloud
  at: 2026-08-11T08:15:00Z
sources:
  - id: okf-spec-v0.2
    resource: https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md
    title: Open Knowledge Format v0.2 Specification
    author: team:gcp-knowledge-catalog
---

# OKF v0.2 anwenden

Dieses Bundle **targetiert OKF Version 0.2**. Jeder Agent, der Regeln schreibt, migriert oder konsumiert, hält sich an diese Playbook-Regeln.

## Konformität (Pflicht)

Ein Bundle ist OKF-v0.2-konform, wenn:

1. Jede nicht-reservierte `.md`-Datei parsebares YAML-Frontmatter hat
2. Jedes Frontmatter ein **nicht-leeres `type`-Feld** enthält — das ist das einzige immer Pflichtfeld
3. Reservierte Dateinamen (`index.md`, `log.md`) der Spezifikation folgen

Reservierte Dateinamen dürfen **keine** Concept-Dokumente sein.

## Bundle-Struktur

```
okf/
├── index.md              # okf_version: "0.2"
├── log.md
├── harness-rules/        # Harness Rules (type: Harness Rule) — SOURCE OF TRUTH
├── concepts/             # Modell, Architektur
├── guides/               # Playbooks (OKF-Authoring, Meta)
└── reference/            # Deployment-Mapping, Spec-Hinweise
```

Harness Rules sind **harness-agnostisch**. `.cursor/rules/` und ähnliche Pfade sind nur generierte Deploy-Targets — siehe [Harness Rules — Modell](/concepts/harness-rules-model.md).

## Frontmatter-Felder (v0.2)

| Feld | Pflicht | Verwendung |
|------|---------|------------|
| `type` | **ja** | z. B. `Harness Rule`, `Playbook`, `Reference` |
| `title` | empfohlen | Anzeigename |
| `description` | empfohlen | Ein Satz für Index und Suche |
| `tags` | optional | Querschnitts-Kategorien |
| `status` | optional | `draft` \| `stable` \| `deprecated` (Default: stable) |
| `generated` | optional | `{ by: <actor>, at: <ISO-8601> }` |
| `verified` | optional | Liste von `{ by, at }` — Trust-Signal |
| `sources` | optional | Provenance mit `resource`, optional `id`, `author` |
| `stale_after` | optional | `YYYY-MM-DD` — absolute Stale-Grenze |

Unbekannte Keys **beibehalten**, nicht verwerfen.

## Actor-Konvention

- `human:<name>` — menschlich autorisiert/bestätigt
- `agent/<name>` oder `tool/<name>` — Agent/Tool erzeugt
- `process:<name>` — automatisierter Prozess

Trust-Tier aus `verified` ableiten: unverified → machine-confirmed → human-reviewed.

## Cross-Links

Bundle-relative Links: `[Titel](/harness-rules/coding-principles.md)`.

## Authoring-Workflow (dieses Repo)

1. **Harness Rule** in `okf/harness-rules/` anlegen/ändern (`type: Harness Rule`)
2. Frontmatter prüfen — mindestens `type`; bei Agent-Content `generated` setzen
3. `okf/index.md` und `okf/log.md` aktualisieren
4. `.apm/instructions/` spiegeln (`harnessRule` + `source` im Frontmatter)
5. `apm install` — generiert Harness-Targets; **nicht** `.cursor/rules/` manuell editieren

## Konsum-Workflow (Agent)

1. Bundle-Root `okf/index.md` lesen → `okf_version` prüfen
2. Relevante Concepts per `type`, `tags` oder Index laden
3. Trust-Signale (`verified`, `stale_after`, `status`) vor Anwendung beachten
4. Bei Widerspruch: User > Projekt-Regeln > Harness Rules > Best Practices

## Was nicht in OKF gehört

- Harness-spezifische Deploy-Pfade (`.cursor/rules/`, `.agents/skills/`) — das ist APM-Schicht
- Projekt-spezifische Befehle (npm, cargo) — gehören ins Zielprojekt, nicht ins übergreifende Bundle

## Spec-Referenz

Vollständige Norm: [OKF v0.2 SPEC](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
