# QSO Mate

GMRS & Amateur Radio contact log — a single-page web app (`index.html`) for logging Ham, YSF, DMR and GMRS contacts, with a roster, a contact map and JSON backup/restore.

## Build 2026-09-30-ysf4

**New**
- **YSF (System Fusion) contacts** — new service with Room / Reflector and DG-ID / Node fields, teal badge, Roster count and map filter.
- **Callsign autofill** — typing a callsign or ID you've logged before fills in the station's details from your roster; new US Ham callsigns are looked up in the FCC database (HamDB, with Callook as backup) for name and city.
- **QRZ links** — QRZ ↗ button on Roster cards, Recent Activity and map pop-ups for any station with a Ham callsign.

**Fixed / improved**
- Map tiles: CARTO now requires an API key, so the Geo Map uses Esri's free dark basemap, with OpenStreetMap as a backup and the radar view as the last resort.
- Smoother map on phones: waits for the map stylesheet before drawing, adds a Full screen mode, finer pinch zoom, bigger tap targets.
- The selected service (Ham / YSF / DMR / GMRS) stays selected between saves.
- Roster stats wrap neatly on narrow screens.

## Data
Your log is stored on the device (or in Claude storage when run as an artifact). Use **Profile → Export** regularly as a backup.
