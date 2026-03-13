# Schritt 3: Ein echtes Beispiel durchgehen

> **Dauer:** ca. 10 Minuten  
> **Was du brauchst:** Einen Texteditor und den Ordner `beispiel-vertragsanalyse/` aus diesem Repo  
> **Was du danach weisst:** Wie ein fertiger Agent von innen aussieht.

---

## Was wir jetzt tun

Du öffnest den Ordner `beispiel-vertragsanalyse/` und schaust dir **jede der 5 Dateien** an. Für jede Datei erkläre ich, was drinsteht und warum.

Der Agent heisst «Vertragsanalyse» und tut folgendes: Du gibst ihm einen Vertrag, und er liefert eine Klausel-für-Klausel-Analyse mit Ampelsystem (🟢🟡🔴), recherchierte Rechtsgrundlagen und eine 1-seitige Management-Zusammenfassung.

---

## Vorbereitung

Öffne jetzt den Ordner `beispiel-vertragsanalyse/` in deinem Datei-Explorer. Du siehst:

```
beispiel-vertragsanalyse/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   ├── vertragsanalyse/
│   │   └── SKILL.md
│   └── zusammenfassung/
│       └── SKILL.md
├── agents/
│   └── recherche-agent.md
└── commands/
    └── vertrag-pruefen/
        └── COMMAND.md
```

**Hinweis:** Der Ordner `.claude-plugin` beginnt mit einem Punkt. Auf manchen Systemen ist er deshalb versteckt. Auf dem Mac: drücke `Cmd + Shift + .` um versteckte Dateien anzuzeigen. Auf Windows: Im Explorer → Ansicht → «Ausgeblendete Elemente» aktivieren.

---

## Datei 1 von 5: Das Manifest

📂 **Öffne jetzt:** `.claude-plugin/plugin.json`

```json
{
  "name": "vertragsanalyse-agent",
  "description": "Analysiert Verträge auf Risiken, fehlende Klauseln 
                  und Abweichungen vom Standard. Erstellt eine 
                  strukturierte Risikoübersicht und eine 
                  Management-Zusammenfassung.",
  "version": "1.0.0",
  "author": {
    "name": "EIZ Legaltech Workshop"
  }
}
```

**Was du hier siehst:**
- `name`: Der technische Name des Agents (Kleinbuchstaben, Bindestriche)
- `description`: Was der Agent tut – das sieht man in der Plugin-Verwaltung von Cowork
- `version` und `author`: Zusatzinfos

**Das war schon Datei 1.** Schliesse sie und öffne die nächste.

---

## Datei 2 von 5: Skill «vertragsanalyse» (die Hauptarbeit)

📂 **Öffne jetzt:** `skills/vertragsanalyse/SKILL.md`

Das ist die längste Datei – die Kernlogik des Agents. Scrolle durch und achte auf folgende Abschnitte:

**Der Kopf (YAML-Header):**
```yaml
---
name: vertragsanalyse
description: >
  Analysiert Verträge auf Risiken, fehlende Klauseln...
  Aktiviert sich wenn der Nutzer einen Vertrag prüfen möchte...
---
```
→ Der `name` ist wichtig – er wird später vom Command und vom zweiten Skill referenziert.
→ Die `description` sagt Claude, *wann* er diesen Skill nutzen soll.

**Die Prüf-Checkliste:**

Scrolle zum Abschnitt «Prüf-Checkliste». Du findest eine Tabelle mit 14 Klauselkategorien:

| # | Klausel | Worauf achten |
|---|---------|---------------|
| 1 | Vertragsparteien | Korrekte Bezeichnung, Vertretungsbefugnis |
| 2 | Vertragsgegenstand | Klar definiert, keine Mehrdeutigkeiten |
| ... | ... | ... |

Das ist das Herz des Skills – hier steckt das juristische Fachwissen.

**Die Delegation an den Sub-Agent:**

Scrolle zum Abschnitt «4. Rechtsgrundlagen». Dort steht:

```markdown
Delegiere an den **recherche-agent**: Suche nach relevanten 
Rechtsgrundlagen und aktueller Rechtsprechung...
```

→ Hier ist die **Verbindung zu Datei 4** (dem Sub-Agent). Claude liest «recherche-agent» und weiss, dass er `agents/recherche-agent.md` aufrufen soll.

**Schliesse die Datei und öffne die nächste.**

---

## Datei 3 von 5: Skill «zusammenfassung» (das Endergebnis)

📂 **Öffne jetzt:** `skills/zusammenfassung/SKILL.md`

Dieser Skill kommt am Ende des Workflows. Achte auf:

**Die Voraussetzung (ganz oben):**
```markdown
## Voraussetzung
Dieser Skill nutzt die **Ergebnisse der Vertragsanalyse** 
(Skill «vertragsanalyse»). Falls noch keine Analyse vorliegt, 
führe zuerst die Vertragsanalyse durch.
```

→ Hier ist die **Verbindung zu Datei 2** (dem ersten Skill). Claude weiss: «Ich brauche die Ergebnisse von «vertragsanalyse», bevor ich arbeiten kann.»

**Das Ausgabeformat:**

Scrolle zum Ausgabeformat. Du siehst eine Vorlage für eine 1-seitige Zusammenfassung:

```markdown
**Gesamtbewertung:** 🟢/🟡/🔴 [Ein Satz]
**Empfehlung:** Unterzeichnen / Nachverhandeln / Ablehnen
```

→ Das ist das Ergebnis, das der Nutzer am Ende bekommt.

**Schliesse die Datei und öffne die nächste.**

---

## Datei 4 von 5: Sub-Agent «recherche-agent» (der Helfer)

📂 **Öffne jetzt:** `agents/recherche-agent.md`

Achte auf den Kopf – er hat mehr Felder als ein Skill:

```yaml
---
name: recherche-agent
model: sonnet         ← Eigenes Modell (Sonnet = schnell und günstig)
tools:
  - WebSearch         ← Darf im Internet suchen
  - Read              ← Darf Dateien lesen
---
```

→ Der Sub-Agent hat **eigene Werkzeuge** – er darf im Web suchen. Das kann der Haupt-Skill nicht.

**Die Aufgabe:**

Der Agent weiss, dass er vom Skill «vertragsanalyse» aufgerufen wird:

```markdown
Du wirst vom Haupt-Agent aufgerufen, wenn dieser während 
einer Vertragsanalyse relevante Rechtsgrundlagen benötigt.
```

→ Er bekommt eine Anfrage wie «Suche Rechtsgrundlagen zu Haftungsbeschränkungen» und liefert Gesetzesartikel und BGE zurück.

**Schliesse die Datei und öffne die letzte.**

---

## Datei 5 von 5: Command «vertrag-pruefen» (der Startknopf)

📂 **Öffne jetzt:** `commands/vertrag-pruefen/COMMAND.md`

Das ist der kürzeste Teil – der Command orchestriert nur:

```markdown
## Schritt 1: Vertragsanalyse
Nutze den Skill **«vertragsanalyse»**...

## Schritt 2: Rechtsgrundlagen recherchieren
Delegiere an den **«recherche-agent»**...

## Schritt 3: Management-Zusammenfassung
Nutze den Skill **«zusammenfassung»**...
```

→ Drei Schritte, drei Verweise auf die anderen Dateien. Der Command ist der **Regisseur**, der alles in der richtigen Reihenfolge startet.

**Aufruf wäre:** `/vertragsanalyse-agent:vertrag-pruefen NDA_Vertrag.pdf`

---

## Zusammenfassung: Alle Verbindungen auf einen Blick

Jetzt hast du alle 5 Dateien gesehen. Hier nochmal, wer wen referenziert:

```
📄 Command (vertrag-pruefen)
│    referenziert → 🧠 Skill «vertragsanalyse»
│    referenziert → 🤖 Agent «recherche-agent»
│    referenziert → 🧠 Skill «zusammenfassung»
│
🧠 Skill «vertragsanalyse»
│    delegiert an → 🤖 Agent «recherche-agent»
│
🤖 Agent «recherche-agent»
│    liefert Ergebnisse an → 🧠 Skill «vertragsanalyse»
│
🧠 Skill «zusammenfassung»
│    nutzt Ergebnisse von → 🧠 Skill «vertragsanalyse»
│    nutzt Ergebnisse von → 🤖 Agent «recherche-agent»
```

---

## Übung: Teste dein Verständnis

Beantworte diese Fragen, indem du die Dateien nochmal öffnest:

1. In welcher Datei steht die Prüf-Checkliste mit 14 Klauseln?
2. Welches Modell nutzt der Sub-Agent?
3. Was passiert, wenn der Command den Skill «zusammenfassung» VOR dem Skill «vertragsanalyse» aufrufen würde?
4. Welche zwei Tools hat der Sub-Agent, die der Haupt-Skill nicht hat?
5. Wo steht die Anweisung, dass die Zusammenfassung maximal 1 Seite lang sein soll?

<details>
<summary>→ Klicke hier für die Antworten</summary>

1. In `skills/vertragsanalyse/SKILL.md` – Abschnitt «Prüf-Checkliste»
2. `sonnet` (steht im YAML-Header von `agents/recherche-agent.md`)
3. Die Zusammenfassung hätte keine Daten zum Zusammenfassen – sie braucht die Ergebnisse von Skill 1
4. `WebSearch` und `Read`
5. In `skills/zusammenfassung/SKILL.md` – bei den Regeln: «Maximal 1 Seite»

</details>

---

## Nächster Schritt

Du hast ein echtes Beispiel von innen gesehen. Jetzt bist du dran – im nächsten Schritt nimmst du die **leere Vorlage** und baust deinen **eigenen Agent**.

→ **[Weiter zu Schritt 4: Eigenen Agent bauen](schritt-4-eigener-agent.md)**
