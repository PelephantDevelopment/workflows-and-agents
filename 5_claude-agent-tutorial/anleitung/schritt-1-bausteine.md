# Schritt 1: Die Bausteine eines Agents

> **Dauer:** ca. 10 Minuten  
> **Was du danach weisst:** Aus welchen Teilen ein Agent besteht – und dass du dafür kein Wort Code brauchst.

---

## Zuerst: Was ist überhaupt ein «Agent»?

Im normalen Claude-Chat funktioniert es so:
1. Du schreibst eine Nachricht
2. Claude antwortet
3. Du schreibst die nächste Nachricht
4. Claude antwortet
5. ...und so weiter

Du bist der **Projektmanager** – du steuerst jeden Schritt.

Ein **Agent** dreht das um: Du beschreibst einmal, was du willst, und Claude arbeitet selbstständig. Er plant die Schritte, führt sie aus, holt sich bei Bedarf Hilfe und liefert am Ende ein fertiges Ergebnis.

Damit Claude das kann, braucht er **Anweisungen** – und genau die schreiben wir in ein sogenanntes **Plugin**.

---

## Ein Plugin ist ein Ordner mit Textdateien

Das ist die zentrale Erkenntnis dieses Schritts. Kein Programm. Keine Datenbank. Kein Code. Nur ein Ordner auf deinem Computer mit ein paar Markdown-Dateien drin.

So sieht ein Plugin aus, wenn du es im Datei-Explorer öffnest:

```
mein-agent/
├── .claude-plugin/
│   └── plugin.json        ← 1 Datei
├── skills/
│   └── mein-skill/
│       └── SKILL.md       ← 1 Datei
├── agents/
│   └── mein-helfer.md     ← 1 Datei
└── commands/
    └── starten/
        └── COMMAND.md     ← 1 Datei
```

Vier Dateien. Alle kannst du in TextEdit oder Notepad öffnen und lesen. Das war's.

---

## Die 5 Bausteine im Detail

Ein Plugin kann bis zu 5 verschiedene Bausteine enthalten. Aber – und das ist wichtig – **nur 2 davon sind Pflicht**. Die anderen 3 sind optional.

---

### 🏷️ Baustein 1: Das Manifest (Pflicht)

**Datei:** `.claude-plugin/plugin.json`  
**Was es tut:** Sagt Claude, wie der Agent heisst und was er tut.  
**Analogie:** Die Visitenkarte deines Agents.

Öffne jetzt die Datei aus dem Beispiel. Navigiere zu:
`beispiel-vertragsanalyse/.claude-plugin/plugin.json`

Du siehst:
```json
{
  "name": "vertragsanalyse-agent",
  "description": "Analysiert Verträge auf Risiken...",
  "version": "1.0.0",
  "author": { "name": "EIZ Legaltech Workshop" }
}
```

Das ist alles. Drei Informationen: Name, Beschreibung, Autor. Das kannst du in 30 Sekunden schreiben.

---

### 🧠 Baustein 2: Skills (Pflicht – mindestens einer)

**Datei:** `skills/[name]/SKILL.md`  
**Was es tut:** Enthält die Arbeitsanweisungen für Claude – was er tun soll, Schritt für Schritt.  
**Analogie:** Ein Handbuch für einen neuen Mitarbeiter.

Ein Skill hat zwei Teile:

**Teil 1: Der Kopf (YAML-Header)** – sagt Claude, *wann* er den Skill nutzen soll:
```markdown
---
name: vertragsanalyse
description: Aktiviert sich wenn Verträge analysiert werden sollen.
---
```

**Teil 2: Die Anweisungen** – sagen Claude, *was* er tun soll:
```markdown
# Vertragsanalyse

Du analysierst Verträge systematisch...

## Vorgehen
1. Lies den Vertrag
2. Prüfe jede Klausel
3. Bewerte mit 🟢🟡🔴
...
```

Das Wichtige: Claude liest den `description`-Text und entscheidet **automatisch**, ob der Skill zur aktuellen Aufgabe passt. Wenn du in Cowork sagst «Prüfe diesen Vertrag», erkennt Claude: «Ah, der Skill vertragsanalyse passt hier» – und nutzt ihn, ohne dass du ihn explizit aufrufen musst.

**Du kannst beliebig viele Skills haben.** Jeder liegt in einem eigenen Ordner unter `skills/`.

---

### 🤖 Baustein 3: Sub-Agents (Optional)

**Datei:** `agents/[name].md`  
**Was es tut:** Definiert einen spezialisierten Helfer mit eigenem Modell und eigenen Werkzeugen.  
**Analogie:** Ein Teammitglied mit einer Spezialaufgabe, z.B. ein Recherche-Assistent.

Der Unterschied zwischen Skill und Sub-Agent:

| | Skill | Sub-Agent |
|---|-------|-----------|
| **Ist wie...** | Ein Kapitel im Handbuch | Ein eigener Mitarbeiter |
| **Arbeitet mit** | Dem gleichen Claude | Einem eigenen Claude |
| **Hat eigene Werkzeuge** | Nein | Ja (z.B. Web-Suche) |
| **Gut für** | Regeln und Prozesse | Recherche, Spezialaufgaben |

Ein Sub-Agent hat im Kopf zusätzliche Angaben:
```markdown
---
name: recherche-agent
model: sonnet              ← Welches Claude-Modell?
tools:
  - WebSearch              ← Darf im Internet suchen
  - Read                   ← Darf Dateien lesen
---
```

**Wann brauchst du einen Sub-Agent?** Wenn eine Teilaufgabe eigene Werkzeuge braucht (z.B. Web-Suche) oder wenn sie parallel und unabhängig erledigt werden soll.

**Wann brauchst du keinen?** Wenn Claude alles mit einem Skill erledigen kann. Die meisten einfachen Agents kommen ohne Sub-Agent aus.

---

### ⚡ Baustein 4: Commands / Slash-Befehle (Optional)

**Datei:** `commands/[name]/COMMAND.md`  
**Was es tut:** Definiert einen Slash-Befehl, den du per `/` aufrufst.  
**Analogie:** Ein Startknopf, der einen ganzen Workflow auslöst.

Der Ordnername wird zum Befehl. Beispiel:
```
commands/vertrag-pruefen/COMMAND.md  →  /vertragsanalyse-agent:vertrag-pruefen
```

Ein Command sagt Claude: «Nutze erst diesen Skill, dann jenen Agent, dann jenen Skill – in dieser Reihenfolge.» Er ist der **Regisseur**, der alles orchestriert.

**Brauchst du einen Command?** Nicht unbedingt. Skills feuern auch automatisch. Aber ein Command ist praktisch, wenn du einen mehrstufigen Workflow per Knopfdruck starten willst.

---

### 🔌 Baustein 5: Connectors (Optional)

**Datei:** `.mcp.json`  
**Was es tut:** Verbindet deinen Agent mit externen Diensten (Gmail, Google Drive, Slack etc.)  
**Analogie:** Telefonanschlüsse ins Büro deines Mitarbeiters.

Connectors werden hauptsächlich in der **Claude Desktop App** eingerichtet (Einstellungen → Connectors), nicht in der Datei. Die `.mcp.json` ist nur eine Erinnerung, welche Verbindungen dein Plugin braucht.

**Brauchst du Connectors?** Nur wenn dein Agent auf externe Dienste zugreifen soll. Für den Anfang: Nein.

---

## Zusammenfassung: Was brauche ich mindestens?

Nur **zwei Dateien**:

```
mein-agent/
├── .claude-plugin/
│   └── plugin.json     ← Pflicht: Wer bin ich?
└── skills/
    └── mein-skill/
        └── SKILL.md    ← Pflicht: Was kann ich?
```

Alles andere – Sub-Agents, Commands, Connectors – ist **optional** und kommt dazu, wenn dein Agent komplexer wird.

---

## Selbsttest: Hast du alles verstanden?

Beantworte kurz für dich:

1. Was ist der Unterschied zwischen einem Skill und einem Sub-Agent?
2. Warum braucht man nicht zwingend einen Command?
3. Wie viele Dateien braucht man mindestens für einen funktionierenden Agent?

<details>
<summary>→ Klicke hier für die Antworten</summary>

1. Ein **Skill** ist eine Anleitung, die Claude befolgt (wie ein Handbuch-Kapitel). Ein **Sub-Agent** ist ein eigenständiger Helfer mit eigenem Modell und eigenen Werkzeugen (wie ein Teammitglied).
2. Weil **Skills automatisch feuern** – Claude erkennt anhand der Beschreibung, ob ein Skill zur Aufgabe passt. Ein Command ist nur ein optionaler «Startknopf».
3. **Zwei:** `plugin.json` (Manifest) + eine `SKILL.md` (mindestens ein Skill).

</details>

---

## Nächster Schritt

Du weisst jetzt, aus welchen Teilen ein Agent besteht. Im nächsten Schritt schauen wir uns an, wie diese Teile **zusammenspielen** – wie ein Skill einen Helfer aufruft und wie ein Command alles orchestriert.

→ **[Weiter zu Schritt 2: Das Zusammenspiel](schritt-2-zusammenspiel.md)**
