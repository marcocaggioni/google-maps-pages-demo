# 🗺️ Addresses on a Google Map — GitHub Pages demo

A minimal example of a **Google Map embedded in GitHub Pages** whose markers are
driven by a **list of addresses stored in the repo** (`addresses.json`).

Edit `addresses.json`, push to `main`, and the map on the live site updates
automatically — no code changes needed.

**Live site:** https://marcocaggioni.github.io/google-maps-pages-demo/

## How it works

- `addresses.json` — the data. Each entry has `name`, `address`, `description`,
  and optional `lat`/`lng`. Entries with coordinates are plotted instantly;
  entries without are geocoded in the browser via the Maps JavaScript API.
- `index.html` — loads the JSON, drops one marker per address, and renders a
  clickable side list. Clicking a marker or a list entry opens an info window
  with the address and its description.
- `config.js` — holds your Google Maps API key (one line).
- `.github/workflows/pages.yml` — deploys the site to GitHub Pages on every push.

## Setup

### 1. Get an API key (free tier)

1. Go to the [Google Cloud Console](https://console.cloud.google.com/) and create a project.
2. **APIs & Services → Library** → enable **Maps JavaScript API**.
3. **APIs & Services → Credentials → Create Credentials → API key**.
4. Restrict the key (recommended): under *Application restrictions* choose
   **HTTP referrers** and add:
   `https://marcocaggioni.github.io/google-maps-pages-demo/*`
5. Paste the key into `config.js`, replacing `YOUR_API_KEY_HERE`.

Google requires a billing account on the project, but the Maps JavaScript API
includes a monthly free credit (~28,000 map loads) — this demo stays well inside it.

### 2. Add your own addresses

Edit `addresses.json`:

```json
{
  "places": [
    {
      "name": "My favorite café",
      "address": "123 Main St, Anytown, USA",
      "description": "Best espresso in town."
    }
  ]
}
```

`lat`/`lng` are optional — leave them out and the address is geocoded
automatically. Commit and push; the GitHub Action redeploys the site in about a minute.

### 3. View it

The site is live at https://marcocaggioni.github.io/google-maps-pages-demo/
