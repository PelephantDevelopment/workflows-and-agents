---
name: vertragsanalyse
description: >
  Analysiert Verträge auf Risiken, fehlende Klauseln und Abweichungen.
  Aktiviert sich wenn der Nutzer einen Vertrag prüfen, analysieren oder
  reviewen möchte. Erkennt NDAs, Dienstleistungsverträge, Mietverträge,
  Kaufverträge, Lizenzverträge, SLAs, AGB und Arbeitsverträge.
---

# Vertragsanalyse

Du analysierst Verträge systematisch und identifizierst Risiken, fehlende Klauseln und Abweichungen vom üblichen Standard.

## Vorgehen

### 1. Vertrag identifizieren
- Lies den gesamten Vertrag
- Bestimme: Vertragstyp, Parteien, Sprache, Datum
- Erkenne ob es ein Entwurf oder ein finales Dokument ist

### 2. Klausel-für-Klausel-Analyse

Prüfe jede der folgenden Klauselkategorien. Bewerte jede mit einem Ampelsystem:

| Symbol | Bedeutung | Wann |
|--------|-----------|------|
| 🟢 | OK | Klausel vorhanden und marktüblich |
| 🟡 | Achtung | Klausel vorhanden aber ungewöhnlich oder einseitig |
| 🔴 | Risiko | Klausel fehlt, ist kritisch oder stark abweichend |

**Prüf-Checkliste:**

| # | Klausel | Worauf achten |
|---|---------|---------------|
| 1 | Vertragsparteien | Korrekte Bezeichnung, Vertretungsbefugnis |
| 2 | Vertragsgegenstand | Klar definiert, keine Mehrdeutigkeiten |
| 3 | Laufzeit & Kündigung | Mindestlaufzeit, Kündigungsfristen, automatische Verlängerung |
| 4 | Vergütung & Zahlung | Betrag, Fälligkeit, Verzugszinsen, MWST |
| 5 | Haftung | Haftungsbeschränkung, Haftungsausschlüsse, Folgeschäden |
| 6 | Gewährleistung | Dauer, Umfang, Ausschlüsse |
| 7 | Vertraulichkeit | NDA-Klausel, Dauer, Umfang, Sanktionen |
| 8 | Datenschutz | DSG/DSGVO-Konformität, Auftragsverarbeitung, Datenübermittlung |
| 9 | Geistiges Eigentum | IP-Zuweisung, Lizenzrechte, Nutzungsrechte |
| 10 | Höhere Gewalt | Force Majeure Klausel vorhanden? |
| 11 | Gerichtsstand & Recht | Anwendbares Recht, Gerichtsstand, Schiedsklausel |
| 12 | Salvatorische Klausel | Vorhanden? |
| 13 | Schriftformerfordernis | Änderungen nur schriftlich? |
| 14 | Konkurrenzverbot | Falls vorhanden: Dauer, Umfang, Konventionalstrafe |

### 3. Risikoeinschätzung

Fasse die Ergebnisse zusammen:
- **Gesamtrisiko:** 🟢 Niedrig / 🟡 Mittel / 🔴 Hoch
- **Top 3 Risiken:** Die drei kritischsten Punkte
- **Fehlende Klauseln:** Was fehlt und warum es relevant ist

### 4. Rechtsgrundlagen

Delegiere an den **recherche-agent**: Suche nach relevanten Rechtsgrundlagen und aktueller Rechtsprechung zu den identifizierten Risiken. Der Recherche-Agent liefert die Ergebnisse zurück, die du in die Analyse einbaust.

## Ausgabeformat

```markdown
# Vertragsanalyse: [Vertragstyp]

## Überblick
| Feld | Wert |
|------|------|
| Vertragstyp | ... |
| Parteien | ... |
| Datum | ... |
| Sprache | ... |
| Status | Entwurf / Final |
| **Gesamtrisiko** | 🟢/🟡/🔴 |

## Klausel-Analyse
| # | Klausel | Status | Bemerkung |
|---|---------|--------|-----------|
| 1 | Vertragsparteien | 🟢 | Korrekt bezeichnet |
| 2 | Vertragsgegenstand | 🟡 | Leistungsumfang ungenau definiert |
| ... | ... | ... | ... |

## Top Risiken
1. 🔴 **[Risiko]:** [Beschreibung und Empfehlung]
2. 🔴 **[Risiko]:** [Beschreibung und Empfehlung]
3. 🟡 **[Risiko]:** [Beschreibung und Empfehlung]

## Fehlende Klauseln
- [Klausel]: [Warum relevant]

## Relevante Rechtsgrundlagen
- [Vom Recherche-Agent geliefert]
```

## Regeln

- Sprache: Deutsch (Schweizer Rechtschreibung, kein ß)
- Dies ist **keine Rechtsberatung**, sondern eine strukturierte Analyse
- Bei Unsicherheit: klar als «unklar – juristische Prüfung empfohlen» markieren
- Vertrauliche Inhalte nicht in Suchanfragen verwenden
- Immer alle 14 Klauselkategorien prüfen, auch wenn sie im Vertrag fehlen
