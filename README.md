## publix-edge-map

**Instacart shopper edge tool** — Flashy, high-density Publix map for the full Central Florida corridor (Tampa Bay ↔ Orlando metro ↔ Ocala ↔ The Villages).

**Live site**: https://richardgoff1218-cmd.github.io/publix-edge-map

### New in this version
- **65+ Publix locations** across Tampa, Orlando metro, Ocala, The Villages (very dense), Lady Lake, Leesburg, Mount Dora, Clermont, and all connecting corridors.
- **Map (left) + List (right)** layout. The list is **permanently sorted highest median household income first** so you can instantly see the best earning potential stores.
- Click any store in the list → the map smoothly flies/zooms to it, highlights the pin, and opens the rich detail sheet.
- Complete flashy/polished design overhaul: deep dark palette, heavy drop shadows, strong popout cards, vibrant accents, hover lift effects, modern elevation.

### Core (unchanged)
- **Zero user logging** of any kind.
- All busyness is **sourced live on the client**:
  - Detailed 24h profile curves per store (from observed Google Popular Times).
  - Real browser `fetch` to free Open-Meteo weather API (Belleview coords) every refresh — rain/heat/cold modulates scores.
  - Scores + colors recompute automatically every 60s.
- One-tap Google Maps links for the true real-time Popular Times graph + traffic.

### How to use on your phone while dashing
1. Keep the page open (add to home screen for PWA feel).
2. Glance at the right-hand list — top = highest income areas (best tip odds).
3. Tap a high-income store in the list → map jumps to it instantly.
4. Check the live modeled busyness + tap the big green Google button for the actual current graph before you head there.

### Enabling / updating the site
Repo Settings → Pages → Deploy from `main` branch, root folder.

---

Next requests welcome (more stores, even richer polygons, additional live data sources, batch planner, etc.).