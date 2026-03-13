---
description: >
  Führt eine vollständige Vertragsanalyse durch: Prüft alle Klauseln,
  recherchiert Rechtsgrundlagen und erstellt eine Management-Zusammenfassung.
  Nutzt den Skill "vertragsanalyse", delegiert an den "recherche-agent"
  und erstellt mit dem Skill "zusammenfassung" das Endergebnis.

arguments: Pfad zur Vertragsdatei oder Name des Vertrags im aktuellen Ordner
---

# Vertragsprüfung – Vollständiger Workflow

Führe eine vollständige Vertragsanalyse in drei Schritten durch:

## Schritt 1: Vertragsanalyse
Nutze den Skill **«vertragsanalyse»** und analysiere den Vertrag:
- Lies den gesamten Vertrag: $ARGUMENTS
- Prüfe alle 14 Klauselkategorien mit dem Ampelsystem (🟢🟡🔴)
- Identifiziere die Top-Risiken und fehlende Klauseln

## Schritt 2: Rechtsgrundlagen recherchieren
Delegiere an den **«recherche-agent»**:
- Übergib ihm die identifizierten Risiken und fehlenden Klauseln
- Der Recherche-Agent sucht passende Gesetzesartikel und Rechtsprechung
- Baue die Ergebnisse in die Analyse ein

## Schritt 3: Management-Zusammenfassung
Nutze den Skill **«zusammenfassung»** und erstelle:
- Eine 1-seitige Entscheidungsvorlage basierend auf der Analyse
- Klare Handlungsempfehlungen (Muss / Sollte / Kann)
- Eine Empfehlung: Unterzeichnen, Nachverhandeln oder Ablehnen

## Ausgabe

Liefere dem Nutzer **beide Dokumente**:
1. Die detaillierte Klausel-Analyse (aus Schritt 1 + 2)
2. Die Management-Zusammenfassung (aus Schritt 3)

Falls der Vertrag als Datei vorliegt, speichere die Ergebnisse auch als Markdown-Datei im gleichen Ordner.
