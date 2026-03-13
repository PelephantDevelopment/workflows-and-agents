---
name: ausgabe-erstellen
description: >
  HIER ANPASSEN: Wann soll dieser Skill aktiviert werden?

  Beispiele:
  - "Erstellt eine Zusammenfassung nach einer Analyse"
  - "Erstellt ein Dokument basierend auf den Ergebnissen"
  - "Erstellt eine Übersicht / Inventarliste / Report"
---

# HIER: Titel deines Ausgabe-Skills

<!--
╔══════════════════════════════════════════════════════════════════╗
║  SKILL 2: AUSGABE ERSTELLEN                                    ║
║                                                                 ║
║  Dieser Skill erstellt das Endergebnis. Er nutzt:               ║
║  → die Ergebnisse von Skill 1 (skills/hauptaufgabe/SKILL.md)   ║
║  → die Ergebnisse des helfer-agent (agents/helfer-agent.md)     ║
║                                                                 ║
║  Dieser Skill wird aufgerufen von:                              ║
║  → dem Command "ausfuehren" (als letzter Schritt)               ║
║  → oder automatisch, wenn jemand eine Zusammenfassung will      ║
╚══════════════════════════════════════════════════════════════════╝
-->

## Voraussetzung

Dieser Skill nutzt die **Ergebnisse aus dem Skill «hauptaufgabe»** und die **Recherche-Ergebnisse des «helfer-agent»**. Falls diese noch nicht vorliegen, führe zuerst den Skill «hauptaufgabe» durch.

## Aufgabe

HIER: Was genau soll erstellt werden?

<!--
Beispiele:
- "Erstelle eine 1-seitige Management-Zusammenfassung"
- "Erstelle eine Excel-Übersicht aller Ergebnisse"
- "Erstelle ein Word-Dokument als Entscheidungsvorlage"
- "Erstelle eine Inventarliste als Markdown"
-->

## Vorgehen

### 1. Ergebnisse zusammentragen
- Übernimm die Bewertungen aus Skill «hauptaufgabe» (🟢🟡🔴)
- Übernimm die Ergebnisse des «helfer-agent»
- HIER: Was noch?

### 2. Ausgabe erstellen
- HIER: Welches Format? (Markdown, Word, Excel, PDF?)
- HIER: Wie lang? (z.B. "Maximal 1 Seite")
- HIER: Welcher Stil? (z.B. "Knapp und entscheidungsorientiert")

### 3. Empfehlung formulieren
- HIER: Was soll die Schlussempfehlung enthalten?

<!--
Beispiele:
- "Unterzeichnen / Nachverhandeln / Ablehnen"
- "Priorisierte To-Do-Liste: Muss / Sollte / Kann"
- "Risiko-Score: 1–10 mit Begründung"
-->

## Ausgabeformat

```markdown
# HIER: Titel

**Gesamtbewertung:** 🟢 / 🟡 / 🔴 – HIER ein Satz

**Kernpunkte:**
- HIER
- HIER
- HIER

**Empfehlungen:**

| Priorität | Empfehlung | Begründung |
|-----------|------------|------------|
| 🔴 HIER | HIER | HIER |
| 🟡 HIER | HIER | HIER |
| 🟢 HIER | HIER | HIER |

**Schlussempfehlung:** HIER
```

## Regeln

- HIER: Regel 1 (z.B. "Maximal 1 Seite")
- HIER: Regel 2 (z.B. "Immer mit konkreter Empfehlung enden")
- HIER: Regel 3 (z.B. "Sprache: Deutsch, Schweizer Rechtschreibung")
