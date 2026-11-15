# Lennart Mahling – Personal Website

Meine persönliche Website und digitale Präsenz für Softwareentwicklung, Webdesign und 3D-Visualisierung. Entwickelt mit [Astro](https://astro.build/) und einem individuellen Design.

Die Website verbindet meine Projekte, Leistungen und meinen technischen Werdegang an einem Ort. Sie dient sowohl als Anlaufstelle für potenzielle Auftraggeber als auch als persönliches Portfolio meiner bisherigen Arbeit.

**Live:** https://dev.lennart-mahling.de  
**Repository:** https://github.com/LennartMahling/lennart-mahling-website

---

## Überblick

Die Website ist von Grund auf mit Astro aufgebaut. Im Mittelpunkt stehen eine klare Gestaltung, eigenständige visuelle Elemente und eine übersichtliche Präsentation meiner Arbeit.

### Inhalte

- **Startseite:** Vorstellung, ausgewählte Arbeiten und Leistungen.
- **Über mich:** Persönlicher und fachlicher Hintergrund.
- **Projekte:** Ausgewählte Arbeiten aus Softwareentwicklung, Web und 3D.
- **Leistungen:** Softwareentwicklung, Webdesign und 3D-Visualisierung.
- **Portfolio:** Projektübersicht, technische Interessen, Qualifikationen und bisheriger Werdegang.
- **Impressum & Datenschutz:** Rechtliche Informationen.

### Schwerpunkte

| Bereich | Beschreibung |
|---|---|
| Softwareentwicklung | Individuelle Softwarelösungen und praxisnahe Anwendungen |
| Webentwicklung | Konzeption, Gestaltung und technische Umsetzung von Websites |
| 3D-Visualisierung | 3D-Modelle, Produktvisualisierungen und Echtzeit-Graphics |

---

## Technologie-Stack

| Technologie | Einsatz |
|---|---|
| [Astro](https://astro.build/) | Webframework und statische Seitengenerierung |
| HTML | Semantische Struktur der Website |
| CSS | Individuelles Design, Layouts und Animationen |
| JavaScript | Interaktive Elemente |
| npm | Paketverwaltung und Build-Prozesse |
| Git & GitHub | Versionsverwaltung und Quellcode |

Das Projekt verwendet Astro ohne zusätzliches UI-Framework. Die Gestaltung basiert auf eigenständig entwickelten Komponenten und CSS.

---

## Projektstruktur

Die wichtigsten Verzeichnisse und Dateien:

```text
lennart-mahling-website/
│
├── src/
│   ├── assets/             # Bilder und weitere importierte Assets
│   ├── components/         # Wiederverwendbare Komponenten
│   ├── layouts/            # Seitenlayouts
│   └── pages/              # Seiten und Routing
│
├── .vscode/                # Editor-Konfiguration
├── .idea/                  # IDE-Konfiguration
│
├── astro.config.mjs        # Astro-Konfiguration
├── package.json            # Abhängigkeiten und Scripts
├── package-lock.json       # Fixierte Dependency-Versionen
├── tsconfig.json           # TypeScript-Konfiguration
└── README.md
```

Astro erzeugt die Seiten automatisch anhand der Dateien im Verzeichnis `src/pages/`. Die Inhalte werden beim Build in statische HTML-Dateien umgewandelt.

---

## Voraussetzungen

Für die lokale Entwicklung werden benötigt:

- [Node.js](https://nodejs.org/) **Version 22.12.0 oder höher**
- npm (wird mit Node.js installiert)
- Git

Die benötigte Node.js-Version ist in der `package.json` hinterlegt.

---

## Installation & Entwicklung

### 1. Repository klonen

```bash
git clone https://github.com/LennartMahling/lennart-mahling-website.git
```

Anschließend in das Projektverzeichnis wechseln:

```bash
cd lennart-mahling-website
```

### 2. Abhängigkeiten installieren

```bash
npm install
```

Alternativ kann bei vorhandener `package-lock.json` eine reproduzierbare Installation mit folgendem Befehl durchgeführt werden:

```bash
npm ci
```

### 3. Entwicklungsserver starten

```bash
npm run dev
```

Die Website ist anschließend standardmäßig unter folgender Adresse erreichbar:

```text
http://localhost:4321
```

Änderungen an den Quelldateien werden während der Entwicklung automatisch übernommen.

---

## Verfügbare Befehle

Alle Befehle werden im Hauptverzeichnis des Projekts ausgeführt.

| Befehl | Funktion |
|---|---|
| `npm install` | Installiert die Projektabhängigkeiten |
| `npm ci` | Installiert Abhängigkeiten anhand der Lock-Datei |
| `npm run dev` | Startet den lokalen Entwicklungsserver |
| `npm run build` | Erstellt den Produktionsbuild |
| `npm run preview` | Zeigt den fertigen Build lokal an |
| `npm run astro` | Führt Astro-CLI-Befehle aus |

### Produktionsbuild

```bash
npm run build
```

Astro erstellt dabei automatisch das Verzeichnis `dist/`.

Dieses enthält die fertige statische Website:

```text
dist/
├── _astro/
├── intro/
├── portfolio/
├── projects/
├── services/
├── index.html
└── ...
```

Der Inhalt dieses Verzeichnisses kann auf einem statischen Webserver bereitgestellt werden.

Vor einer Veröffentlichung kann der Build lokal geprüft werden:

```bash
npm run preview
```

---

## Deployment

Die Website wird als statische Astro-Seite auf einem Debian-Server mit Apache bereitgestellt.

**Deployment-Ziel:**

```text
dev.lennart-mahling.de
```

Der Server benötigt dafür keinen dauerhaft laufenden Node.js-Prozess. Apache liefert die fertig generierten Dateien aus.

### Deployment-Ablauf

Der Quellcode wird für das Deployment temporär aus GitHub geklont. Anschließend werden die Abhängigkeiten installiert und die Website gebaut.

```bash
cd /tmp

git clone https://github.com/LennartMahling/lennart-mahling-website.git dev-website

cd /tmp/dev-website

npm ci

npm run build
```

Nach einem erfolgreichen Build wird der Inhalt von `dist/` in das Webverzeichnis kopiert:

```bash
rm -rf /var/www/dev.lennart-mahling.de/html/*

cp -a dist/. /var/www/dev.lennart-mahling.de/html/
```

Anschließend kann der temporäre Clone entfernt werden:

```bash
rm -rf /tmp/dev-website
```

**Wichtig:** Das bisherige Webverzeichnis sollte erst ersetzt werden, wenn `npm run build` erfolgreich abgeschlossen wurde. Der Git-Clone und die Build-Dateien bleiben außerhalb des eigentlichen Webroots.

---

## Projektstatus

Die Website wird kontinuierlich weiterentwickelt. Neue Projekte, Inhalte und gestalterische Anpassungen werden nach und nach ergänzt.

Der Schwerpunkt liegt darauf, technische Fähigkeiten praktisch einzusetzen, neue Technologien kennenzulernen und aus eigenen Ideen funktionierende Projekte zu entwickeln.

---

## Kontakt

**Lennart Mahling**  
Softwareentwicklung · Web · 3D

- Website: https://dev.lennart-mahling.de
- GitHub: https://github.com/LennartMahling
- LinkedIn: https://www.linkedin.com/in/lennart-mahling-677100301/
- E-Mail: info@lennart-mahling.de

---

## Lizenz

Für dieses Repository ist derzeit keine separate Open-Source-Lizenz hinterlegt. Eine Nutzung, Weiterverbreitung oder Veränderung des Quellcodes ist daher nicht automatisch freigegeben. Bei Interesse an einer Verwendung bitte vorher Kontakt aufnehmen.
