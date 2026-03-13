# Schritt 2: Wie die Bausteine zusammenspielen

> **Dauer:** ca. 10 Minuten  
> **Was du danach weisst:** Wie die Teile sich gegenseitig aufrufen – und dass die Verbindung nichts anderes ist als ein Name in einer Textdatei.

---

## Das Prinzip in einem Satz

Die Bausteine eines Agents sind über **Namen** miteinander verbunden. Wenn in einer Datei steht «Delegiere an den **helfer-agent**», dann sucht Claude die Datei `agents/helfer-agent.md` und ruft sie auf.

Das ist alles. Keine Konfiguration, keine Programmierung. Nur ein Name in einem Satz.

---

## Die drei Verbindungsarten

Es gibt genau drei Arten, wie sich Bausteine gegenseitig aufrufen können. Schauen wir sie uns der Reihe nach an.

---

### Verbindung 1: Command ruft Skills auf

Ein Command ist der Startpunkt eines Workflows. Er sagt: «Mache erst das, dann das, dann das.»

**So sieht das in der Datei aus:**

```markdown
# In commands/ausfuehren/COMMAND.md:

## Schritt 1
Nutze den Skill **«hauptaufgabe»** und analysiere den Vertrag.

## Schritt 2
Nutze den Skill **«ausgabe-erstellen»** und erstelle eine Zusammenfassung.
```

Claude liest «Skill «hauptaufgabe»» und sucht automatisch die Datei `skills/hauptaufgabe/SKILL.md`.

**Probiere es aus:** Öffne die Datei `beispiel-vertragsanalyse/commands/vertrag-pruefen/COMMAND.md` in deinem Texteditor. Suche nach den Stellen, wo Skills referenziert werden. Du wirst finden:
- «Skill **«vertragsanalyse»**» → zeigt auf `skills/vertragsanalyse/SKILL.md`
- «Skill **«zusammenfassung»**» → zeigt auf `skills/zusammenfassung/SKILL.md`

---

### Verbindung 2: Skill ruft Sub-Agent auf

Ein Skill kann mitten in seiner Arbeit sagen: «Für diesen Teil brauche ich Hilfe» – und eine Aufgabe an einen Sub-Agent delegieren.

**So sieht das in der Datei aus:**

```markdown
# In skills/hauptaufgabe/SKILL.md:

### 4. Teilaufgabe delegieren
Delegiere an den **helfer-agent**: Suche relevante Rechtsgrundlagen
zu den identifizierten Risiken.
```

Claude liest «helfer-agent» und sucht die Datei `agents/helfer-agent.md`.

**Probiere es aus:** Öffne `beispiel-vertragsanalyse/skills/vertragsanalyse/SKILL.md`. Scrolle zum Abschnitt «4. Rechtsgrundlagen». Du findest dort den Verweis auf den «recherche-agent».

---

### Verbindung 3: Skill nutzt Ergebnisse eines anderen Skills

Ein Skill kann sagen: «Ich brauche die Ergebnisse von Skill 1, bevor ich arbeiten kann.»

**So sieht das in der Datei aus:**

```markdown
# In skills/ausgabe-erstellen/SKILL.md:

## Voraussetzung
Dieser Skill nutzt die **Ergebnisse aus dem Skill «hauptaufgabe»**
und die **Recherche-Ergebnisse des «helfer-agent»**.
```

**Probiere es aus:** Öffne `beispiel-vertragsanalyse/skills/zusammenfassung/SKILL.md`. Ganz oben findest du die Voraussetzung, die auf den Skill «vertragsanalyse» verweist.

---

## Alles zusammen: Der Ablauf

Jetzt setzen wir die drei Verbindungen zusammen. So läuft ein vollständiger Agent ab:

```
DU tippst: /mein-agent:ausfuehren Vertrag.pdf
│
│  ① Command liest deine Eingabe
│
│  "Nutze Skill «hauptaufgabe»"
│  ─────────────────────────────────────────────┐
│                                               ▼
│                                    ┌─────────────────────┐
│                                    │ 🧠 SKILL 1           │
│                                    │ «hauptaufgabe»       │
│                                    │                      │
│                                    │ Liest den Vertrag    │
│                                    │ Prüft die Checkliste │
│                                    │ Bewertet 🟢🟡🔴       │
│                                    │                      │
│                                    │ "Ich brauche Hilfe   │
│                                    │  bei der Recherche"  │
│                                    │         │            │
│                                    └─────────┼────────────┘
│                                              │
│                                    ② "Delegiere an «helfer-agent»"
│                                              │
│                                              ▼
│                                    ┌─────────────────────┐
│                                    │ 🤖 SUB-AGENT         │
│                                    │ «helfer-agent»       │
│                                    │                      │
│                                    │ Eigenes Modell       │
│                                    │ Eigene Tools         │
│                                    │ (z.B. Web-Suche)     │
│                                    │                      │
│                                    │ Recherchiert...      │
│                                    │         │            │
│                                    └─────────┼────────────┘
│                                              │
│                                    ③ Ergebnisse zurück an Skill 1
│                                              │
│                                              ▼
│                                    Skill 1 baut Ergebnisse ein
│
│  "Nutze Skill «ausgabe-erstellen»"
│  ─────────────────────────────────────────────┐
│                                               ▼
│                                    ┌─────────────────────┐
│                                    │ 🧠 SKILL 2           │
│                                    │ «ausgabe-erstellen»  │
│                                    │                      │
│                                    │ ④ Liest Ergebnisse   │
│                                    │ von Skill 1 + Agent  │
│                                    │                      │
│                                    │ Erstellt Endergebnis │
│                                    └─────────────────────┘
│
▼
ERGEBNIS wird an dich geliefert
```

---

## Die goldene Regel

**Verbindung = ein Name in Anführungszeichen.**

| Wenn du schreibst... | ...sucht Claude |
|----------------------|-----------------|
| `Skill **«hauptaufgabe»**` | `skills/hauptaufgabe/SKILL.md` |
| `Skill **«zusammenfassung»**` | `skills/zusammenfassung/SKILL.md` |
| `**recherche-agent**` | `agents/recherche-agent.md` |

Der Name in deiner Datei muss mit dem `name`-Feld im YAML-Header der Zieldatei übereinstimmen. Wenn dort steht `name: recherche-agent`, dann schreibst du in deinem Skill «Delegiere an den **recherche-agent**».

---

## Selbsttest: Verbindungen finden

Beantworte, ohne ins Beispiel zu schauen:

1. Wenn ein Skill einen Sub-Agent aufrufen will, was schreibt er in die Datei?
2. Woher weiss Claude, welche Datei zum Namen «recherche-agent» gehört?
3. Was passiert, wenn du den Namen falsch schreibst (z.B. «rechercheagent» statt «recherche-agent»)?

<details>
<summary>→ Klicke hier für die Antworten</summary>

1. Er schreibt z.B.: «Delegiere an den **recherche-agent**: [Aufgabe]» – einfach den Namen im Text erwähnen.
2. Claude sucht in `agents/` nach einer Datei, deren `name`-Feld im YAML-Header übereinstimmt.
3. Claude findet den Agent nicht und macht entweder die Aufgabe selbst oder fragt nach. Deshalb: **Namen immer genau gleich schreiben.**

</details>

---

## Nächster Schritt

Du verstehst jetzt die Theorie. Im nächsten Schritt öffnest du einen **echten, fertigen Agent** und schaust dir jede Datei an – damit du siehst, wie das in der Praxis aussieht.

→ **[Weiter zu Schritt 3: Ein echtes Beispiel](schritt-3-beispiel.md)**
