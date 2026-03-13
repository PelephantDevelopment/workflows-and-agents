---
name: hauptaufgabe
description: >
  HIER ANPASSEN: Wann soll dieser Skill aktiviert werden?
  Sei konkret – Claude liest diesen Text und entscheidet ob der Skill passt.

  Beispiele:
  - "Aktiviert sich wenn Verträge analysiert werden sollen"
  - "Aktiviert sich wenn Dateien sortiert oder organisiert werden sollen"
  - "Aktiviert sich bei Fragen zu Datenschutz und Compliance"
---

# HIER: Titel deines Haupt-Skills

<!--
╔══════════════════════════════════════════════════════════════════╗
║  SKILL 1: HAUPTAUFGABE                                         ║
║                                                                 ║
║  Dies ist die Kernfähigkeit deines Agents – die Hauptaufgabe.   ║
║                                                                 ║
║  Dieser Skill wird genutzt von:                                 ║
║  → dem Command "ausfuehren" (commands/ausfuehren/COMMAND.md)    ║
║  → dem Sub-Agent "helfer-agent" (agents/helfer-agent.md)        ║
║                                                                 ║
║  Dieser Skill ruft auf:                                         ║
║  → den Sub-Agent "helfer-agent" für Teilaufgaben                ║
║                                                                 ║
║  Passe ALLES mit "HIER" an. Lösche die Kommentare am Ende.     ║
╚══════════════════════════════════════════════════════════════════╝
-->

## Deine Rolle

<!-- Wer ist Claude in diesem Kontext? -->

Du bist ein HIER ROLLE BESCHREIBEN.

<!--
Beispiele:
- "Du bist ein erfahrener M&A-Anwalt"
- "Du bist ein Compliance-Spezialist für Schweizer Recht"
- "Du bist ein Dokumenten-Manager für eine Anwaltskanzlei"
-->

## Aufgabe

<!-- Was genau soll Claude tun? Schritt für Schritt. -->

Wenn du eine Anfrage zu HIER THEMA erhältst:

### 1. Analyse
HIER: Was wird zuerst gelesen/geprüft?

### 2. Bewertung
HIER: Wie werden die Ergebnisse bewertet?

Nutze folgendes Bewertungsschema:

| Symbol | Bedeutung |
|--------|-----------|
| 🟢 | HIER: Wann grün? (z.B. "OK, marktüblich") |
| 🟡 | HIER: Wann gelb? (z.B. "Achtung, ungewöhnlich") |
| 🔴 | HIER: Wann rot? (z.B. "Risiko, kritisch") |

### 3. Prüf-Checkliste

| # | Prüfpunkt | Worauf achten |
|---|-----------|---------------|
| 1 | HIER | HIER |
| 2 | HIER | HIER |
| 3 | HIER | HIER |
| 4 | HIER | HIER |
| 5 | HIER | HIER |

<!-- Füge so viele Zeilen hinzu wie nötig -->

### 4. Teilaufgabe an Sub-Agent delegieren

Delegiere an den **helfer-agent**: HIER BESCHREIBEN was der Sub-Agent tun soll.

<!--
Der helfer-agent (definiert in agents/helfer-agent.md) übernimmt eine
spezialisierte Teilaufgabe. Er arbeitet unabhängig und liefert die
Ergebnisse an diesen Skill zurück.

Beispiele:
- "Suche relevante Rechtsgrundlagen zu den identifizierten Risiken"
- "Recherchiere Hintergrundinformationen zu den beteiligten Parteien"
- "Prüfe ob es aktuelle Gesetzesänderungen zu diesem Thema gibt"
-->

Baue die Ergebnisse des helfer-agent in deine Analyse ein.

## Ausgabeformat

<!-- Wie soll das Ergebnis aussehen? -->

```markdown
# HIER: Titel der Ausgabe

## Überblick
| Feld | Wert |
|------|------|
| HIER | HIER |
| HIER | HIER |
| **Gesamtbewertung** | 🟢 / 🟡 / 🔴 |

## Detailanalyse
| # | Prüfpunkt | Status | Bemerkung |
|---|-----------|--------|-----------|
| 1 | HIER | 🟢 | HIER |
| 2 | HIER | 🟡 | HIER |

## Ergebnisse vom Sub-Agent
HIER: Was der helfer-agent geliefert hat

## Empfehlungen
1. HIER
2. HIER
3. HIER
```

## Regeln

- HIER: Regel 1 (z.B. "Sprache: Deutsch, Schweizer Rechtschreibung, kein ß")
- HIER: Regel 2 (z.B. "Dies ist keine Rechtsberatung, sondern eine Analyse")
- HIER: Regel 3 (z.B. "Bei Unsicherheit klar kennzeichnen")
- HIER: Regel 4 (z.B. "Vertrauliche Inhalte nicht in Web-Suchen verwenden")
