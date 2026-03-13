---
description: >
  HIER ANPASSEN: Was passiert wenn jemand diesen Command aufruft?
  Dieser Command orchestriert den gesamten Workflow:
  Skill «hauptaufgabe» → Sub-Agent «helfer-agent» → Skill «ausgabe-erstellen»

arguments: HIER was der Nutzer eingeben kann (z.B. "Pfad zur Datei" oder "Name des Dokuments")
---

<!--
╔══════════════════════════════════════════════════════════════════╗
║  COMMAND: DER ORCHESTRATOR                                      ║
║                                                                 ║
║  Dieser Command verbindet alle Bausteine zu einem Workflow:     ║
║                                                                 ║
║  Schritt 1 → Skill «hauptaufgabe»     (Analyse)                ║
║  Schritt 2 → Agent «helfer-agent»     (Recherche/Teilaufgabe)  ║
║  Schritt 3 → Skill «ausgabe-erstellen» (Endergebnis)           ║
║                                                                 ║
║  Aufruf: /HIER-PLUGIN-NAME:ausfuehren [Datei oder Eingabe]     ║
║                                                                 ║
║  TIPP: Benenne den Ordner "ausfuehren/" um für einen            ║
║  besseren Command-Namen, z.B.:                                  ║
║  "pruefen/" → /mein-agent:pruefen                              ║
║  "analysieren/" → /mein-agent:analysieren                       ║
║  "sortieren/" → /mein-agent:sortieren                           ║
╚══════════════════════════════════════════════════════════════════╝
-->

# HIER: Beschreibung des Workflows

Führe den gesamten Workflow in drei Schritten durch:

## Schritt 1: Analyse mit Skill «hauptaufgabe»

Nutze den Skill **«hauptaufgabe»** und HIER BESCHREIBEN:
- HIER: Was wird analysiert? (z.B. "Lies den Vertrag: $ARGUMENTS")
- HIER: Was wird geprüft? (z.B. "Prüfe alle Punkte der Checkliste")
- HIER: Was wird bewertet? (z.B. "Bewerte mit Ampelsystem 🟢🟡🔴")

## Schritt 2: Teilaufgabe an Sub-Agent «helfer-agent»

Delegiere an den **«helfer-agent»**:
- HIER: Was soll der Sub-Agent tun? (z.B. "Recherchiere Rechtsgrundlagen zu den Risiken")
- Der helfer-agent arbeitet unabhängig und liefert Ergebnisse zurück
- Baue die Ergebnisse in die Analyse aus Schritt 1 ein

## Schritt 3: Ausgabe mit Skill «ausgabe-erstellen»

Nutze den Skill **«ausgabe-erstellen»** und HIER BESCHREIBEN:
- HIER: Was wird erstellt? (z.B. "Erstelle eine Management-Zusammenfassung")
- Nutze die Ergebnisse aus Schritt 1 und Schritt 2
- HIER: Wie soll die Ausgabe aussehen? (z.B. "Maximal 1 Seite, mit Empfehlung")

## Ergebnis

Liefere dem Nutzer:
1. HIER: Erstes Ergebnis (z.B. "Die detaillierte Analyse aus Schritt 1+2")
2. HIER: Zweites Ergebnis (z.B. "Die Zusammenfassung aus Schritt 3")

Die Eingabe des Nutzers war: $ARGUMENTS
