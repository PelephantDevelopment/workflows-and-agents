# Einen Skill erstellen: «Ordner aufräumen»

> **Dauer:** ca. 20 Minuten  
> **Für wen:** Alle, die Cowork nutzen – keine technischen Vorkenntnisse nötig  
> **Was du am Ende hast:** Einen Skill, der Dateien nach Inhalt sortiert – aufrufbar in jedem Cowork-Task  
> **Was du brauchst:**
> - Claude Desktop App ([claude.com/download](https://claude.com/download))
> - Pro, Max, Team oder Enterprise Abo
> - Den Ordner `testdateien/` aus diesem Repo (50 chaotische Beispieldateien)

---

## Was ist ein Skill?

Kurz gesagt: Ein Skill ist eine **Arbeitsanweisung**, die Claude sich merkt.

Ohne Skill sagst du jedes Mal:
> *«Lies alle Dateien in diesem Ordner, kategorisiere sie nach Verträge, Urteile, Fachartikel, Korrespondenz, Rechnungen und Präsentationen, erstelle Unterordner, benenne die Dateien einheitlich um im Format Datum_Beschreibung, und erstelle eine Inventarliste als Markdown...»*

Mit Skill sagst du:
> *«Räume diesen Ordner auf.»*

Claude erkennt, dass der Skill passt, und befolgt die hinterlegte Anleitung. Du schreibst die lange Anweisung einmal – und nutzt sie immer wieder.

---

## Vorbereitung

### Claude Desktop App prüfen

1. Öffne die **Claude Desktop App** (nicht die Website claude.ai!)
2. Oben siehst du drei Tabs: **Chat | Cowork | Code**
3. Klicke auf **«Cowork»**
4. Siehst du links eine Sidebar mit «Customize»? → Perfekt, du bist bereit

Falls du den Tab «Cowork» nicht siehst:
- Prüfe, ob die App auf dem neuesten Stand ist (App schliessen, neu öffnen)
- Mac: Du brauchst Apple Silicon (M1 oder neuer)
- Windows: Alle unterstützten Geräte funktionieren

### Testdateien vorbereiten

1. Lade `testdateien-chaos.zip` aus diesem Repo herunter
2. Entpacke die ZIP auf deinem **Desktop**
3. Du hast jetzt einen Ordner `testdateien/` mit 50 chaotischen Dateien

Öffne den Ordner kurz und schau rein. Du siehst ein Durcheinander aus Verträgen, Urteilen, E-Mails, Rechnungen, Präsentationen – in verschiedenen Sprachen, mit uneinheitlichen Dateinamen. Genau so sieht ein typischer Downloads-Ordner aus.

---

## Schritt 1: Neuen Cowork-Task starten

1. Klicke in Cowork auf **«+ New task»** (oder «Neue Aufgabe»)
2. Claude fragt dich, auf welchen **Ordner** du Zugriff geben willst
3. Wähle den Ordner **`testdateien/`** auf deinem Desktop
4. Du siehst jetzt ein Chatfenster – Claude hat Zugriff auf den Ordner

**Noch nichts eintippen.** Wir erstellen zuerst den Skill.

---

## Schritt 2: Skill erstellen

Tippe folgenden Text in das Chatfenster und drücke Enter:

```
Ich möchte einen neuen Skill erstellen. Der Skill soll "ordner-aufraeumen" heissen und folgendes tun:

Wenn ich sage "räume auf", "sortiere", "organisiere diesen Ordner" oder ähnliches, soll der Skill aktiviert werden.

Hier ist die Anleitung, die der Skill enthalten soll:

---

SKILL: Juristische Datei-Sortierung

ROLLE:
Du bist ein Dokumenten-Sortier-Assistent für eine Anwaltskanzlei.

AUFGABE:
Analysiere ALLE Dateien im aktuellen Ordner. Lies den INHALT jeder Datei (nicht nur den Dateinamen) und sortiere sie systematisch.

VORGEHEN:

1. Jede Datei öffnen und den Inhalt lesen
2. Dokumenttyp erkennen (Vertrag, Urteil, Fachartikel etc.)
3. Sprache erkennen (DE, FR, EN, IT)
4. Datum aus dem Inhalt extrahieren (falls erkennbar)
5. Datei in den passenden Unterordner verschieben
6. Datei einheitlich umbenennen
7. Am Ende eine Inventarliste erstellen

KATEGORIEN UND UNTERORDNER:
- 01_Vertraege/    → NDA, Dienstleistungsverträge, Mietverträge, Kaufverträge, AGB, SLA, Lizenzverträge, Aufhebungsvereinbarungen
- 02_Urteile/      → BGE, Handelsgerichtsurteile, Strafbefehle, Behördenentscheide, EuGH-Urteile
- 03_Fachartikel/  → Papers, Aufsätze, Kommentare, Whitepapers, Studien, Newsletter
- 04_Korrespondenz/ → E-Mails, Briefe, Mahnungen, Memos, Notizen, Meeting Notes, Protokolle, Gutachten
- 05_Rechnungen/   → Rechnungen, Honorarnoten, Offerten, Budgets, Spesen, Zeiterfassungen
- 06_Praesentationen/ → PowerPoint, Pitch Decks, Vortragsslides, Schulungen
- 07_Personal/     → Lebensläufe, Arbeitszeugnisse, Bewerbungen
- 08_Sonstiges/    → Alles was nicht eindeutig zugeordnet werden kann

UMBENENNUNG:
Schema: [JJJJ-MM-DD]_[Kurzbeschreibung].[ext]
- Datum aus dem Inhalt extrahieren
- Falls kein Datum erkennbar: 0000-00-00
- Kurzbeschreibung: max. 5 Wörter, Unterstriche statt Leerzeichen
- Beispiele:
  - 2026-02-15_NDA_TechVision_InnoSoft.docx
  - 2022-03-22_BGE_148_II_137_Auskunftsrecht.pdf
  - 0000-00-00_Arbeitsvertrag_Muster.pdf

INVENTARLISTE:
Erstelle eine Datei 00_INVENTAR.md im Hauptordner mit:
- Zusammenfassungstabelle: Kategorie | Anzahl Dateien
- Detailtabelle: Originaler Name | Neuer Pfad | Sprache | Beschreibung (1 Satz)
- Warnungen für besondere Dateien:
  - ⚠ VERTRAULICH: Dokumente mit Vertraulichkeitshinweis
  - 📝 ENTWURF: Nicht finalisierte Dokumente
  - ⚠ SICHERHEITSRISIKO: Passwort-Dateien, unverschlüsselte Zugangsdaten

REGELN:
- NIEMALS Dateien löschen – nur verschieben und umbenennen
- Bei Unsicherheit: in 08_Sonstiges/ ablegen
- Sprache der Inventarliste: Deutsch (Schweizer Rechtschreibung, kein ß)
- Dateien in allen Sprachen (DE, FR, EN, IT) werden korrekt erkannt
- Die Datei claude.md NICHT verschieben (falls vorhanden)

---

Bitte erstelle diesen Skill für mich und speichere ihn, sodass ich ihn in jedem zukünftigen Cowork-Task nutzen kann.
```

---

## Schritt 3: Claudes Rückfragen beantworten

Claude wird den Skill erstellen und dabei möglicherweise **Rückfragen** stellen, z.B.:

- *«Soll der Skill nur in bestimmten Ordnern funktionieren?»* → **Nein, in jedem Ordner**
- *«Soll ich den Skill als eigenständigen Skill oder als Plugin speichern?»* → **Als eigenständigen Skill**
- *«Möchtest du den Skill anpassen?»* → **Nein, so ist es gut. Bitte speichern.**

Beantworte die Fragen. Claude erstellt und speichert den Skill.

---

## Schritt 4: Prüfen ob der Skill gespeichert ist

1. Klicke links in der Sidebar auf **«Customize»**
2. Du solltest den Skill **«ordner-aufraeumen»** in der Liste sehen
3. Klicke darauf, um die Details anzusehen

Siehst du ihn? → Weiter zu Schritt 5.

Siehst du ihn nicht? → Tippe in den Chat:
```
Bitte zeige mir meine gespeicherten Skills.
```
Falls der Skill nicht gespeichert wurde, bitte Claude:
```
Bitte speichere den Skill "ordner-aufraeumen" als eigenständigen Skill 
in meinen Cowork-Einstellungen.
```

---

## Schritt 5: Skill testen – die 50 Dateien sortieren

Jetzt der Moment, auf den alles hinarbeitet. Du hast den Skill gespeichert – testen wir ihn.

**Falls du noch im gleichen Task bist** (Ordner `testdateien/` ist noch aktiv):

Tippe einfach:
```
Bitte räume diesen Ordner auf.
```

**Falls du einen neuen Task startest:**

1. Klicke auf **«+ New task»**
2. Wähle den Ordner **`testdateien/`**
3. Tippe:
   ```
   Sortiere alle Dateien in diesem Ordner.
   ```

---

## Schritt 6: Zuschauen

Claude zeigt dir jetzt seinen **Plan**. Du siehst etwas wie:

> *«Ich werde alle 50 Dateien lesen, ihren Inhalt analysieren, sie in 8 Kategorien einteilen, Unterordner erstellen, die Dateien verschieben und umbenennen, und eine Inventarliste erstellen.»*

**Bestätige den Plan.** Dann lehne dich zurück und schaue zu.

Was du sehen wirst:
- Claude öffnet Datei für Datei
- Erkennt: «Das ist ein NDA zwischen TechVision und InnoSoft»
- Erstellt den Ordner `01_Vertraege/`
- Benennt um: `NDA_Project_Alpha_unsigned.docx` → `2026-02-15_NDA_TechVision_InnoSoft.docx`
- Verschiebt die Datei
- Nächste Datei...

Das dauert einige Minuten. Du kannst zwischendurch etwas anderes tun – Claude arbeitet weiter.

---

## Schritt 7: Ergebnis prüfen

Wenn Claude fertig ist, öffne den Ordner `testdateien/` im Datei-Explorer.

**Vorher** sah der Ordner so aus:
```
testdateien/
├── NDA_Project_Alpha_unsigned.docx
├── BGE_148_II_137.pdf
├── Rechnung_2024-0847.pdf
├── scan0042.txt
├── passwörter_NICHT_LÖSCHEN.txt
├── Präsentation_Mandantenmeeting.pptx
├── ... (50 Dateien wild durcheinander)
```

**Nachher** sollte er so aussehen:
```
testdateien/
├── 00_INVENTAR.md              ← Übersichtsliste
├── 01_Vertraege/
│   ├── 2026-02-15_NDA_TechVision_InnoSoft.docx
│   ├── 2025-01-01_Mietvertrag_Talstrasse.docx
│   └── ... (ca. 10 Dateien)
├── 02_Urteile/
│   ├── 2022-03-22_BGE_148_II_137_Auskunftsrecht.pdf
│   └── ... (ca. 8 Dateien)
├── 03_Fachartikel/
│   └── ... (ca. 8 Dateien)
├── 04_Korrespondenz/
│   └── ... (ca. 10 Dateien)
├── 05_Rechnungen/
│   └── ... (ca. 6 Dateien)
├── 06_Praesentationen/
│   └── ... (ca. 4 Dateien)
├── 07_Personal/
│   └── ... (1 Datei)
└── 08_Sonstiges/
    └── ... (ca. 3 Dateien, z.B. die Passwort-Datei)
```

**Öffne die Datei `00_INVENTAR.md`** in einem Texteditor. Du siehst:
- Eine Zusammenfassung (wie viele Dateien pro Kategorie)
- Eine Detailtabelle (jede Datei mit altem und neuem Namen)
- Warnungen (vertrauliche Dokumente, Entwürfe, Sicherheitsrisiken)

**Prüfe stichprobenartig:**
- Sind die Verträge wirklich Verträge?
- Hat Claude die französischen und englischen Dokumente richtig erkannt?
- Sind die Dateinamen sinnvoll?
- Wurde die Passwort-Datei als Sicherheitsrisiko markiert?

---

## Schritt 8: Skill in einem anderen Ordner testen

Der Skill ist jetzt **dauerhaft gespeichert**. Teste ihn mit einem anderen Ordner:

1. Starte einen **neuen Task** in Cowork
2. Wähle einen **anderen Ordner** (z.B. deinen echten Downloads-Ordner – aber Vorsicht, mach vorher ein Backup!)
3. Tippe:
   ```
   Räume diesen Ordner auf.
   ```

Claude erkennt automatisch, dass der Skill «ordner-aufraeumen» passt, und wendet ihn an – ohne dass du die ganzen Anweisungen nochmal schreiben musst.

---

## Schritt 9: Skill anpassen (optional)

Der Skill ist nicht in Stein gemeisselt. Du kannst ihn jederzeit anpassen:

1. Gehe zu **«Customize»** in der Sidebar
2. Klicke auf den Skill **«ordner-aufraeumen»**
3. Klicke auf **«Customize»** (oben rechts)
4. Claude öffnet einen Dialog, in dem du Anpassungen beschreiben kannst

**Beispiele für Anpassungen:**

```
Füge eine neue Kategorie hinzu: "09_Entwuerfe/" für alle 
Dokumente die als Entwurf erkennbar sind (Draft, Entwurf, v2, v3).
```

```
Ändere das Umbenennungsschema: Füge die Kategorie in den 
Dateinamen ein, z.B. Vertrag_2026-02-15_NDA_TechVision.docx
```

```
Füge eine Regel hinzu: Dateien die älter als 2 Jahre sind, 
sollen in einen Unterordner "Archiv/" verschoben werden.
```

---

## Zusammenfassung: Was du gemacht hast

```
Schritt 1:  Cowork-Task gestartet
Schritt 2:  Skill-Anleitung an Claude gegeben → "Erstelle diesen Skill"
Schritt 3:  Rückfragen beantwortet
Schritt 4:  Geprüft ob der Skill gespeichert ist
Schritt 5:  "Räume diesen Ordner auf" getippt
Schritt 6:  Claude hat 50 Dateien selbstständig sortiert
Schritt 7:  Ergebnis geprüft
Schritt 8:  Skill in anderem Ordner getestet
Schritt 9:  Optional: Skill angepasst
```

Der Skill bleibt gespeichert. Ab jetzt reicht in jedem Cowork-Task ein Satz.

---

## Wie geht es weiter?

Du hast jetzt **einen** Skill. Hier sind drei Ideen, was du als nächstes tun kannst:

### Idee 1: Diesen Skill als geplante Aufgabe einrichten
Tippe in einem Cowork-Task:
```
/schedule
```
Und sage: «Jeden Freitag um 17:00 den Downloads-Ordner aufräumen.»
Claude sortiert dann automatisch – ohne dass du es jedes Mal manuell anstösst.

### Idee 2: Einen zweiten Skill erstellen
Nutze das gleiche Vorgehen (Schritt 2) mit einer anderen Aufgabe, z.B.:
- *«Erstelle einen Skill, der Verträge auf Risiken prüft»*
- *«Erstelle einen Skill, der Meeting-Teilnehmer recherchiert»*
- *«Erstelle einen Skill, der eine Zusammenfassung von Dokumenten erstellt»*

### Idee 3: Vom Skill zum Plugin
Wenn du mehrere zusammenhängende Skills hast, kannst du sie in ein **Plugin** bündeln – mit Sub-Agents, Slash-Commands und Connectors. Das ist der nächste Level. Siehe dazu den Workshop «Agenten-Struktur verstehen».

---

## Wenn etwas nicht funktioniert

| Was passiert | Woran liegt es | Was tun |
|-------------|----------------|---------|
| «Cowork» Tab fehlt | App veraltet oder Intel-Mac | App updaten. Mac: M1+ nötig |
| Skill wird nicht gespeichert | Claude hat den Skill nur ausgeführt, aber nicht gespeichert | Explizit bitten: «Speichere diesen Skill dauerhaft» |
| Skill feuert nicht bei neuem Task | Claude erkennt die Aufgabe nicht als passend | Expliziter formulieren: «Nutze den Skill ordner-aufraeumen und sortiere diesen Ordner» |
| Dateien werden falsch kategorisiert | Der Inhalt war unklar oder der Skill zu ungenau | Skill anpassen via Customize → konkretere Beschreibung der Kategorien |
| Claude löscht Dateien | Sollte nicht passieren – Cowork fragt vorher | Falls doch: Backup nutzen. Regel «NIEMALS löschen» im Skill noch stärker betonen |
| Vorgang dauert sehr lange | Viele oder grosse Dateien | Normal bei 50+ Dateien. Abwarten oder kleinere Ordner nutzen |
| Token-Limit erreicht | Zu viele Dateien in einer Session | Ordner aufteilen oder auf einen günstigeren Zeitpunkt warten |
