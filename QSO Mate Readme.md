# QSO Mate

A single-file, self-contained contact logbook for GMRS, Amateur (Ham) Radio, and DMR — built to run as a Progressive Web App or be packaged into a standalone Android app. No backend, no account, no ads. Your data stays on your device.

## Features

- **Log contacts across three services** — Ham, DMR, and GMRS — with fields that adapt per contact:
  - Ham Callsign, DMR ID, and GMRS ID (fill in whichever apply; many contacts hold more than one)
  - Frequency/Repeater and Tone/Offset fields relabel automatically (e.g. "Talkgroup / Repeater" for DMR)
  - Visual S-meter signal strength picker (S1 through S9+40)
  - Location by city/town (auto-geocoded) or exact lat/lng
  - Optional custom timestamp and notes
- **Roster** — a master list of every station you've logged, with:
  - Search by callsign, GMRS ID, DMR ID, or name
  - Full contact history per station
  - Inline editing (add a Ham callsign you later learn for a GMRS-only contact, etc.)
- **Map**, in two modes:
  - **Geo Map** — a real map (OpenStreetMap-style tiles) that auto-fits its zoom to include every contact as you log farther ones
  - **Radar** — an offline distance/bearing plot centered on your home station, no internet required
  - Filter by service type (Ham / DMR / GMRS) with one-tap toggle chips
  - Automatically falls back to Radar if map tiles can't load
- **Profile** — your own callsign, license info, and home location (auto-computes your Maidenhead grid square)
- **Export / Import** — back up your whole log as JSON, or move it between devices. Export tries a native share sheet first, falls back to a direct download, and always offers a "show as text + copy" option that works everywhere.

## Privacy

- No login, no account, no analytics, no ads.
- All contact data is stored **locally on your device** — nothing is sent to any server except:
  - A geocoding lookup (via [Photon](https://photon.komoot.io)) for place names you type in, so they can be plotted
  - Map tile images (via [CARTO](https://carto.com)) when using Geo Map
- The app file itself contains no personal data — a fresh install always starts empty.

## Installing

### Option A: Add to Home Screen (easiest)
1. Host `index.html` somewhere with a stable URL — [Netlify Drop](https://app.netlify.com/drop) (drag-and-drop, no account needed) or GitHub Pages both work well.
2. Open that URL on your phone in Chrome.
3. Menu (⋮) → **Add to Home Screen**.
4. It installs with its own icon and opens full-screen, no browser bar.

> Hosting it first (rather than opening a downloaded file directly) matters — it gives the app a stable origin so your data reliably persists between sessions.

### Option B: Package as a standalone Android app
1. Zip `index.html` so it sits at the **root** of the zip (not inside a folder).
2. Upload the zip to [WebIntoApp](https://webintoapp.com) and generate an APK.
3. Download the APK to your phone and install it (you'll need to allow "install unknown apps" for whatever app you use to open it — Android will prompt you through this the first time).

## Data storage details

The app auto-detects where it's running:
- Inside a compatible host environment with a persistent storage API, it uses that.
- Otherwise (standalone PWA, packaged APK, or a plain downloaded file), it falls back to the browser's local storage.

Either way, storage is **tied to that specific device and install** — it won't sync across phones or browsers on its own. Use **Profile → Export** regularly as a backup, especially before reinstalling or switching devices, and **Profile → Import** to bring a backup back in.

The bottom of the Profile tab shows a build identifier — useful for confirming a fresh install/update actually took effect.

## Building your own version

The whole app is a single HTML file with inline CSS and JavaScript — no build step, no dependencies to install. Open it in any text editor, make changes, and reload. It uses:
- [Leaflet.js](https://leafletjs.com) for the Geo Map (loaded from a CDN on demand)
- [CARTO](https://carto.com) dark basemap tiles
- [Photon](https://photon.komoot.io) for geocoding place names

## Known limitations

- Local storage doesn't sync across devices — export/import is the current way to move data around.
- Geocoding is best-effort; unusual place names may not resolve. Use the **Retry locating** button on the Map tab's "Unmapped Contacts" list, or enter exact coordinates manually via the Log form's Advanced section.
- Requires an internet connection for the Geo Map and geocoding; the Radar view and all logging/roster features work fully offline.

## License

Choose a license that fits how you want to share this (MIT is a common permissive default for small personal-utility projects like this one) and add a `LICENSE` file to the repo.

## Credits

Map data © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors, tiles by [CARTO](https://carto.com), geocoding by [Photon](https://photon.komoot.io)/[Komoot](https://www.komoot.com), mapping powered by [Leaflet](https://leafletjs.com).
