# Expense tracker Max

Offline-first expense, checklist and diary tracker for life in Taiwan. Single-page vanilla JS app, no build step.

## Run
- Local: `python3 -m http.server 8000` in this folder, open http://localhost:8000 (service worker needs localhost or https).
- Host: push `index.html` and `sw.js` together to GitHub Pages or Vercel.

## Files
- `index.html`: all HTML, CSS and JS (sections marked with `// ----------` comments).
- `sw.js`: network-first cache so the app loads offline.

## Architecture
- Storage: IndexedDB `twlife` with stores `tx`, `log`, `notes`, `meta` (settings in `meta` key `cfg`).
- Each expense stores `a` (TWD), `r` (INR per TWD on that day), `d` (date), `c`/`s` (category/sub), `n` (note), `src` (manual or ai).
- Rates: open.er-api.com, fetched at most once a day when online.
- AI: Groq `chat/completions` (JSON mode) and `audio/transcriptions`. Key and model names are set in the More tab and stay on the device.
- Backups: JSON, CSV, diary TXT, ICS calendar via the `files()` function.

## Ideas to expand
- Receipt photos, roommate split, savings goals, yearly PDF report, notifications, manifest and icons for install, charts library.
