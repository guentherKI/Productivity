# 📘 DevFlow Suite – README 

> **Ziel:** Eine Desktop-Applikation für Frontend- und Fullstack-Developer, die mehrere Zeit-sparende Tools in einem Programm vereint.  
> Die App dient als „Developer Efficiency HQ“ mit Deploy-Tools, API-Tester, Performance-Board, File-Tools und mehr.

---

# 1. Projektbeschreibung

**DevFlow Suite** ist ein modular aufgebautes Developer-Toolset in einer einzigen Electron-App.

Inhalte der App:

- **LiveDeploy Template Manager**  
  Templates verwalten, deployen, clonen, bearbeiten.
- **API Tester (Postman-Alternative)**  
  Tabs, Environments, Token-Manager, History.
- **Performance & Tracking Board**  
  Logs, Speed-Monitoring, Live-Tracking.
- **Developer Utilities**  
  JSON/Regex Tools, Snippet Vault, File Tools, Inspector.
- **Plugin-System**  
  Erweiterbar durch neue Module.

Ziele des Projekts:

- maximale Übersichtlichkeit  
- klare Modularisierung  
- UI & Backend strikt getrennt  
- schnelle Erweiterbarkeit  
- modernes DX (Developer Experience)

---

# 2. Technologien & Anforderungen

## 2.1 Stack
- **Electron 32+**
- **Vite + React**
- **TypeScript**
- **TailwindCSS**
- **Node.js (Electron Main Process)**
- **Optional Persistenz:** LowDB / JSON / SQLite

## 2.2 Build-System
- `electron-builder` – Builds/Installer  
- `vite` – UI Build  
- `tsc` – Type Checking

## 2.3 Optional CI
- GitHub Actions für Auto-Builds & Releases

---

# 3. Projektstruktur

```plaintext
devflow-suite/
│
├── app/                         # UI (Renderer)
│   ├── src/
│   │   ├── components/          # Globale UI-Komponenten
│   │   ├── pages/               # Jede Tool-Seite der App
│   │   ├── modules/             # Frontend-Module aller Tools
│   │   │   ├── api-tester/
│   │   │   │   ├── ui/
│   │   │   │   ├── logic/
│   │   │   │   └── types/
│   │   │   ├── livedeploy/
│   │   │   ├── performance/
│   │   │   ├── utilities/
│   │   │   └── shared/
│   │   ├── store/               # Globaler Zustand
│   │   ├── hooks/               # Globale Hooks
│   │   ├── styles/              # Styles + Tailwind
│   │   ├── App.tsx
│   │   └── main.tsx
│   └── index.html
│
├── main/                        # Electron Main Process
│   ├── ipc/                     # IPC Handler (Renderer <-> Main)
│   ├── tools/                   # Node-Tools (FS, HTTP, Deploy)
│   ├── core/                    # Config, DB, Logging, Settings
│   ├── windows/                 # Window Controller
│   ├── preload/                 # Preload Scripts
│   └── main.ts                  # Electron Entry Point
│
├── modules/                     # Reine Logik-Pakete (NPM-kompatibel)
│   ├── api-tester/
│   ├── livedeploy/
│   ├── performance/
│   └── utilities/
│
├── assets/                      # Icons, Logos, Themes
├── docs/                        # Dokumentation
├── dist/                        # Build Output
├── scripts/                     # Build- & Deployment Skripte
│
├── package.json
├── vite.config.js
├── electron-builder.config.js
└── README.md
