## publix-edge-map

**Instacart shopper edge tool** — Interactive map for Publix stores within practical range of Belleview, FL (expanded ~80-150 mile central Florida coverage).

Live at: https://richardgoff1218-cmd.github.io/publix-edge-map (after Pages enabled)

### What it gives you
- Color-coded busyness (true red=packed → green=slow) using a grocery-tuned time-of-day + day-of-week model
- Your own logged observations heavily influence the displayed scores over time (builds your personal dataset)
- Median household income (curated ACS 5-year) per store ZIP — hunt high-income + currently lower busyness
- Trade area outlines: for key stores, estimated dense neighborhoods / subdivisions that feed that location (polygons on map)
- One-tap Google Maps deep links for live Popular Times graph + traffic confirmation (the only reliable "live" source)
- GPS: see distances, filter to stores near you right now
- Strong data gathering: quick-tap logging (Quiet/Normal/Busy/Packed) with timestamps. Export your history as CSV for personal analysis or future ML ideas.

### Key improvements over publix-intel-map (your previous repo)
- Much larger geographic scope and store count (22+ high-value locations seeded)
- Real polygon trade areas (not just circles) for The Villages and other dense zones
- First-class persistent personal logging that actually changes predictions
- Better red-green gradient and mobile bottom-sheet UX designed for quick glances between batches
- Time simulator to plan future shifts
- CSV export of *your* gathered data

### How the "live" busyness works (important)
There is no free public API for real-time Google Popular Times in a web app (scraping violates TOS and is fragile). 

This app uses:
1. A strong predictive model tailored to Florida grocery patterns (peaks 4-7:30pm weekdays, different on weekends/snowbird season)
2. **Your observations win**: The more you log for a specific store, the more the displayed score shifts toward reality you've seen. After 4-5 logs it becomes very personalized.
3. Prominent "Verify on Google Maps" button that jumps you straight to that store's live page (Popular Times graph + current traffic).

Over 2-3 weeks of normal use while dashing you will have excellent personal intel no one else has.

### 150 mile radius note
Full 150mi would include 80-100+ Publix. Current seed focuses on the highest-density, highest-value Instacart territory (Marion, Sumter/The Villages, Lake, Citrus, north Hernando, Alachua edges). Easy to expand.

### How to expand / improve data (you or me)
1. For more stores: Go to https://overpass-turbo.eu/ and run:
   ```
   [out:csv("name","lat","lon","addr:full","addr:postcode")][timeout:900];
   area["ISO3166-2"="US-FL"]->.searchArea;
   (node["brand"="Publix"](area.searchArea); way["brand"="Publix"](area.searchArea););
   out center;
   ```
   Filter the CSV to ~150mi of Belleview (29.06, -82.06), convert to the JSON format used in index.html.
2. For better polygons: Provide a list of stores + rough vertex coords (or describe neighborhoods), I will add precise Leaflet polygons.
3. Income: Current values are curated ACS approximates. Full Florida ZCTA CSV from data.census.gov can be converted.

### Phone "App" install
- Open the live URL in Safari (iOS) or Chrome (Android)
- Add to Home Screen
- It will feel and launch like a native app, works great offline for the data already loaded.

### Tech
- 100% static GitHub Pages (free, public)
- Leaflet + OpenStreetMap (no API keys)
- Tailwind via CDN
- Everything (including your logs) stays in your browser

Built for serious full-time Instacart shoppers who want a real data advantage in the Belleview / Ocala / Villages zone.

---

Next steps for this repo (tell me priorities):
- Add your full current store list from the other repo
- More detailed trade area polygons for 5-8 key locations
- "My Stats" dashboard (avg tip proxy by store, best times you personally observed, etc.)
- Batch scoring / multi-stop planner
- Darker or custom theme

Let's make this your daily driver.