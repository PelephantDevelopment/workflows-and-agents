# Workshop: «Ordner aufräumen» – Einen Agent in Claude Cowork bauen

> **Dauer:** 30 Minuten  
> **Zielgruppe:** Juristinnen und Juristen (keine technischen Vorkenntnisse nötig)  
> **Ziel:** Einen Agent bauen, der 50 chaotische Dateien automatisch sortiert – und ihn als geplante Aufgabe einrichten.

---

## Was du am Ende hast

Einen funktionierenden Agent, der:

- ✅ 50+ Dateien nach **Inhalt** liest (nicht nur Dateinamen)
- ✅ Automatisch in **Kategorien** sortiert (Verträge, Urteile, Fachartikel etc.)
- ✅ Dateien **einheitlich umbenennt** (`[Datum]_[Beschreibung].[ext]`)
- ✅ Bei unklaren Dokumenten im **Web recherchiert** (Sub-Agent)
- ✅ Eine **Inventarliste** erstellt mit Warnungen (vertraulich, Entwurf, Sicherheitsrisiko)
- ✅ **Jeden Freitag automatisch** läuft (geplante Aufgabe)

---

## Voraussetzungen

- [ ] Claude **Pro** ($20/Mo), **Max**, **Team** oder **Enterprise** Abo
- [ ] **Claude Desktop App** installiert → [claude.com/download](https://claude.com/download)
- [ ] macOS oder Windows

---

## Workshop-Ablauf

| Schritt | Was | Dauer | Anleitung |
|---------|-----|-------|-----------|
| **Vorbereitung** | Demo-Dateien entpacken | 2 Min. | Siehe unten |
| **Schritt 1** | Plugin verstehen, installieren und testen | 15–20 Min. | [→ schritt-1-skill-erstellen.md](anleitung/schritt-1-skill-erstellen.md) |
| **Schritt 2** | Als geplante Aufgabe einrichten | 5–10 Min. | [→ schritt-2-skill-planen.md](anleitung/schritt-2-skill-planen.md) |

---

## Vorbereitung: Demo-Dateien entpacken

1. Lade `workshop-dateien-chaos.zip` aus diesem Repo herunter
2. Entpacke die ZIP auf deinem Desktop
3. Du hast jetzt einen Ordner `workshop-dateien/` mit **50 chaotischen Dateien**:

| Kategorie | Anzahl | Sprachen |
|-----------|--------|----------|
| Verträge | 10 | DE, FR, EN |
| Urteile & Entscheide | 8 | DE, FR, EN |
| Fachartikel & Studien | 8 | DE, FR, EN |
| Korrespondenz & Notizen | 10 | DE |
| Rechnungen & Finanzen | 6 | DE, EN |
| Präsentationen | 4 | DE |
| Sonstiges | 4 | DE |

Die Dateien sind inhaltlich zusammenhängend – die gleiche Kanzlei, die gleichen Mandanten und Projekte tauchen in verschiedenen Dokumenttypen auf. Der Agent muss den Inhalt wirklich verstehen.

---

## Dateien in diesem Repo

```
workshop-ordner-aufraeumen/
│
├── README.md                                ← Diese Datei
│
├── anleitung/
│   ├── schritt-1-skill-erstellen.md         ← Schritt-für-Schritt: Plugin installieren
│   └── schritt-2-skill-planen.md            ← Schritt-für-Schritt: Geplante Aufgabe
│
├── plugin/
│   └── ordner-aufraeumen/                   ← Das fertige Plugin
│       ├── .claude-plugin/
│       │   └── plugin.json                  ← 🏷️ Manifest
│       ├── skills/
│       │   ├── datei-sortierung/
│       │   │   └── SKILL.md                 ← 🧠 Hauptlogik: Sortieren
│       │   └── inventar/
│       │       └── SKILL.md                 ← 🧠 Inventarliste erstellen
│       ├── agents/
│       │   └── dokument-checker.md          ← 🤖 Sub-Agent: Unklare Dateien prüfen
│       └── commands/
│           └── sortieren/
│               └── COMMAND.md               ← ⚡ Slash-Command: Workflow starten
│
├── workshop-dateien-chaos.zip               ← 50 Demo-Dateien (entpacken!)
├── ordner-aufraeumen-plugin.zip             ← Plugin als ZIP (zum Verteilen)
│
└── demo-dateien/
    └── generate_workshop_files.py           ← Script: Demo-Dateien selbst generieren
```

---

## So spielen die Plugin-Bausteine zusammen

```
DU: "Sortiere diesen Ordner"  (oder /ordner-aufraeumen:sortieren)
│
├──→ 🧠 SKILL: datei-sortierung
│       Liest 50 Dateien, erkennt Dokumenttyp, erstellt Ordner, verschiebt
│       │
│       └──→ 🤖 SUB-AGENT: dokument-checker
│               Recherchiert im Web bei unklaren Dokumenten (z.B. "Was ist BGE 148 II 137?")
│               Gibt Kategorisierungs-Empfehlung zurück an Skill 1
│
└──→ 🧠 SKILL: inventar
        Nutzt Ergebnisse von Skill 1 + Sub-Agent
        Erstellt 00_INVENTAR.md mit Übersicht und Warnungen
│
▼
ERGEBNIS: Sauberer Ordner + Inventarliste + Warnungen
```

---

### Mögliche Fragen der Teilnehmenden

| Frage | Antwort |
|-------|---------|
| «Kann Claude meine Dateien löschen?» | Claude fragt immer um Erlaubnis vor dem Löschen. Unser Plugin löscht nie – es verschiebt nur. |
| «Funktioniert das auch mit 500 Dateien?» | Ja, braucht einfach länger. Bei sehr grossen Ordnern empfiehlt sich die geplante Aufgabe. |
| «Sieht Anthropic meine Dateien?» | Cowork läuft lokal. Dateien werden nicht zu Anthropic hochgeladen (aber Inhalte werden für die KI-Verarbeitung übermittelt). |
| «Kann ich die Kategorien anpassen?» | Ja! Öffne `skills/datei-sortierung/SKILL.md` in einem Texteditor und passe die Tabelle an. |
| «Funktioniert das auf dem Handy?» | Nein, Cowork gibt es nur in der Desktop App (macOS/Windows). |
