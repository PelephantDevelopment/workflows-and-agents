# Schritt 2: Skill planen (Scheduled Task)

> **Dauer:** 5–10 Minuten  
> **Voraussetzung:** Schritt 1 abgeschlossen (Plugin installiert und getestet)  
> **Was du lernst:** Wie du den Sortier-Agent automatisch nach Zeitplan laufen lässt.

---

## Was ist eine geplante Aufgabe?

Bisher musstest du Claude jedes Mal manuell beauftragen: «Sortiere diesen Ordner.» Mit einer geplanten Aufgabe (Scheduled Task) passiert das **automatisch** – z.B. jeden Freitag um 17:00.

```
OHNE geplante Aufgabe:              MIT geplanter Aufgabe:

Jeden Freitag:                       Einmal einrichten:
1. Cowork öffnen                     1. /schedule
2. Ordner wählen                     2. Was? → Sortieren
3. "Sortiere bitte" tippen           3. Wann? → Freitag 17:00
4. Warten                            4. Welcher Ordner? → Downloads
5. Nächsten Freitag: Repeat...       5. Fertig – läuft automatisch
```

---

## Geplante Aufgabe erstellen

### Methode 1: Im Chat mit /schedule

1. Öffne **Cowork** in der Claude Desktop App

2. Starte einen **neuen Task**

3. Tippe:
   ```
   /schedule
   ```

4. Claude startet einen Dialog und fragt dich:

   **Was soll gemacht werden?**
   ```
   Sortiere alle Dateien im Ordner Downloads nach juristischen 
   Kategorien. Nutze das Plugin "ordner-aufraeumen". Erstelle 
   Unterordner nach Dokumenttyp, benenne die Dateien einheitlich 
   um und erstelle eine Inventarliste.
   ```

   **Wie oft / wann?**
   ```
   Jeden Freitag um 17:00
   ```

   **Welcher Ordner?**
   → Wähle deinen Downloads-Ordner (oder einen anderen Ordner)

5. Claude fasst die Aufgabe zusammen und fragt zur Bestätigung

6. Bestätige → ✅ Die geplante Aufgabe ist eingerichtet

### Methode 2: Über die Sidebar

1. Klicke in der linken Sidebar auf **«Scheduled»**
2. Klicke auf **«New Task»** (oder «Neue Aufgabe»)
3. Fülle die Felder aus:
   - **Name:** Ordner aufräumen
   - **Beschreibung:** Sortiere alle neuen Dateien nach juristischen Kategorien
   - **Zeitplan:** Wöchentlich, Freitag, 17:00
   - **Ordner:** [Dein Zielordner]
4. Bestätige

---

## Geplante Aufgabe verwalten

Alle geplanten Aufgaben findest du über **«Scheduled»** in der linken Sidebar.

### Aktionen:

| Aktion | Wie |
|--------|-----|
| **Übersicht** | Sidebar → «Scheduled» → alle Aufgaben sehen |
| **Manuell starten** | Aufgabe öffnen → «Run now» / «Jetzt ausführen» |
| **Zeitplan ändern** | Aufgabe öffnen → Zeitplan bearbeiten |
| **Pausieren** | Aufgabe öffnen → «Pause» |
| **Fortsetzen** | Aufgabe öffnen → «Resume» |
| **Löschen** | Aufgabe öffnen → «Delete» |
| **Verlauf ansehen** | Aufgabe öffnen → vergangene Ausführungen ansehen |

---

## Praxis-Beispiele für geplante Aufgaben

### Beispiel 1: Downloads-Ordner aufräumen (wöchentlich)

```
Was: Sortiere alle neuen Dateien im Ordner ~/Downloads nach 
     juristischen Kategorien. Verschiebe sortierte Dateien in 
     ~/Dokumente/Sortiert/. Erstelle eine Inventarliste.
Wann: Jeden Freitag um 17:00
```

### Beispiel 2: Desktop aufräumen (täglich)

```
Was: Prüfe den Desktop auf neue Dateien. Sortiere sie in den 
     Ordner ~/Dokumente/Sortiert/. Lass Verknüpfungen und 
     Ordner wo sie sind.
Wann: Jeden Tag um 18:00
```

### Beispiel 3: Mandatsordner prüfen (montags)

```
Was: Erstelle eine Inventarliste aller Dateien im Mandatsordner 
     ~/Mandate/Projekt_Alpha/. Nicht sortieren, nur analysieren. 
     Markiere neue Dateien seit letztem Montag.
Wann: Jeden Montag um 08:00
```

### Beispiel 4: Eingangspost digitalisiert sortieren (täglich)

```
Was: Prüfe den Ordner ~/Scans/ auf neue gescannte Dokumente. 
     Lies den Inhalt per OCR, kategorisiere sie und verschiebe 
     sie in die passenden Mandatsordner.
Wann: Jeden Tag um 07:00
```

---

## Wichtige Hinweise

### Voraussetzungen für geplante Aufgaben

- ⚡ Die **Claude Desktop App** muss **geöffnet** sein (nicht nur installiert)
- 💻 Der **Computer** muss **wach** sein (nicht im Schlafmodus)
- 🔄 Falls der Computer beim geplanten Zeitpunkt schlief: Claude holt die Aufgabe **automatisch nach**, sobald der Computer aufwacht und die App offen ist

### Was passiert wenn es nicht klappt?

| Problem | Lösung |
|---------|--------|
| Aufgabe wurde übersprungen | Computer war aus/im Schlafmodus → wird nachgeholt |
| Aufgabe läuft nicht | Prüfe: App offen? Cowork aktiv? |
| Ergebnisse stimmen nicht | Aufgabe bearbeiten → Beschreibung präzisieren |
| Zu viele Tokens verbraucht | Aufgabe seltener laufen lassen (z.B. wöchentlich statt täglich) |

### Token-Verbrauch

Geplante Aufgaben verbrauchen **mehr Tokens** als normale Chats, weil Claude autonom arbeitet und viele Dateien liest. Tipps:
- Starte mit **wöchentlicher** Frequenz, nicht täglich
- Begrenze den Ordner auf einen spezifischen Pfad
- Prüfe deinen Verbrauch unter **Settings → Usage**

---

## Zusammenfassung: Was du gebaut hast

```
Schritt 1: Plugin installiert
├── 🧠 Skill «datei-sortierung» → Dateien lesen, kategorisieren, umbenennen
├── 🤖 Sub-Agent «dokument-checker» → Unklare Dateien per Web identifizieren
├── 🧠 Skill «inventar» → Übersichtsliste erstellen
└── ⚡ Command /ordner-aufraeumen:sortieren → Alles orchestrieren

Schritt 2: Geplante Aufgabe eingerichtet
└── ⏰ Jeden Freitag um 17:00 → Claude sortiert automatisch
```

Du hast jetzt einen **vollständigen Agenten**, der:
1. Per Sprache oder Slash-Command manuell gestartet werden kann
2. Automatisch nach Zeitplan läuft
3. 50+ Dateien selbstständig liest, versteht, sortiert und dokumentiert
4. Bei unklaren Dokumenten im Web recherchiert
5. Eine professionelle Inventarliste erstellt

---

## Weiterdenken: Was könnte dein nächster Agent?

- **Vertragsanalyse:** Verträge auf Risiken prüfen statt sortieren
- **E-Mail-Triage:** Jeden Morgen E-Mails priorisieren und zusammenfassen
- **Mandats-Monitoring:** Neue Urteile zu laufenden Mandaten finden
- **Compliance-Check:** Dokumente gegen Regulierungen prüfen
- **Meeting-Prep:** Jeden Abend die Teilnehmer für morgen recherchieren

Die Plugin-Struktur ist immer die gleiche. Nur die Skills ändern sich.
