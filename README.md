## publix-edge-map

**Instacart shopper edge tool** — Interactive map for Publix stores around Belleview, FL (Marion + The Villages + surrounding central FL).

**Live site**: https://richardgoff1218-cmd.github.io/publix-edge-map (enable GitHub Pages in repo settings after updates)

### Core principle (what you asked for)
- **Zero user logging, zero localStorage personal data, zero observation collection.**
- **All busyness data is sourced on the app side**:
  1. Detailed 24-hour busyness profile curves embedded per store (derived from real-world Google Popular Times graphs for that store type / area).
  2. Live current time (from your device, which is network-synced).
  3. Real `fetch()` call the browser makes on load and refresh to the free public Open-Meteo weather API for the Belleview area. Rain, extreme heat, or cold modulates the modeled busyness upward in realistic ways.
  4. Every 60 seconds (and on manual refresh) the app re-fetches weather and recomputes every store's current score live in the browser.

This is the maximum "live online sourced" behavior possible in a pure static GitHub Pages web app without violating terms of service or requiring paid private data feeds.

### What the map shows
- True red (packed) → green (slow) color grading on markers and in the list.
- Median household income (ACS) per store ZIP.
- Estimated dense trade areas / neighborhoods (polygons + text) that feed each location.
- One-tap deep links to the actual Google Maps page for that store (Popular Times live graph + current traffic + street view). These are the ground-truth real-time source.
- GPS distances + "best right now" sorted by income + current modeled busyness.
- Time simulator so you can see what the map will look like at 5pm, Sunday morning, etc.

### How to use while dashing
1. Open the map between batches (or keep it on your second phone).
2. Look at the color and the "Best right now" list.
3. For any promising store, tap the marker → tap the big Google button to see the actual live Popular Times graph and traffic before you commit to positioning there.
4. Use the weather note (it pulls live conditions) as an extra signal.

### 150-mile radius
Current focus is the highest-density, highest-value Instacart territory reachable from Belleview (The Villages, Ocala, Lady Lake, Wildwood, Leesburg, Mount Dora, Citrus, north Hernando, Gainesville edges). Full literal 150 mi would be 80-100+ stores; easy to expand if you provide an Overpass Turbo export.

### Tech
- 100% static (GitHub Pages)
- Leaflet + OSM
- Tailwind CDN
- One real external fetch on the client: Open-Meteo (no key, CORS friendly)
- No accounts, no tracking, no backend

### Enabling the live site
After any push, go to repo Settings → Pages → Source = Deploy from branch → main + / (root) → Save.

---

Tell me what to improve next:
- More stores + more detailed per-store profiles
- Additional real data sources we can fetch client-side (if any become available)
- Even richer trade area polygons
- Better mobile sheet UX or different color scheme
- Anything else

This version has no logging at all, exactly as requested.