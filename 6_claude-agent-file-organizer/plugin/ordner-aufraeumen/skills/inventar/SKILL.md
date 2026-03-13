---
name: inventar
description: >
  Erstellt eine strukturierte Inventarliste aller Dateien in einem Ordner.
  Aktiviert sich nach einer Sortierung, oder wenn der Nutzer eine Übersicht,
  ein Inventar oder eine Bestandsaufnahme eines Ordners anfordert.
  Nutzt die Ergebnisse des Skills «datei-sortierung» als Grundlage.
---

# Inventarliste erstellen

Du erstellst eine vollständige, strukturierte Inventarliste aller Dateien in einem Ordner. Dieser Skill wird typischerweise nach dem Skill «datei-sortierung» aufgerufen und nutzt dessen Ergebnisse.

## Voraussetzung

Falls bereits eine Sortierung durch den Skill «datei-sortierung» stattgefunden hat, nutze dessen Ergebnisse. Falls nicht, lies selbst alle Dateien und erstelle die Inventarliste ohne vorherige Sortierung.

## Vorgehen

### 1. Daten sammeln
- Übernimm die Zuordnungen aus dem Skill «datei-sortierung» (falls vorhanden)
- Oder: Lies selbst den Inhalt jeder Datei
- Erfasse: Originaler Name, neuer Name/Pfad, Kategorie, Sprache, Datum, Kurzbeschreibung

### 2. Inventar-Datei erstellen

Erstelle die Datei `00_INVENTAR.md` im Hauptordner.

### 3. Warnungen identifizieren
- ⚠ VERTRAULICH: Dokumente mit Hinweisen auf Vertraulichkeit
- 📝 ENTWURF: Dokumente die als Entwurf erkennbar sind
- ⚠ SICHERHEITSRISIKO: Passwort-Dateien, unverschlüsselte Zugangsdaten
- ❓ UNKLAR: Dokumente die nicht eindeutig kategorisiert werden konnten

## Ausgabeformat

```markdown
# Inventar – Sortierung vom [Datum]

## Zusammenfassung

| Kategorie | Anzahl |
|-----------|--------|
| 01 Verträge | X |
| 02 Urteile | X |
| 03 Fachartikel | X |
| 04 Korrespondenz | X |
| 05 Rechnungen | X |
| 06 Präsentationen | X |
| 07 Personal | X |
| 08 Sonstiges | X |
| **Total** | **X** |

## Detailliste

| # | Originaler Name | Neuer Pfad | Sprache | Beschreibung |
|---|----------------|------------|---------|-------------|
| 1 | ... | 01_Vertraege/... | DE | ... |
| 2 | ... | 02_Urteile/... | DE | ... |
| ... | | | | |

## Warnungen

- ⚠ VERTRAULICH: [Datei] – [Grund]
- 📝 ENTWURF: [Datei] – [Grund]
- ⚠ SICHERHEITSRISIKO: [Datei] – [Grund]

## Statistik

- Sprachen: X Deutsch, X Französisch, X Englisch
- Zeitraum: [ältestes Dokument] bis [neuestes Dokument]
- Sortiert am: [Datum und Uhrzeit]
```

## Regeln

- Jede Datei muss in der Liste erscheinen – keine auslassen
- Beschreibung: maximal 1 Satz pro Datei
- Sprache: Deutsch (Schweizer Rechtschreibung, kein ß)
