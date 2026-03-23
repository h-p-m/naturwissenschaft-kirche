# Dokumentation: Webprojekt Stiftung Naturwissenschaft und Kirche

**Erstellt:** 17. März 2026
**Projektverzeichnis:** `C:\Users\micro\claude_workspaces\NWK\`
**Live-URL:** https://h-p-m.github.io/naturwissenschaft-kirche/
**GitHub-Repository:** https://github.com/h-p-m/naturwissenschaft-kirche

---

## 1. Analyse der Originalwebsite

**Quelle:** naturwissenschaft-kirche.de (leitet weiter auf https://wp.nw-k.de/)
**Ergebnis:** `mat/analyse-naturwissenschaft-kirche.md`

Die Originalseite ist ein schlichter WordPress-Auftritt (Theme: GeneratePress) der
*Stiftung Naturwissenschaft und Kirche*, Essen. Sie umfasst 5 Unterseiten:
Stiftung, Stifter, Aktivitäten, Kuratorium, Kontakt.

---

## 2. Spiegelung der Originalseite

Die Originalseite wurde zur Referenz lokal gespeichert:

**Verzeichnis:** `htdocs_old/`

```
htdocs_old/
├── index.html
├── stifter.html
├── aktivitaten.html
├── kuratorium.html
├── kontakt.html
└── assets/
    ├── css/
    │   ├── generatepress.min.css
    │   └── block-library.min.css
    ├── js/
    │   ├── classList.min.js
    │   └── menu.min.js
    └── img/
        ├── cropped-Logo_Web.png   (3528×1179 px, Headerlogo)
        └── Logo_NWK-2.png         (100×100 px)
```

**Werkzeug:** `curl` (wget nicht verfügbar in der Umgebung)

Aus der Analyse der heruntergeladenen Dateien wurden ermittelt:
- **Grünton der Originalseite:** `#29b716`
- **Logo-Datei:** `cropped-Logo_Web.png`

---

## 3. Erstellung der statischen Bootstrap-Seiten

**Verzeichnis:** `htdocs/`
**Framework:** Bootstrap 5.3.3 (via jsDelivr CDN)
**Font:** Libertinus Serif + Libertinus Sans (via Bunny Fonts CDN)

### 3.1 Dateistruktur

```
htdocs/
├── index.html           Startseite
├── stifter.html         Biographie Ludolf Schiffer
├── aktivitaeten.html    Wettbewerbe und Dokumente
├── kuratorium.html      Kuratoriumsmitglieder
├── kontakt.html         Kontakt und Impressum
├── assets/
│   └── img/
│       ├── cropped-Logo_Web.png
│       └── Logo_NWK-2.png
└── css/
    └── style.css
```

### 3.2 Design-Entscheidungen

| Element | Lösung |
|---|---|
| Primärfarbe | `#29b716` (Grün, aus Original übernommen) |
| Sekundärfarbe | `#636363` (Grau, aus Original übernommen) |
| Fließtext | Libertinus Serif (400, 400i, 700) |
| Überschriften, Footer, Nav | Libertinus Sans (400, 700) |
| Font-Bezug | `@import` via `fonts.bunny.net` (DSGVO-konform) |
| Navbar | Weißer Hintergrund, grüne Unterlinie, Logo 90px hoch |
| Kontakt | Einfacher `mailto:`-Link (kein Serverformular nötig) |
| Seitenbalken | CSS `::before` Pseudo-Element, 80% Höhe, vertikal zentriert |

### 3.3 CSS-Variablen (`style.css`)

```css
:root {
  --nwk-green:   #29b716;   /* Primärfarbe */
  --nwk-green-dk:#1f8e10;   /* Hover-Dunkel */
  --nwk-gray:    #636363;   /* Grau (Footer, Labels) */
  --nwk-light:   #f7f8f9;   /* Heller Hintergrund */
  --nwk-text:    #222222;   /* Fließtext */
  --font-serif:  'Libertinus Serif', Georgia, serif;
  --font-sans:   'Libertinus Sans', Arial, sans-serif;
}
```

---

## 4. Iterative Anpassungen

Die folgenden Änderungen wurden schrittweise auf Basis von Feedback vorgenommen:

| # | Änderung | Betroffene Datei(en) |
|---|---|---|
| 1 | Graue Top-Bar entfernt | alle HTML |
| 2 | Aktiv-Unterstrich im Menü entfernt | style.css |
| 3 | Libertinus-Font via Bunny Fonts CDN eingebunden | style.css |
| 4 | Grünton `#29b716` aus Original übernommen | style.css |
| 5 | Logo `cropped-Logo_Web.png` in Navbar eingebunden | alle HTML |
| 6 | Steckbrief-Tabelle: Beschriftungen dunkler und fett | style.css |
| 7 | Hero-Logo auf Startseite hinzugefügt (später wieder entfernt) | index.html |
| 8 | Navbar-Logo von 60px auf 90px vergrößert | style.css |
| 9 | Hintergrund `.page-header` entfernt | style.css |
| 10 | Hintergrund `blockquote.nwk-quote` entfernt | style.css |
| 11 | Libertinus Sans für alle h1–h6 gesetzt | style.css |
| 12 | Preisträger Essaywettbewerb 2023 mit PDF-Links ergänzt | aktivitaeten.html |
| 13 | Seitenbalken auf 80% Höhe via `::before` Pseudo-Element | style.css |
| 14 | `blockquote-footer` transparenter Hintergrund ergänzt | style.css |
| 15 | Grünen Balken neben Zitat oben und unten verkürzt (padding, margin-bottom) | style.css |

---

## 5. Inhalt der Seiten

### index.html – Stiftung
- Hero-Bereich mit Titel und Untertitel
- Textabschnitt „Unser Anliegen" mit Zitat des Stifters
- Download-Link zur Satzung (PDF)
- Drei Übersichts-Cards: Stifter, Aktivitäten, Kuratorium

### stifter.html – Der Stifter
- Biographie Ludolf Schiffer (1930–2016)
- Abschnitte: Geistliche Laufbahn, Publikation, Stiftungsgründung
- Steckbrief-Seitenleiste (Geburtsort, Studium, Priesterweihe, Stellen, Publikation, Tod)

### aktivitaeten.html – Aktivitäten
- Videowettbewerb 2025 (aktuell): KI und Glaube, Frist 1. Oktober 2025
- Essaywettbewerb 2023 (abgeschlossen):
  - Preisträger mit verlinkten Essay-PDFs (Renz, Nemet, Kalvelage, Krebser)
  - Sonderpreis Bischöfliche Canisiusschule Ahaus
  - Festvortrag Prof. Blome, Flyer, Anschreiben als PDF

### kuratorium.html – Kuratorium
- Tabelle: 5 ordentliche Mitglieder
- Tabelle: 2 assoziierte Mitglieder

### kontakt.html – Kontakt & Impressum
- mailto-Link: stiftung@naturwissenschaft-kirche.de
- Postanschrift (c/o Bärbel Volmer, Wedemark)
- Impressumstext

---

## 6. Deployment auf GitHub Pages

### Voraussetzungen (bereits vorhanden)
- Git 2.53 installiert
- GitHub CLI (`gh`) 2.86 installiert und eingeloggt als `h-p-m`

### Durchgeführte Schritte

```bash
# 1. Git-Repository initialisieren
cd htdocs/
git init
git add .
git commit -m "Initiales Commit: Stiftung Naturwissenschaft und Kirche"

# 2. GitHub-Repository erstellen und pushen
gh repo create naturwissenschaft-kirche --public \
  --description "Stiftung Naturwissenschaft und Kirche – statische Website" \
  --source . --remote origin --push

# 3. GitHub Pages aktivieren (API)
gh api repos/h-p-m/naturwissenschaft-kirche/pages \
  --method POST \
  -f "source[branch]=master" \
  -f "source[path]=/"
```

### Zukünftige Updates deployen

```bash
cd C:\Users\micro\claude_workspaces\NWK\htdocs
git add .
git commit -m "Beschreibung der Änderung"
git push
```

GitHub Pages aktualisiert sich automatisch ca. 1 Minute nach dem Push.

---

## 7. Hinweise und offene Punkte

- **Font-Fallback:** Sollte Bunny Fonts nicht erreichbar sein, greift der Browser auf Georgia (Serif) bzw. Arial (Sans) zurück.
- **PDF-Links** auf `aktivitaeten.html` verweisen noch auf `wp.nw-k.de` – bei einem vollständigen Umzug müssten die PDFs ebenfalls ins Repository kopiert werden.
- **Satzungs-PDF** verweist ebenfalls noch auf `wp.nw-k.de`.
- **Custom Domain:** Die Seite ist derzeit unter `h-p-m.github.io/naturwissenschaft-kirche/` erreichbar. Eine eigene Domain (`naturwissenschaft-kirche.de`) kann in den GitHub-Repository-Einstellungen unter *Pages → Custom domain* eingetragen werden.
