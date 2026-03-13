---
name: zusammenfassung
description: >
  Erstellt eine kurze Management-Zusammenfassung basierend auf einer
  Vertragsanalyse. Aktiviert sich nach einer Vertragsanalyse oder wenn
  der Nutzer eine Zusammenfassung, ein Executive Summary oder eine
  Entscheidungsvorlage zu einem Vertrag anfordert. Nutzt die Ergebnisse
  des Skills "vertragsanalyse" als Grundlage.
---

# Management-Zusammenfassung erstellen

Du erstellst eine knappe, entscheidungsorientierte Zusammenfassung für Partner oder Mandanten, basierend auf der detaillierten Vertragsanalyse aus dem Skill «vertragsanalyse».

## Voraussetzung

Dieser Skill nutzt die **Ergebnisse der Vertragsanalyse** (Skill «vertragsanalyse»). Falls noch keine Analyse vorliegt, führe zuerst die Vertragsanalyse durch.

## Vorgehen

### 1. Ergebnisse der Vertragsanalyse lesen
- Übernimm die Klausel-Bewertungen (🟢🟡🔴)
- Übernimm die identifizierten Risiken
- Übernimm die fehlenden Klauseln
- Übernimm die Rechtsgrundlagen vom Recherche-Agent

### 2. Zusammenfassung erstellen
- Maximal **1 Seite** (ca. 300 Wörter)
- Sprache: klar, knapp, entscheidungsorientiert
- Keine juristischen Fachbegriffe ohne Erklärung
- Klare Handlungsempfehlungen mit Priorisierung

### 3. Handlungsempfehlungen formulieren
- Pro Empfehlung: Was tun? Warum? Wie dringend?
- Kategorisiere: **Muss** (vor Unterzeichnung) / **Sollte** (empfohlen) / **Kann** (nice-to-have)

## Ausgabeformat

```markdown
# Zusammenfassung: [Vertragstyp] – [Parteien]

**Gesamtbewertung:** 🟢/🟡/🔴 [Ein Satz]

**Kernpunkte:**
- [Wichtigster positiver Punkt]
- [Wichtigstes Risiko]
- [Wichtigste fehlende Klausel]

**Handlungsempfehlungen:**

| Priorität | Empfehlung | Begründung |
|-----------|------------|------------|
| 🔴 Muss | ... | ... |
| 🟡 Sollte | ... | ... |
| 🟢 Kann | ... | ... |

**Empfehlung:** [Unterzeichnen / Nachverhandeln / Ablehnen] – [Begründung in 1-2 Sätzen]
```

## Regeln

- Maximal 1 Seite – Partner haben keine Zeit für lange Texte
- Immer mit konkreter Empfehlung enden (Unterzeichnen / Nachverhandeln / Ablehnen)
- Sprache: Deutsch (Schweizer Rechtschreibung, kein ß)
- Dies ist keine Rechtsberatung, sondern eine strukturierte Entscheidungsgrundlage
