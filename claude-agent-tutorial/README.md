# Eigenen KI-Agent bauen – Selbstlernkurs

> **Dauer:** ca. 45 Minuten (im eigenen Tempo)  
> **Für wen:** Juristinnen und Juristen – keine technischen Vorkenntnisse nötig  
> **Was du brauchst:** Claude Desktop App + Pro/Max/Team/Enterprise Abo  
> **Was du am Ende hast:** Einen eigenen KI-Agent, den du per Slash-Command starten kannst

---

## Worum geht es?

Du kennst Claude wahrscheinlich aus dem Chat – du stellst eine Frage, Claude antwortet. In diesem Kurs lernst du etwas Neues: Wie du Claude in einen **Spezialisten** verwandelst.

Stell dir vor, du hättest einen neuen Praktikanten. Du gibst ihm ein Handbuch: «Wenn ein Vertrag reinkommt, prüfe diese 14 Punkte, recherchiere die Rechtsgrundlagen und schreibe eine Zusammenfassung.» Genau das ist ein Agent – ein Handbuch für Claude, das du einmal schreibst und immer wieder nutzen kannst.

Das Besondere: **Ein Agent ist kein Programm.** Er besteht aus ganz normalen Textdateien. Wenn du eine E-Mail schreiben kannst, kannst du einen Agent bauen.

---

## Bevor du loslegst: Checkliste

Gehe diese Liste durch. Wenn ein Punkt fehlt, erledige ihn zuerst.

- [ ] **Claude Desktop App** installiert (nicht die Website claude.ai, sondern die App!)
  - Mac: [claude.com/download](https://claude.com/download) → macOS herunterladen → installieren
  - Windows: [claude.com/download](https://claude.com/download) → Windows herunterladen → installieren
- [ ] App geöffnet und mit deinem Claude-Account **eingeloggt**
- [ ] Du hast ein bezahltes Abo (**Pro** $20/Mo, **Max**, **Team** oder **Enterprise**)
- [ ] Oben in der App siehst du **drei Tabs: Chat | Cowork | Code** – klicke testweise auf «Cowork»
- [ ] Du hast dieses Repo **heruntergeladen und entpackt** (der Ordner, in dem diese README.md liegt)
- [ ] Du hast einen **Texteditor** bereit (TextEdit auf Mac, Notepad auf Windows, oder was du magst)

Alles erledigt? Dann los.

---

## So ist der Kurs aufgebaut

Du arbeitest vier Schritte durch, jeder baut auf dem vorherigen auf:

**[Schritt 1: Die Bausteine](anleitung/schritt-1-bausteine.md)** (10 Min.)
*Du lernst, aus welchen Teilen ein Agent besteht. Spoiler: Es sind nur 5 Teile, und 3 davon sind optional.*

↓

**[Schritt 2: Das Zusammenspiel](anleitung/schritt-2-zusammenspiel.md)** (10 Min.)
*Du lernst, wie die Teile zusammenarbeiten. Ein Skill ruft einen Helfer auf, der Helfer liefert Ergebnisse zurück – alles über einfache Namensverweise.*

↓

**[Schritt 3: Ein echtes Beispiel](anleitung/schritt-3-beispiel.md)** (10 Min.)
*Du öffnest einen fertigen Agent (Vertragsanalyse) und schaust dir jede Datei an. Am Ende machst du eine kleine Übung.*

↓

**[Schritt 4: Selber bauen](anleitung/schritt-4-eigener-agent.md)** (15 Min.)
*Du nimmst die leere Vorlage, füllst sie mit deinem eigenen Anwendungsfall aus und installierst deinen Agent in Cowork.*

---

## Was du in diesem Ordner siehst

```
workshop-agent-verstehen/
│
├── 📖 README.md                           ← Du bist hier
│
├── 📚 anleitung/                          ← Die 4 Schritte (der Reihe nach lesen)
│   ├── schritt-1-bausteine.md
│   ├── schritt-2-zusammenspiel.md
│   ├── schritt-3-beispiel.md
│   └── schritt-4-eigener-agent.md
│
├── 📗 beispiel-vertragsanalyse/           ← Ein FERTIGER Agent (zum Anschauen)
│   ├── .claude-plugin/plugin.json
│   ├── skills/vertragsanalyse/SKILL.md
│   ├── skills/zusammenfassung/SKILL.md
│   ├── agents/recherche-agent.md
│   └── commands/vertrag-pruefen/COMMAND.md
│
├── 📝 vorlage-leer/                       ← Eine LEERE Vorlage (zum Ausfüllen)
│   ├── .claude-plugin/plugin.json
│   ├── skills/hauptaufgabe/SKILL.md
│   ├── skills/ausgabe-erstellen/SKILL.md
│   ├── agents/helfer-agent.md
│   ├── commands/ausfuehren/COMMAND.md
│   └── .mcp.json
│
├── beispiel-vertragsanalyse.zip           ← Das Beispiel als ZIP
└── vorlage-leer.zip                       ← Die Vorlage als ZIP
```

Du brauchst dich jetzt nicht um die Dateien zu kümmern. Starte einfach mit Schritt 1:

→ **[Starte hier: Schritt 1](anleitung/schritt-1-bausteine.md)**
