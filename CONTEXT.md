# Planet Group — Styleguide, Organigramm & Präsentation

## Übersicht

Dieses Repo enthält das Planet Design System sowie eine interaktive Organigramm-Anwendung für die Planet Group.

**Live-Repo:** https://github.com/Planet-Group/Planet  
**Lokaler Dev-Server:** `npx serve -p 3457 .` (oder über `.claude/launch.json`)

---

## Dateien

| Datei | Beschreibung |
|---|---|
| `UX-Styleguide.html` | Planet Design System Styleguide (Komponenten, Tokens, Typografie) |
| `Presentation_Styleguide.html` | **Präsentations-Template** — alle Folientypen + Raster-Referenz |
| `Report_Styleguide.html` | **Bericht-Template** — A4-Print/PDF-Referenz, alle Seiten- und Komponententypen |
| `Tagung_Styleguide.html` | **Tagungs-Layout** (Test) — editoriales 12-Spalten-Raster, A4-Print, 9 Beispielseiten |
| `orgchart.html` | **Organigramm** — interaktives Radial-Chart |
| `orgdata.js` | Org-Daten (generiert aus Personio-Export) — `var ORG_DATA = {...}` |
| `planet.css` | Planet Design System — Tokens, Typo, Layout, Komponenten |
| `temp.css` | App-spezifische Styles (Org-Chart) |
| `CONTEXT.md` | Diese Datei |
| `Pages/` | Signatur.html, Bildzuschnitt.html, index.html |

---

## Organigramm (`orgchart.html`)

### Features
- **Radiales D3.js-Layout** (v7) mit Expand/Collapse, Accordion-Verhalten
- **Dark Mode** mit `localStorage`-Persistenz und System-Präferenz-Erkennung
- **Mobile Drill-Down** — separater View für `≤768px`
- **Zoom-to-Fit** beim Aufklappen, Fenstergröße-Änderung und Fullscreen
- **Aktiver Strang** — inaktive Nodes und Links werden ausgeblendet
- **Suche** mit Auto-Zoom auf Treffer

### Bedienung
- **Kreis klicken** → aufklappen / einklappen
- **Name klicken** → Info-Panel öffnen
- **P klicken** → alles einklappen (Reset)
- **`fit_screen`-Button** → auf Bildschirm einpassen
- **Fullscreen-Button** → Vollbild

### Node-Typen & Farben (Light Mode)
| Typ | Farbe | Beschreibung |
|---|---|---|
| `holding` | `#0000FF` (Blau) | Planet GmbH |
| `company` | `#000000` (Schwarz) | Tochtergesellschaften |
| `area` | `#3C3C3C` (Dunkelgrau) | Bereiche |
| `department` | `#888888` (Grau) | Abteilungen |
| `team` | `#C8C8C8` (Hellgrau) | Teams |
| `employee` | `#EFEFEF` (Sehr hell) | Mitarbeitende |

**Sonderfall:** Operations (Inuvet DE) → Planet-Gelb `#D4FF00`

---

## Org-Daten (`orgdata.js`)

### Quelle
Personio-Export `Personio_inuvet-gmbh_employees_*.csv`  
→ Datei ist via `.gitignore` vom Repo ausgeschlossen.

### Aktualisieren
1. Neuen Personio-Export in `/Users/michaelhoppe/code/Planet-Styleguide/` ablegen
2. Claude mit dieser CONTEXT.md als Kontext starten
3. „Bitte `orgdata.js` aus dem neuen Personio-Export regenerieren"

### Struktur
```
Planet GmbH (holding)
└── Inuvet (company)
    ├── Inuvet DE (company) ← Inuvet GmbH
    ├── Inuvet AT           ← Inuvet GmbH (Österreich)
    ├── Inuvet CH           ← Inuvet AG
    ├── Inuvet FR/LUX       ← Inuvet SARL
    ├── Inuvet IT           ← Planet Group IT S.r.l
    ├── Inuvet ES           ← PLNT Group Ibérica S.L.
    ├── Inuvet BE           ← PLNT Group BE B.V.
    ├── Inuvet JP           ← Planet Group Japan G.K.
    └── Inuvet TW           ← Inuvet Taiwan
├── EQX                     ← EQX AG
├── Byox                    ← Byox Healthcare GmbH
├── Planimol                ← Planimol GmbH
└── PLNT Group GmbH         ← PLNT Group GmbH
```

### Felder pro Node
```json
{
  "id": "eindeutige-kebab-id",
  "name": "Anzeigename",
  "short": "KRZ",
  "type": "holding | company | area | department | team | employee",
  "role": "Stellenbezeichnung (nur employees)",
  "description": "Freitext",
  "color": "#HEX (optional — Sonderfarbe)",
  "textColor": "#HEX (optional)"
}
```

---

## Design System (`planet.css`)

### Tokens
- **Primär:** `#0000FF` (Blau)
- **Sekundär:** `#D4FF00` (Gelb)
- **Schrift:** Neue Haas Grotesk Display (Adobe Fonts, Kit `phj5hyp`), weights 500/600
- **Spacing:** 8px-Grid (`--space-1` bis `--space-16`)
- **Keine Magic Numbers** — alle Werte aus Token-System

### Regeln
- Kein `italic`
- Container Queries: `cqw` (nicht `cqi`)
- Keine Wildcards (`* { ... }` vermeiden)

---

## Technischer Stack
- **D3.js v7** (CDN) — Radial-Tree-Layout
- **Material Icons Outlined** (Google CDN)
- **Adobe Fonts** — Neue Haas Grotesk Display
- **Kein Build-Tool** — alles plain HTML/CSS/JS, läuft direkt im Browser
- **Kein Backend** — statische Dateien, `file://` und HTTP-Server beide unterstützt

---

---

## Präsentation (`Presentation_Styleguide.html`)

### Skill
Neue Präsentationen werden mit dem Skill **`planet-presentation`** erstellt:
> „Erstelle eine Präsentation über [Thema]"

Der Skill generiert eine eigenständige HTML-Datei unter `Pages/presentations/{slug}.html`.

### Raster-Grundregeln

```
Folie:         1920 × 1080 px (16:9), alle Maße in cqw
Padding:       2.5cqw allseitig (= Satzspiegel)
Spaltenbreite: 30cqw (je Spalte), 3 Spalten
Gutter:        2.5cqw (zwischen Spalten)
slide-top:     position: absolute; top: 2.5cqw  → Inhalt oben verankert
slide-bottom:  position: absolute; bottom: 2.5cqw → Inhalt unten verankert
```

**Ausnahme:** Nur `slide--fullbleed` (Vollbild-Foto) darf Ränder ignorieren.

### Sichtbarkeitsregeln
| Situation | Klasse |
|---|---|
| Spalte 1 in `slide-bottom` belegt | `slide--no-num` |
| Spalte 1 in `slide-top` belegt | `slide--no-logo` |
| Beide belegt | `slide--no-logo slide--no-num` |

### Folientypen
| Nr | Typ | Klassen | Besonderheit |
|---|---|---|---|
| 01 | Cover Primary | `slide--primary slide--no-num` | Nur h1, max 8 Wörter |
| 02 | Headline + Body | (weiß) | h1 + p, Spalten 2–3 |
| 03 | H2 + Body | (weiß) | h2 + p, Spalten 2–3 |
| 04 | 5 Body-Blöcke | `slide--acid slide--no-num` | 2 oben + 3 unten |
| 05 | Text + Bilder | `slide--primary` | p + Bilder in Spalten 2–3 |
| 05a | Bild oben · Text unten | `slide--primary slide--no-num` | Bild in slide-top |
| 05b | Bild-Spalte links | `slide--primary slide--no-logo slide--no-num` | `slide-image--col-left` |
| 05c | Text oben · Bild unten | `slide--primary slide--no-num` | Bild in slide-bottom |
| 06 | Bild rechts + Caption | `slide--primary slide--no-num` | `slide-image--fill` (Spalten 2–3) |
| 06b | Rundbild 2 Spalten | `slide--primary slide--no-num` | Kreis Ø 51.25cqw, rotierend |
| 07 | Stat Monumental | `slide--primary` | 1 Kennzahl, `slide-stat-number` |
| 08 | Triptychon | `slide--no-num` | 3 Portrait-Bilder, kein Text |
| 09 | Vollbild-Foto | `slide--fullbleed slide--no-num` | Einziger Typ ohne Rasterrand |
| 10 | Vollbild + Caption | `slide--fullbleed slide--no-num` | Caption Spalte 1–2 |
| Acid Cover | `slide--acid slide--no-num` | Gelber Cover |

### Inhalts-Limits
| Element | Regel |
|---|---|
| `h1` | Max. 8 Wörter |
| `h2` | Max. 12 Wörter |
| `p` | Max. 30 Wörter pro Block |
| Stat | 1 Wert mit Einheit (z.B. `+38 %`) |
| Caption | Max. 20 Wörter |

### Bild-Regeln
- `width: 100%` der Spalte — **nie** explizite `width` in `cqw` setzen
- Nur `height` explizit (in `cqw`)
- Runde Bilder: `slide-image--circle` → rotiert automatisch (`planetRotate 28s`)
- Bilder füllen max. verfügbaren Platz — Min-Gap zu Text: `2.5cqw`
- **Nur `slide--fullbleed` darf Rasterränder ignorieren**

### Animations-Regeln
- Einblendung (nur Präsentationsmodus): Logo 0ms → slide-top 120ms → slide-bottom 240ms → Nummer 360ms
- Easing: `cubic-bezier(0.0, 0.0, 0.2, 1)`

---

## Bericht (`Report_Styleguide.html`)

### Skill
Neue Berichte werden mit dem Skill **`planet-report`** erstellt:
> „Erstelle einen Bericht über [Thema]"

Der Skill generiert eine eigenständige HTML-Datei (Vorschlag: `Pages/reports/{slug}.html`), die im Browser zur Ansicht stapelt und über **Drucken → Als PDF sichern** sauber auf DIN A4 ausgibt — ein Blatt pro `.page`.

### Seiten-Grundregeln

```
Blatt:        210 × 297 mm (DIN A4), alle Maße in mm/pt (nie cqw/vw)
Satzspiegel:  oben 26mm · seitlich 22mm · unten 22mm
1 .page       = 1 gedrucktes A4-Blatt — kein Überlauf, sonst neue .page
Kopf/Fuß:     laufende .page-header / .page-footer (außer Cover)
Cover:        .page--cover (blau, randlos, einzige farbige Vollfläche)
```

### Seitentypen
Inhaltsseite (weiß) · `.page--cover` (blau) · `.page--divider` (Kapitel-Trenner, blau) · `.page--primary` (blaue Inhaltsseite, Kopf/Fuß automatisch weiß) · `.page--image` (Vollbild-Foto, randlos) · `.page--back` (Rückseite/Kontakt, blau).

### Komponenten
`.section-head` (+ `.sh-num`) · `.stat-row`/`.stat` · `.stat-hero` (monumentale Kennzahl) · `.table` · `.dl` · `.callout` (`--primary`/`--acid`) · `.quote` · `.figure` · `.cols-2` · `.text-cols` (zweispaltiger Fließtext) · `.barchart` · `.toc` · `.flow` (vertikaler Rhythmus).

### 🔒 Farbregel (gilt auch für den Präsentations-Skill)
Auf blauem Grund (Cover, Divider, Back, `.page--primary`, `.callout--primary`, `slide--primary`) ist Schrift **immer weiß** — nie Gelb, nie Schwarz. Gelb/Schwarz nur als Fläche (z. B. `--acid`), nie als Schrift auf Blau.

### Type-Skala (fix, pt)
Cover-Titel 52 · h2 21 · h3 14 · h4 11 · lead 13 · body 10.5 · stat 40 · quote 18 · meta 8.
Akzentfarbe im Inhalt: Blau `--planet-primary`. Kein Italic, keine Inline-`font-size`.

### Print-Regeln
`@page { size: A4; margin: 0 }`; Figuren/Tabellenzeilen/Callouts/Quotes `break-inside: avoid`; Überschriften `break-after: avoid`; Seitenzahlen per JS automatisch nach Blatt-Reihenfolge.

---

## Tagungs-Layout (`Tagung_Styleguide.html`) — Test/Alternativ

### Skill
Alternativer Skill **`planet-tagung`** (`skills/planet-tagung.skill`) — editoriales Layout, abgeleitet aus einer InDesign-Vorlage. Für Standard-Geschäftsberichte bleibt `planet-report` der Favorit.

### Raster (gesperrt, aus PDF-Hilfslinien abgeleitet)
```
A4 · 12 Spalten × 10 mm · Gutter 5 mm (Spaltenfeld 175 mm)
Ränder: links 20 · rechts 15 · oben 20 · unten ≥15 mm
Linke Meta-Spalte = Spalten 1–2 (Logo oben, Seitenzahl/Meta unten, schwarz)
Leerzone = Spalten 3–4 (prägendes Weiß — bleibt leer)
Content = Spalten 5–12 (versetzt, bewusst nicht voll breit)
```

### Seiten-/Bausteintypen
Cover (blau) · Artikel (H1/Lead/H2/H3) · Programm/Agenda · Bildseite · Statement (blau) · Kennzahlen (`.stats`) · Balkendiagramm (`.barchart`) · monumentale Zahl (`.stat-mono`, blau) · Display-Headline (`h1.display`, 54 pt) · Typo-Specimen. Logo = H2-Größe. Farbregel „weiß auf Blau" gilt auch hier.

---

## Bekannte Punkte / Offene Aufgaben
- Franca Caspari (Inuvet DE Marketing) arbeitet funktional für EQX — evtl. verschieben
- Evelin Bauer steht unter Inuvet AT (laut Personio), ist aber HR für mehrere Einheiten
- `description`-Felder in `orgdata.js` sind noch leer („Inhalte folgen.")
- GitHub Repo ggf. auf **Private** stellen (orgdata.js enthält echte Mitarbeiternamen)
