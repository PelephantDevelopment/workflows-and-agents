---
description: >
  Sortiert alle Dateien im Ordner nach juristischen Kategorien,
  benennt sie einheitlich um und erstellt eine Inventarliste.
  Nutzt den Skill «datei-sortierung», delegiert unklare Dokumente
  an den «dokument-checker» und erstellt mit dem Skill «inventar»
  die Übersichtsliste.

arguments: Optionaler Pfad zum Ordner. Ohne Angabe wird der aktuelle Ordner verwendet.
---

# Ordner aufräumen – Vollständiger Workflow

Führe eine vollständige Datei-Sortierung in drei Schritten durch:

## Schritt 1: Dateien sortieren

Nutze den Skill **«datei-sortierung»**:
- Lies den Inhalt aller Dateien im Ordner: $ARGUMENTS
- Kategorisiere jede Datei (Verträge, Urteile, Fachartikel etc.)
- Erstelle die Unterordner (01_Vertraege/ bis 08_Sonstiges/)
- Benenne die Dateien einheitlich um
- Verschiebe sie in die passenden Unterordner

## Schritt 2: Unklare Dokumente klären

Delegiere an den **«dokument-checker»**:
- Übergib alle Dateien, die nicht eindeutig zugeordnet werden konnten
- Der dokument-checker recherchiert im Web und gibt Empfehlungen zurück
- Verschiebe die Dateien gemäss den Empfehlungen

## Schritt 3: Inventar erstellen

Nutze den Skill **«inventar»**:
- Erstelle eine vollständige Inventarliste (00_INVENTAR.md)
- Nutze die Ergebnisse aus Schritt 1 und Schritt 2
- Markiere vertrauliche Dokumente, Entwürfe und Sicherheitsrisiken

## Wichtig

- NIEMALS Dateien löschen
- Die Datei claude.md NICHT verschieben
- Bei Unsicherheit: in 08_Sonstiges/ ablegen
