# Base44 Dev Environment

## Project Overview
This is a **static single-file web app** — a "Robot Editor" built with the PenguinMod Packager (a Scratch-like project packager). The entire app is contained in `index.html` (~9MB), which embeds all JavaScript, assets, and project data inline. There is no backend, no build step, no package manager, and no external dependencies.

## Running the App
```
docker compose -f docker-compose.base44.yml up -d
```
- Serves `index.html` via nginx:alpine on host port **3000**.
- The file is bind-mounted read-only, so edits to `index.html` are reflected on browser reload (no live-reload dev server — call `reload_preview` after edits).
- Healthcheck: `GET /` via wget.

## Verification
- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return `200`.
- The page shows a loading screen, then a green-flag launch button to start the project.

## Secrets
None required. The app is fully self-contained with no external service calls at boot.
