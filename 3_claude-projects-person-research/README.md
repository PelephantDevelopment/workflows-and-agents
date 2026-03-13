# Workshop: Personen-Dossier mit Claude Projects

> **Dauer:** 45 Minuten  
> **Zielgruppe:** Juristinnen und Juristen  
> **Ziel:** Ein Claude-Projekt erstellen, das auf Knopfdruck strukturierte Personen-Dossiers mit PowerPoint-Ausgabe generiert.

---

## Übersicht

In diesem Workshop bauen Sie Schritt für Schritt ein Claude-Projekt auf, das als «Recherche-Maschine» für Gesprächsvorbereitungen funktioniert. Am Ende haben Sie ein wiederverwendbares Werkzeug, das:

- Personen anhand von Name und Organisation recherchiert
- Ein strukturiertes Dossier im Chat ausgibt
- Eine PowerPoint-Präsentation im Corporate Design generiert
- Fotos der Personen auf den Folien platziert

### Was Sie brauchen

- Einen Claude-Account mit **Pro- oder Team-Abo** (für Projects)
- Zugang zu [claude.ai](https://claude.ai)
- Die Dateien aus diesem Repository

### Aufbau

| Schritt | Was passiert | Dauer |
|---------|-------------|-------|
| [Schritt 1](#schritt-1-recherche-im-chat) | Einfache Personen-Recherche im Chat | 10 Min. |
| [Schritt 2](#schritt-2-powerpoint-ausgabe-ergänzen) | Anweisung erweitern um PowerPoint-Generierung | 10 Min. |
| [Schritt 3](#schritt-3-design-vorlage-hochladen) | Python-Template für das Corporate Design hochladen | 10 Min. |
| [Schritt 4](#schritt-4-foto-handling-verfeinern) | Foto-Handling mit URL-Fallback ergänzen | 10 Min. |
| Abschluss | Testen, Diskussion, Transfer | 5 Min. |

---

## Vorbereitung

### Projekt in Claude erstellen

1. Öffnen Sie [claude.ai](https://claude.ai)
2. Klicken Sie links in der Sidebar auf **«Projects»**
3. Klicken Sie auf **«Create a project»**
4. Benennen Sie das Projekt, z.B. **«Personen-Dossier»**
5. Sie sehen nun zwei Bereiche:
   - **Custom Instructions** (oben) – hier kommt die Anweisung rein
   - **Files** (unten) – hier laden Sie später Dateien hoch

---

## Schritt 1: Recherche im Chat

> **Ziel:** Claude recherchiert Personen und gibt ein strukturiertes Dossier im Chat aus.

### Was Sie tun

1. Öffnen Sie die Datei [`anweisungen/schritt-1.md`](anweisungen/schritt-1.md)
2. Kopieren Sie den **gesamten Inhalt**
3. Fügen Sie ihn in die **Custom Instructions** Ihres Projekts ein
4. Klicken Sie auf **«Save»**

### Testen

Öffnen Sie einen neuen Chat innerhalb des Projekts und geben Sie ein:

```
Bitte recherchiere:
- [Name einer bekannten Person], [Organisation]
```

> **Tipp für den Workshop:** Nehmen Sie den Namen einer Person, die Sie kennen – z.B. eine bekannte Anwältin oder einen CEO. So können Sie die Qualität der Recherche sofort einschätzen.

### Was Sie sehen sollten

Claude recherchiert per Web-Suche und gibt ein strukturiertes Dossier aus mit:
- Basisprofil (Name, Titel, Organisation)
- Werdegang
- Online-Präsenz & LinkedIn
- Publikationen & Medien
- Engagement & Netzwerk
- Rollenspezifische Infos (Rechtsgebiete bei Juristen, Unternehmensprofil bei Firmenvertretern)
- 3 Gesprächsanknüpfungspunkte
- 1 Einschätzung zum Kommunikationsstil

### Was hier noch fehlt

Die Ausgabe erfolgt nur im Chat – es wird noch keine PowerPoint erstellt. Das kommt in Schritt 2.

---

## Schritt 2: PowerPoint-Ausgabe ergänzen

> **Ziel:** Claude erstellt zusätzlich zum Chat-Dossier eine PowerPoint-Datei.

### Was Sie tun

1. Öffnen Sie die Datei [`anweisungen/schritt-2.md`](anweisungen/schritt-2.md)
2. Kopieren Sie den **gesamten Inhalt**
3. **Ersetzen** Sie die bestehende Anweisung in den Custom Instructions damit
4. Klicken Sie auf **«Save»**

### Testen

Öffnen Sie einen **neuen Chat** im Projekt und geben Sie dieselbe Anfrage ein wie in Schritt 1.

### Was sich geändert hat

Neu enthält die Anweisung einen Abschnitt «Ausgabeformat», der Claude anweist:
1. Zuerst das Dossier im Chat auszugeben
2. Dann eine PowerPoint zu erstellen mit einer Folie pro Person

Claude erstellt die PowerPoint eigenständig mit `python-pptx`. Das Design ist funktional, aber noch nicht an Ihr Corporate Design angepasst. Das kommt in Schritt 3.

---

## Schritt 3: Design-Vorlage hochladen

> **Ziel:** Die PowerPoint wird im EIZ-Corporate-Design generiert – mit Logo, Farben und Layout.

### Was Sie tun

**A) Python-Template hochladen:**

1. Laden Sie die Datei [`templates/eiz_dossier_template_v1.py`](templates/eiz_dossier_template_v1.py) aus diesem Repository herunter
2. Gehen Sie in Ihrem Claude-Projekt zu **Project Knowledge**
3. Klicken Sie auf **«Add content»** → **Datei hochladen**
4. Wählen Sie die Datei `eiz_dossier_template_v1.py`

**B) Logo hochladen:**

1. Laden Sie die Datei [`assets/europa_institut_logo.jpg`](assets/europa_institut_logo.jpg) herunter
2. Laden Sie sie ebenfalls in die **Project Knowledge** hoch

**C) Anweisung aktualisieren:**

1. Öffnen Sie die Datei [`anweisungen/schritt-3.md`](anweisungen/schritt-3.md)
2. Kopieren Sie den **gesamten Inhalt**
3. **Ersetzen** Sie die bestehende Anweisung in den Custom Instructions damit
4. Klicken Sie auf **«Save»**

### Testen

Öffnen Sie einen **neuen Chat** im Projekt und testen Sie erneut.

### Was sich geändert hat

- Die PowerPoint wird jetzt mit dem **EIZ-Design** generiert:
  - Dunkles Petrol-Panel links mit Gradient-Overlay
  - EuropaInstitut-Logo oben rechts
  - Richtige Schriftarten und Farben
  - Professioneller Footer
- Die Anweisung referenziert das hochgeladene Python-Template
- Claude nutzt die Funktion `create_dossier_presentation()` aus dem Template

### Hinweis: Eigenes Corporate Design verwenden

Wenn Sie ein eigenes Design verwenden möchten statt des EIZ-Designs:

1. Laden Sie Ihre eigene PowerPoint-Vorlage in einen **normalen Chat** (nicht ins Projekt)
2. Bitten Sie Claude: *«Analysiere diese PowerPoint-Vorlage und erstelle ein Python-Skript mit python-pptx, das dieses Design exakt reproduziert.»*
3. Laden Sie das generierte Python-Skript in die Project Knowledge hoch
4. Passen Sie die Anweisung entsprechend an

---

## Schritt 4: Foto-Handling verfeinern

> **Ziel:** Fotos werden auf der Folie platziert – mit klickbarem URL-Fallback, wenn der Download nicht möglich ist.

### Was Sie tun

**A) Neues Python-Template hochladen:**

1. Laden Sie die Datei [`templates/eiz_dossier_template_v2.py`](templates/eiz_dossier_template_v2.py) herunter
2. Gehen Sie in die **Project Knowledge** Ihres Projekts
3. **Löschen** Sie die alte Datei `eiz_dossier_template_v1.py`
4. Laden Sie die neue Datei `eiz_dossier_template_v2.py` hoch

**B) Anweisung aktualisieren:**

1. Öffnen Sie die Datei [`anweisungen/schritt-4.md`](anweisungen/schritt-4.md)
2. Kopieren Sie den **gesamten Inhalt**
3. **Ersetzen** Sie die bestehende Anweisung in den Custom Instructions damit
4. Klicken Sie auf **«Save»**

### Was sich geändert hat

Drei Ergänzungen gegenüber Schritt 3:

1. **Neues Feld `foto_url`** im Personen-Dict – speichert die URL des Fotos als Fallback
2. **Drei-Stufen-Logik** für Fotos auf der Folie:
   - **Foto heruntergeladen?** → Wird direkt auf der Folie platziert
   - **Nur URL bekannt?** → Platzhalter mit klickbarem Link zur Foto-URL
   - **Gar kein Foto?** → Platzhalter mit «Kein Foto verfügbar»
3. **Aktualisiertes Python-Template** (`v2`) mit Unterstützung für klickbare URLs

### Testen

Öffnen Sie einen **neuen Chat** und testen Sie mit einer Person, bei der ein Foto auf der Kanzlei-/Unternehmenswebsite zu finden ist.

---

## Abschluss: Testen & Diskussion

### Finaler Test

Geben Sie eine realistische Anfrage mit mehreren Personen ein:

```
Bitte erstelle ein Dossier für unser Meeting am Donnerstag:

- [Name 1], [Rolle], [Organisation]
- [Name 2], [Rolle], [Organisation]
- [Name 3], [Rolle], [Organisation]
```

Prüfen Sie:
- [ ] Werden alle Personen korrekt recherchiert?
- [ ] Werden Juristen und Unternehmensvertreter unterschiedlich aufbereitet?
- [ ] Wird die PowerPoint im richtigen Design generiert?
- [ ] Sind Fotos (oder Platzhalter) auf den Folien?
- [ ] Stimmen die Gesprächsanknüpfungspunkte?

### Diskussionsfragen

- Wo hat Claude überraschend gute Ergebnisse geliefert?
- Wo waren die Grenzen? Was hat gefehlt?
- Für welches eigene Projekt würden Sie das morgen einsetzen?
- Welche anderen Anwendungen fallen Ihnen ein? (z.B. Unternehmens-Dossiers, Konferenz-Vorbereitung, Pitch-Recherche)

---

## Dateien in diesem Repository

```
workshop-personen-dossier/
├── README.md                              ← Diese Datei
├── anweisungen/
│   ├── schritt-1.md                       ← Anweisung für Schritt 1 (nur Chat)
│   ├── schritt-2.md                       ← Anweisung für Schritt 2 (+ PowerPoint)
│   ├── schritt-3.md                       ← Anweisung für Schritt 3 (+ Design-Template)
│   └── schritt-4.md                       ← Anweisung für Schritt 4 (+ Foto-URL-Fallback)
├── templates/
│   ├── eiz_dossier_template_v1.py         ← Python-Template Schritt 3
│   └── eiz_dossier_template_v2.py         ← Python-Template Schritt 4 (mit foto_url)
└── assets/
    └── europa_institut_logo.jpg           ← EIZ-Logo für die PowerPoint
```

---

## Tipps & Hinweise

### Häufige Fragen

**«Claude findet nichts zu meiner Person.»**  
→ Manche Personen haben wenig Online-Präsenz. Prüfen Sie, ob Name und Organisation korrekt geschrieben sind. Bei häufigen Namen hilft eine genauere Angabe (z.B. Fachgebiet, Standort).

**«Die PowerPoint sieht nicht genau aus wie unsere Vorlage.»**  
→ Das Python-Template bildet das Design so nah wie möglich ab. Feinjustierungen (z.B. exakte Schriftgrössen, Abstände) können Sie im Template-Code anpassen.

**«Kann ich das auch für andere Zwecke nutzen?»**  
→ Ja! Das gleiche Prinzip funktioniert für Unternehmens-Dossiers, Konferenz-Vorbereitungen, Pitch-Recherchen, Mandats-Akquise etc. Passen Sie einfach die Anweisung an.

**«Kann ich mein eigenes Logo und Design verwenden?»**  
→ Ja. Laden Sie Ihre eigene PowerPoint-Vorlage in einen separaten Chat, lassen Sie Claude den Code generieren, und tauschen Sie das Template in der Project Knowledge aus. Siehe [Schritt 3 → Eigenes Corporate Design verwenden](#hinweis-eigenes-corporate-design-verwenden).

### Einschränkungen

- Claude kann nicht auf Inhalte hinter Login-Walls zugreifen (z.B. LinkedIn-Profile sind nur teilweise einsehbar)
- Die Foto-Suche findet nur Bilder auf öffentlich zugänglichen Websites
- Bei sehr vielen Personen (>8) kann die Recherche einige Minuten dauern
- Die PowerPoint-Generierung erfordert ein Claude-Abo mit Code-Ausführung (Pro oder Team)

---

## Lizenz

Dieses Workshop-Material steht unter der [MIT License](LICENSE). Die EIZ-Design-Elemente (Logo, Farben) sind Eigentum des EuropaInstituts an der Universität Zürich und dürfen nur im Rahmen autorisierter EIZ-Veranstaltungen verwendet werden.
