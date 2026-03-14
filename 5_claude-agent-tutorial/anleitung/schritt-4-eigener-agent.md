
# Schritt 4_0: Prework - Probleme selber lösen.
> **Dauer:** ca. 15 Minuten  
> **Was du brauchst:** den Ordner `vorlage-leer/` aus diesem Repo als .zip Datei 
> **Was du am Ende hast:** Einen Weg gefunden, technische Probleme selber zu lösen.
>
> ## Was wir jetzt tun
>
> ## Schritt 4_0a: Plugin installieren

Jetzt wird es ernst – du installierst deinen Agent in Cowork:

1. Öffne die **Claude Desktop App**
2. Wechsle zum Tab **«Cowork»** (oben)
3. Klicke links in der Sidebar auf **«Customize»**
4. Klicke auf **«Browse plugins»**
5. Klicke auf **«Upload»** (oder «Eigenes Plugin hochladen»)
6. Navigiere zu deinem Plugin-Ordner vorlage-leer.zip und wähle ihn
7. Du solltest eine Fehlermeldung sehen, dass das PlugIn auf Grund von "Plugin name must be kebab-case: lowercase letters, numbers, and hyphens (e.g. 'my-plugin')." nicht installierbar ist.

Was das bedeutet:
In plugin.json steht "name": "HIER-PLUGIN-NAME" — die Grossbuchstaben verletzen die kebab-case-Regel. Cowork akzeptiert nur Kleinbuchstaben, Zahlen und Bindestriche.

Wie kannst du das beheben?
1. Öffne im Explorer claude.ai
2. kopiere einen Screenshot der Fehlermeldung und Frage um Rat
tip: du kannst bei Claude.ai ganze .zip files hochladen und claude bitten es anzupassen
3. Wenn dir der Tip nicht geholfen hat, mache konkret Folgendes:
Lade die Datei vorlage-leer.zip in den Chat, zusammen mit folgendem Text: "bitte prüfe wo das problem liegt"
Claude wird das Problem finden: "Da ist das Problem: In plugin.json steht "name": "HIER-PLUGIN-NAME"" und dich fragen ob er das Problem beheben soll. Nehme den Vorschlag an, lasse Claude eine neue .zip datei erstellen, und starte nun nochmals den Versuch diese als Plug-In zu installieren


# Schritt 4_0: Prework - Probleme selber lösen - erfolgreich beendet :)

# Schritt 4: Eigenen Agent bauen

> **Dauer:** ca. 15 Minuten  
> **Was du brauchst:** Einen Texteditor und den Ordner `vorlage-leer/` aus diesem Repo  
> **Was du am Ende hast:** Einen eigenen Agent, installiert und funktionsfähig in Cowork.

---

## Was wir jetzt tun

Du nimmst den Ordner `vorlage-leer/`, ersetzt alle `HIER`-Platzhalter mit deinem eigenen Inhalt und installierst das Ergebnis als Plugin in Cowork.

---

## Schritt 4a: Anwendungsfall wählen

Bevor du anfängst zu schreiben, entscheide: **Was soll dein Agent tun?**

Nimm dir einen Moment und beantworte diese drei Fragen – am besten auf einem Zettel oder in einem leeren Dokument:

| Frage | Deine Antwort |
|-------|---------------|
| **1. Was ist die Hauptaufgabe?** | z.B. «Verträge auf Risiken prüfen» |
| **2. Wobei braucht der Agent Hilfe?** | z.B. «Rechtsgrundlagen im Web suchen» |
| **3. Was soll am Ende rauskommen?** | z.B. «1-seitige Zusammenfassung» |

**Dir fällt nichts ein?** Hier sind Ideen – wähle eine:

| Nr. | Agent-Idee | Hauptaufgabe | Helfer tut | Endergebnis |
|-----|------------|-------------|------------|-------------|
| A | **Vertragsanalyse** | Klauseln prüfen (🟢🟡🔴) | Rechtsgrundlagen suchen | Zusammenfassung + Empfehlung |
| B | **Datenschutz-Check** | nDSG/DSGVO-Konformität prüfen | EDÖB-Praxis suchen | Massnahmenplan |
| C | **Meeting-Vorbereitung** | Teilnehmer identifizieren | Personen recherchieren | Briefing-Dokument |
| D | **Fristenkontrolle** | Fristen aus Verträgen lesen | Gesetzl. Fristen nachschlagen | Fristenkalender |
| E | **Compliance-Check** | Neue Regulierung analysieren | Betroffene Policies suchen | Gap-Analyse |
| F | **Mandats-Status** | Offene Punkte sammeln | Aktuelle Entwicklungen suchen | Wochenbericht |

Du hast dich entschieden? Dann los.

---

## Schritt 4b: Ordner kopieren

1. Kopiere den Ordner `vorlage-leer/` an einen Ort deiner Wahl (z.B. Desktop)
2. Benenne die Kopie um – z.B. in `datenschutz-check/` oder `meeting-prep/`

Ab jetzt arbeitest du nur in deiner Kopie.

---

## Schritt 4c: Manifest ausfüllen (1 Minute)

📂 **Öffne:** `.claude-plugin/plugin.json`

Du siehst:
```json
{
  "name": "HIER-PLUGIN-NAME",
  "description": "HIER ANPASSEN: Was tut dein Agent? (1-2 Sätze)",
  "version": "1.0.0",
  "author": {
    "name": "HIER DEIN NAME"
  }
}
```

**Ersetze die drei HIER-Felder.** Beispiel:
```json
{
  "name": "datenschutz-check",
  "description": "Prüft Dokumente und Prozesse auf Konformität mit nDSG und DSGVO. Recherchiert aktuelle EDÖB-Praxis und erstellt einen Massnahmenplan.",
  "version": "1.0.0",
  "author": {
    "name": "Anna Muster"
  }
}
```

**Regeln für `name`:** Kleinbuchstaben, keine Leerzeichen, Bindestriche erlaubt. Dieser Name wird Teil des Slash-Commands: `/datenschutz-check:ausfuehren`

**Speichern und schliessen.**

---

## Schritt 4d: Skill 1 ausfüllen – die Hauptaufgabe (5 Minuten)

📂 **Öffne:** `skills/hauptaufgabe/SKILL.md`

Das ist die wichtigste Datei – nimm dir hier am meisten Zeit. Du siehst eine Datei voller `HIER`-Platzhalter und Kommentare in `<!-- -->`.

**Arbeite von oben nach unten:**

**1. YAML-Header (die ersten 3 Zeilen):**
```yaml
---
name: HIER-SKILL-NAME
description: >
  HIER ANPASSEN: Wann soll dieser Skill aktiviert werden?
---
```
Ersetze mit deinem Skill-Namen und einer Beschreibung. Beispiel:
```yaml
---
name: konformitaets-pruefung
description: >
  Aktiviert sich wenn Dokumente oder Prozesse auf Datenschutz-Konformität
  geprüft werden sollen. Erkennt Datenschutzerklärungen, Verträge mit
  Personendaten-Bezug und interne Richtlinien.
---
```

**2. Rolle:**
```markdown
Du bist ein HIER ROLLE BESCHREIBEN.
```
Ersetze mit einer konkreten Rolle, z.B.:
```markdown
Du bist ein Datenschutz-Spezialist für Schweizer und europäisches Recht, 
mit besonderer Expertise im nDSG und in der DSGVO.
```

**3. Aufgabe und Prüf-Checkliste:**

Hier kommt dein Fachwissen rein. Ersetze die leere Tabelle:
```markdown
| # | Prüfpunkt | Worauf achten |
|---|-----------|---------------|
| 1 | HIER | HIER |
```

mit deinen konkreten Prüfpunkten, z.B.:
```markdown
| # | Prüfpunkt | Worauf achten |
|---|-----------|---------------|
| 1 | Informationspflicht (Art. 19 nDSG) | Werden Betroffene informiert? |
| 2 | Rechtsgrundlage (Art. 6 nDSG) | Liegt eine Rechtsgrundlage vor? |
| 3 | DSFA (Art. 22 nDSG) | Ist eine Folgenabschätzung nötig? |
| 4 | Auslandsübermittlung (Art. 16 nDSG) | Werden Daten ins Ausland übermittelt? |
| 5 | Auftragsverarbeitung (Art. 9 nDSG) | Gibt es einen AVV? |
```

**4. Delegation an den Sub-Agent:**

Ersetze:
```markdown
Delegiere an den **helfer-agent**: HIER BESCHREIBEN was der Sub-Agent tun soll.
```
mit z.B.:
```markdown
Delegiere an den **helfer-agent**: Recherchiere die aktuelle EDÖB-Praxis 
und relevante Stellungnahmen zu den identifizierten Datenschutz-Risiken.
```

**5. Ausgabeformat und Regeln:** Ersetze die restlichen `HIER`-Platzhalter.

**6. Ordner umbenennen:** Benenne den Ordner `hauptaufgabe/` um in deinen Skill-Namen, z.B. `konformitaets-pruefung/`.

**Tipp:** Du musst nicht alles perfekt haben. Fülle aus was du kannst – du kannst den Skill jederzeit nachbearbeiten.

**Speichern und schliessen.**

---

## Schritt 4e: Sub-Agent ausfüllen (3 Minuten)

📂 **Öffne:** `agents/helfer-agent.md`

**1. YAML-Header:**
```yaml
---
name: helfer-agent
model: sonnet
tools:
  - WebSearch
  - Read
---
```

Passe an:
- `name`: Wie soll dein Helfer heissen? (z.B. `edoeb-recherche`)
- `model`: `sonnet` (schnell) oder `opus` (gründlicher) – für Recherche ist `sonnet` meist ausreichend
- `tools`: Welche Werkzeuge braucht er? Meistens `WebSearch` + `Read`

**2. Aufgabe:** Ersetze die `HIER`-Platzhalter mit konkreten Beispiel-Anfragen, die der Skill an den Agent schicken würde.

**3. Datei umbenennen:** z.B. `helfer-agent.md` → `edoeb-recherche.md`

**⚠️ Wichtig:** Wenn du den `name` änderst, musst du auch den Verweis in Skill 1 anpassen! Wenn dort steht «Delegiere an den **helfer-agent**» und du den Agent in `edoeb-recherche` umbenennst, ändere es in «Delegiere an den **edoeb-recherche**».

**Brauchst du keinen Sub-Agent?** Dann lösche den ganzen `agents/`-Ordner und entferne die Delegation aus Skill 1 (den Abschnitt «Teilaufgabe delegieren»).

**Speichern und schliessen.**

---

## Schritt 4f: Skill 2 ausfüllen – die Ausgabe (3 Minuten)

📂 **Öffne:** `skills/ausgabe-erstellen/SKILL.md`

**1. YAML-Header:** Name und Beschreibung anpassen.

**2. Voraussetzung:** Hier stehen schon Verweise auf Skill 1 und den Sub-Agent. Passe die **Namen** an die Namen an, die du in Schritt 4d und 4e vergeben hast.

Beispiel – vorher:
```markdown
Dieser Skill nutzt die **Ergebnisse aus dem Skill «hauptaufgabe»**
```
Nachher:
```markdown
Dieser Skill nutzt die **Ergebnisse aus dem Skill «konformitaets-pruefung»**
```

**3. Aufgabe und Format:** Was soll am Ende rauskommen? Eine Zusammenfassung? Ein Massnahmenplan? Ein Excel?

**4. Ordner umbenennen:** z.B. `ausgabe-erstellen/` → `massnahmenplan/`

**Brauchst du keinen zweiten Skill?** Wenn Skill 1 schon alles liefert, lösche den Ordner.

**Speichern und schliessen.**

---

## Schritt 4g: Command ausfüllen (2 Minuten)

📂 **Öffne:** `commands/ausfuehren/COMMAND.md`

Hier musst du nur die drei Schritte anpassen und sicherstellen, dass die **Namen stimmen**:

```markdown
## Schritt 1
Nutze den Skill **«konformitaets-pruefung»** und...
                   ↑ muss identisch sein mit dem name in Skill 1

## Schritt 2
Delegiere an den **«edoeb-recherche»**...
                    ↑ muss identisch sein mit dem name des Sub-Agent

## Schritt 3
Nutze den Skill **«massnahmenplan»** und...
                   ↑ muss identisch sein mit dem name in Skill 2
```

**Ordner umbenennen:** z.B. `ausfuehren/` → `pruefen/`

Damit wird der Slash-Command: `/datenschutz-check:pruefen`

**Speichern und schliessen.**

---

## Schritt 4h: Connectors-Datei (30 Sekunden)

📂 **Schau dir an:** `.mcp.json`

Brauchst du externe Dienste (Gmail, Google Drive, Slack)?
- **Nein** → Lösche die Datei
- **Ja** → Richte die Connectors in der Claude Desktop App ein (Settings → Connectors)

Für den Anfang: **Lösche die Datei.** Du kannst sie später immer hinzufügen.

---

## Schritt 4i: Selbst-Check

Bevor du installierst – gehe diese Checkliste durch:

- [ ] **plugin.json:** `name` und `description` ausgefüllt? Keine `HIER`-Platzhalter mehr?
- [ ] **Skill 1:** Alle `HIER` ersetzt? Rolle, Aufgabe, Checkliste, Ausgabeformat, Regeln?
- [ ] **Skill 1 → Agent:** Der Name des Sub-Agent stimmt mit dem `name` im Agent überein?
- [ ] **Sub-Agent:** `name`, `model` und `tools` gewählt? Aufgabe beschrieben?
- [ ] **Skill 2:** Verweist auf Skill 1 und Sub-Agent mit den **richtigen Namen**?
- [ ] **Command:** Alle drei Schritte referenzieren die **richtigen Namen**?
- [ ] **Ordner umbenannt?** (Keine generischen Namen wie `hauptaufgabe/` mehr)

---

## Schritt 4j: Plugin installieren

Jetzt wird es ernst – du installierst deinen Agent in Cowork:

1. Öffne die **Claude Desktop App**
2. Wechsle zum Tab **«Cowork»** (oben)
3. Klicke links in der Sidebar auf **«Customize»**
4. Klicke auf **«Browse plugins»**
5. Klicke auf **«Upload»** (oder «Eigenes Plugin hochladen»)
6. Navigiere zu deinem Plugin-Ordner (z.B. `datenschutz-check/`) und wähle ihn
7. Du solltest eine Bestätigung sehen, dass das Plugin installiert wurde

**Siehst du den Ordner nicht?** Wenn der Ordner `.claude-plugin` versteckt ist, zeige versteckte Dateien an (Mac: `Cmd+Shift+.`, Windows: Explorer → Ansicht → Ausgeblendete Elemente).

---

## Schritt 4k: Testen

Starte einen neuen Cowork-Task und teste deinen Agent:

**Test 1 – Natürliche Sprache:**
Tippe einfach, was du willst, z.B.:
```
Prüfe bitte dieses Dokument auf Datenschutz-Konformität.
```
Claude sollte deinen Skill automatisch erkennen und nutzen.

**Test 2 – Per Slash-Command:**
```
/datenschutz-check:pruefen
```
Der Command sollte den vollständigen Workflow starten.

**Test 3 – Prüfe die Kette:**
Achte während der Arbeit darauf:
- [ ] Startet Skill 1 und geht die Checkliste durch?
- [ ] Wird der Sub-Agent aufgerufen (erkennst du an der Web-Suche)?
- [ ] Kommt am Ende das Ergebnis von Skill 2?

---

## Wenn etwas nicht funktioniert

| Was passiert | Woran liegt es wahrscheinlich | Was tun |
|-------------|-------------------------------|---------|
| Plugin erscheint nicht in Cowork | `plugin.json` liegt nicht in `.claude-plugin/` | Prüfe die Ordnerstruktur |
| Skill feuert nicht automatisch | Die `description` ist zu ungenau | Präziser formulieren, was den Skill auslösen soll |
| Sub-Agent wird nicht aufgerufen | Name-Mismatch zwischen Skill und Agent | Prüfe ob der Name im Skill exakt mit dem `name` im Agent übereinstimmt |
| Command findet Skill nicht | Name-Mismatch im Command | Prüfe ob alle referenzierten Namen korrekt sind |
| Ergebnis ist zu lang oder unstrukturiert | Regeln im Skill zu vage | Füge Regeln hinzu wie «Maximal 1 Seite» oder «Antworte in Tabellenform» |
| «Ich habe alles geprüft und es geht trotzdem nicht» | – | Starte einen neuen Cowork-Task und installiere das Plugin erneut |

---

## Geschafft! 🎉

Du hast deinen eigenen Agent gebaut und installiert. Ab jetzt kannst du:

- **Arbeiten:** Per Sprache oder Slash-Command deinen Agent nutzen
- **Verbessern:** Jederzeit die Markdown-Dateien bearbeiten und neu hochladen
- **Erweitern:** Neue Skills hinzufügen (neuer Ordner unter `skills/`)
- **Teilen:** Den Plugin-Ordner als ZIP an Kollegen schicken
- **Automatisieren:** Mit `/schedule` als geplante Aufgabe einrichten, die z.B. jeden Montag morgen läuft

---

## Wie geht es weiter?

Drei Ideen für deinen nächsten Schritt:

1. **Plugin verfeinern:** Nutze den Agent ein paar Tage und passe die Skills an, bis das Ergebnis stimmt. Das ist ein iterativer Prozess – die erste Version ist nie perfekt.

2. **Geplante Aufgabe:** Tippe `/schedule` in Cowork und richte deinen Agent als automatische, wiederkehrende Aufgabe ein – z.B. «Jeden Montag um 8:00 den Mandatsordner prüfen».

3. **Zweiten Agent bauen:** Jetzt wo du die Struktur kennst, geht der zweite Agent viel schneller. Kopiere die Vorlage erneut, fülle sie aus, installiere – fertig.
