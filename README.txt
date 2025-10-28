# Interactive Map Bundle (Token‑Free)

This bundle contains:
- **3d-globe-continent-country-select.html** — 3D globe (MapLibre GL, no token). Hover + click countries, continent zoom pills, Continue → redirects to Typeform with hidden fields.
- **interactive-world-continent-country-select.html** — 2D Leaflet fallback. Hover + click, continent zoom pills.
- **index.html** — Redirects to the 3D globe file by default.

## How to host (GitHub Pages)
1. Create a **public** repo.
2. Upload all three `.html` files to the **root** of the repo.
3. In **Settings → Pages**, set **Source: Deploy from branch**, **Branch: main**, **Folder: /(root)**.
4. Your site will be live at `https://<username>.github.io/<repo>/`.

## How to host (Netlify Drag‑and‑Drop)
1. Go to https://app.netlify.com/drop
2. Drag these three files in.
3. Use the root URL (index.html redirects to the 3D globe).

## Typeform integration
Open **3d-globe-continent-country-select.html** and set:
```js
const TYPEFORM_BASE_URL = "https://form.typeform.com/to/YourFormID";
const HIDDEN_FIELD_NAMES = { country: "country", continent: "continent" };
```
Add **Hidden fields** `country` and `continent` in Typeform.

## Kiosk on iPad
- Add hosted URL to Home Screen (full-screen web app look).
- Use **Guided Access** or **MDM Single App Mode** to lock down.

## Tech choices (no Mapbox token)
- **MapLibre GL JS** (open-source fork of Mapbox GL JS) with the public `demotiles.maplibre.org` style for the 3D globe.
- **Leaflet** + OpenStreetMap tiles for the 2D fallback.
- **Countries** come from a public GeoJSON (Natural Earth via the Holtzy gallery). We do the hit‑testing client‑side for selection.

## Advanced: Self‑hosted vector tiles (no tokens, Mapbox‑like)
If you want Mapbox‑quality rendering but no tokens, consider **Protomaps PMTiles** + **maplibre‑gl‑protomaps**:
- Download a world PMTiles (`.pmtiles`) from Protomaps.
- Serve the file and add it as a raster/vector source in MapLibre.
- This keeps you token‑free and removes reliance on external CDNs.

