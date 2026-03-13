# Schritt 1: Skill erstellen und als Plugin installieren

> **Dauer:** 15–20 Minuten  
> **Was du lernst:** Wie ein Cowork-Plugin aufgebaut ist und wie du es installierst.

---

## Was du brauchst

- [ ] Claude Desktop App installiert und eingeloggt ([claude.com/download](https://claude.com/download))
- [ ] Claude Pro, Max, Team oder Enterprise Abo
- [ ] Die Datei `workshop-dateien-chaos.zip` entpackt auf deinem Desktop
- [ ] Die Datei `plugin/ordner-aufraeumen/` aus diesem Repo (oder die ZIP `ordner-aufraeumen-plugin.zip`)

---

## Teil A: Verstehen was ein Plugin ist

Ein Plugin besteht aus **Textdateien in einer bestimmten Ordnerstruktur**. Kein Code, kein Build-Prozess. Alles was Claude wissen muss, steht in Markdown-Dateien.

Unser Plugin «ordner-aufraeumen» hat diese Struktur:

```
ordner-aufraeumen/
│
├── .claude-plugin/
│   └── plugin.json               ← Wer bin ich?
│
├── skills/
│   ├── datei-sortierung/
│   │   └── SKILL.md              ← 🧠 Wie sortiere ich Dateien?
│   └── inventar/
│       └── SKILL.md              ← 🧠 Wie erstelle ich eine Inventarliste?
│
├── agents/
│   └── dokument-checker.md       ← 🤖 Wer hilft bei unklaren Dateien?
│
└── commands/
    └── sortieren/
        └── COMMAND.md            ← ⚡ Wie starte ich alles auf einmal?
```

### Wie die Bausteine zusammenspielen:

```
DU: "Sortiere diesen Ordner"
         │
         ▼
⚡ Command: /ordner-aufraeumen:sortieren
         │
         ├──→ 🧠 Skill: datei-sortierung
         │       • Liest jede Datei
         │       • Erkennt den Dokumenttyp
         │       • Erstellt Unterordner
         │       • Verschiebt und benennt um
         │       │
         │       └──→ 🤖 Sub-Agent: dokument-checker
         │               • Erhält unklare Dateien
         │               • Recherchiert im Web
         │               • Gibt Empfehlung zurück
         │
         └──→ 🧠 Skill: inventar
                 • Liest alle Ergebnisse
                 • Erstellt 00_INVENTAR.md
                 • Markiert Warnungen (⚠📝)
         
         ▼
ERGEBNIS: Sauberer Ordner + Inventarliste
```

---

## Teil B: Plugin installieren

### Option 1: Fertige ZIP hochladen (empfohlen für den Workshop)

1. Lade `ordner-aufraeumen-plugin.zip` herunter (aus diesem Repo)
2. Entpacke die ZIP-Datei
3. Öffne die **Claude Desktop App**
4. Wechsle zum Tab **«Cowork»**
5. Klicke links in der Sidebar auf **«Customize»**
6. Klicke auf **«Browse plugins»**
7. Klicke auf **«Upload»** (oder «Eigenes Plugin hochladen»)
8. Navigiere zum entpackten Ordner **`ordner-aufraeumen/`** und wähle ihn
9. ✅ Das Plugin ist installiert

### Option 2: Plugin selbst zusammenbauen

Falls du das Plugin von Grund auf erstellen willst (z.B. als Übung):

1. Erstelle einen neuen Ordner `ordner-aufraeumen/` auf deinem Desktop

2. Erstelle darin die Unterordner:
   ```
   ordner-aufraeumen/
   ├── .claude-plugin/
   ├── skills/
   │   ├── datei-sortierung/
   │   └── inventar/
   ├── agents/
   └── commands/
       └── sortieren/
   ```

3. Kopiere die Dateien aus dem Repo in die entsprechenden Ordner (oder tippe sie ab – sie sind alle in Markdown)

4. Installiere das Plugin wie in Option 1 beschrieben

---

## Teil C: Plugin testen

### Test 1: Automatischer Skill (natürliche Sprache)

1. Klicke auf **«+ New task»** in Cowork
2. Wähle den Ordner **`workshop-dateien/`** (die entpackten 50 Chaos-Dateien) als Arbeitsordner
3. Tippe:
   ```
   Bitte sortiere alle Dateien in diesem Ordner.
   ```
4. Claude erkennt automatisch, dass der Skill «datei-sortierung» relevant ist
5. Claude zeigt seinen Plan → bestätige
6. Schaue zu, wie Claude arbeitet

### Test 2: Per Slash-Command

1. Starte einen neuen Task
2. Wähle wieder den Ordner `workshop-dateien/`
3. Tippe:
   ```
   /ordner-aufraeumen:sortieren
   ```
4. Der Command startet den kompletten Workflow (Sortierung → Dokument-Check → Inventar)

### Test 3: Nur Inventar (ohne Sortierung)

1. Starte einen neuen Task
2. Tippe:
   ```
   Erstelle mir eine Übersicht aller Dateien in diesem Ordner, ohne etwas zu verschieben.
   ```
3. Claude nutzt nur den Skill «inventar» – liest alles, verschiebt nichts

---

## Teil D: Was du sehen solltest

### Vorher (Chaos):
```
workshop-dateien/
├── NDA_Project_Alpha_unsigned.docx
├── BGE_148_II_137.pdf
├── Rechnung_2024-0847.pdf
├── scan0042.txt
├── passwörter_NICHT_LÖSCHEN.txt
├── ... (50 Dateien durcheinander)
```

### Nachher (sortiert):
```
workshop-dateien/
├── 00_INVENTAR.md                           ← Inventarliste
├── 01_Vertraege/
│   ├── 2026-02-15_NDA_TechVision_InnoSoft.docx
│   ├── 2026-01-01_Dienstleistungsvertrag_Meier_DataFlow.docx
│   ├── 2025-04-01_Mietvertrag_Talstrasse.docx
│   └── ... (10 Dateien)
├── 02_Urteile/
│   ├── 2022-03-22_BGE_148_II_137_Auskunftsrecht.pdf
│   ├── 2026-01-15_Urteil_HGer_ZH_NDA_Verletzung.pdf
│   └── ... (8 Dateien)
├── 03_Fachartikel/
│   └── ... (8 Dateien)
├── 04_Korrespondenz/
│   └── ... (10 Dateien)
├── 05_Rechnungen/
│   └── ... (6 Dateien)
├── 06_Praesentationen/
│   └── ... (4 Dateien)
├── 07_Personal/
│   └── 2024-00-00_Lebenslauf_Anna_Lisa_Berger.docx
└── 08_Sonstiges/
    └── 0000-00-00_Passwoerter_SICHERHEITSRISIKO.txt  ← ⚠
```

### Die Inventarliste (00_INVENTAR.md):

```markdown
# Inventar – Sortierung vom 13.03.2026

## Zusammenfassung
| Kategorie | Anzahl |
|-----------|--------|
| 01 Verträge | 10 |
| 02 Urteile | 8 |
| ... | ... |
| **Total** | **50** |

## Warnungen
- ⚠ VERTRAULICH: Kaufvertrag_Geschaeftsanteile_VERTRAULICH.pdf
- ⚠ VERTRAULICH: memo_intern_due_diligence.docx – Anwaltsprivileg
- 📝 ENTWURF: Lizenzvertrag_Software_Draft2.docx
- 📝 ENTWURF: gutachten_entwurf_ki_berufsgeheimnis.docx
- ⚠ SICHERHEITSRISIKO: passwörter_NICHT_LÖSCHEN.txt – Klartext-Passwörter
```

---

## Troubleshooting

**«Cowork» Tab fehlt in der App:**  
→ App aktualisieren. Auf macOS: Apple Silicon (M1+) nötig. Windows: alle Geräte unterstützt.

**Plugin erscheint nicht nach Upload:**  
→ Prüfe ob `plugin.json` im Ordner `.claude-plugin/` liegt (mit Punkt am Anfang!). Auf manchen Systemen werden Ordner mit Punkt versteckt.

**Claude sortiert nicht richtig:**  
→ Die Skills feuern automatisch basierend auf der `description`. Versuche den Slash-Command `/ordner-aufraeumen:sortieren` für explizites Auslösen.

**«Datei XY wurde nicht erkannt»:**  
→ Der dokument-checker Sub-Agent sollte bei unklaren Dateien einspringen. Falls nicht: Starte den Task erneut und sage explizit «Prüfe auch die unklaren Dateien im Web».

---

## Nächster Schritt

Wenn die Sortierung funktioniert → weiter zu [**Schritt 2: Skill planen (Scheduled Task)**](schritt-2-skill-planen.md)
