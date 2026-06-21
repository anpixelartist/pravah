# Pravah — Flipkart GRiD · Prototype Round 2 submission

Copy-paste values for each form field. Files to upload live in this `submission/` folder.

---

## Title *
```
Pravah — Glass-Box Parking-Pressure Command Centre (PS1)
```
(shorter alt: `Pravah — Stop Counting Tickets, Start Recovering Time`)

---

## Description *  (paste into the rich-text box; bold the **marked** bits)

**Pravah** turns Bengaluru's parking-violation data into a decision tool for the Traffic Police.
Police today count *violations* and deploy by gut — but 500 helmet tickets can cause zero
congestion while one truck at a chokepoint costs thousands of vehicle-hours. Pravah re-expresses
every violation as **hours of stuck traffic**, ranks each junction by a single **pressure score
(0–100)**, exposes the city's evening **blind spots**, **predicts** which junctions worsen next
week, and outputs an **officer-deployment plan with a reason on every pick**.

**What's novel**

- **The data lies by omission, and we correct for it.** Tickets only exist where officers stood.
  Only **0.85%** of all tickets are written in the 3–9pm rush (FACT) — an enforcement blind spot,
  not an absence of violations. We surface it instead of reinforcing it.
- **Glass box, never black box.** Every score decomposes into named parts; every recommendation
  states why, in plain language a constable can act on. Tune the priorities and the whole city
  re-ranks live.
- **Interpretable AI.** A gradient-boosted model forecasts next-week pressure per junction
  (**R² = 0.844** on held-out weeks, beating naive persistence by 6.2% MAE), with SHAP reasons —
  never a neural net.
- **Honest by design.** Every figure is badged **FACT** (measured), **EST** (modelled) or **AI**
  (predicted). We even say where our edge is small (re-ranking deployment adds only ~3–5%; the real
  win is covering the blind hours and phantom hotspots count-based patrols never see).
- **Runs 100% offline** on a real Bengaluru street map — no tiles, no APIs, no internet at demo time.

**How it answers PS1 (Parking-Induced Congestion):** reactive enforcement → a forward forecast;
no impact heat-map → a live pressure map of 137 junctions; hard to prioritise → ranked list +
phantom hotspots; quantify impact → hours of stuck traffic; targeted enforcement → an explained
deployment plan.

Built on **298,445 real parking-violation records**. Repo: github.com/anpixelartist/pravah ·
Live: anpixelartist.github.io/pravah

---

## Theme *
Pick the option in the dropdown closest to **Smart Cities / Urban Mobility / Sustainability**
(or **Logistics & Supply Chain** if those aren't offered). Rationale to keep in mind: Pravah is a
civic urban-mobility decision tool that recovers commuter-time and reduces congestion — frame it as
smart-city / sustainable-mobility. *(Tell me the exact dropdown options and I'll pick the best one.)*

---

## Snapshots   (upload — `submission/snapshots/`)
1. `01-overview.png` — headline KPIs + the blind-clock story
2. `02-city-map.png` — the live Bengaluru street map, pressure dots + phantom rings
3. `03-junction-glassbox.png` — a junction's decomposed score + forecast + raw evidence
4. `04-deployment.png` — officer plan with reasons + equity check
5. `05-forecast.png` — interpretable model card (R²) + predicted risers

## Video URL *
*(skipped — record a 2–3 min screen walk-through of the live demo and paste the link.)*

## Presentation *   (upload)
`submission/pravah-deck.pdf`  (9-slide pitch deck, ~8 MB)

## Demo Link *
```
https://anpixelartist.github.io/pravah/
```
*(One-time enable: GitHub repo → Settings → Pages → Source: “Deploy from a branch” → branch
`gh-pages` → `/ (root)` → Save. Live in ~1 min. Fallback demo: unzip the source and double-click
`web/index.html` — it runs fully offline.)*

## Repository URL *
```
https://github.com/anpixelartist/pravah
```

## Source Code *   (upload)
`submission/pravah-source.zip`  (full project, no raw data; ~0.5 MB)

---

## Instructions to Run *  (paste into the rich-text box)

**Fastest — just open it (no setup, works offline):**
1. Open the live demo: **https://anpixelartist.github.io/pravah/**, or
2. From the source zip, double-click **`web/index.html`** — it runs entirely in the browser with no
   server and no internet.
3. Explore: tap any dot for a junction's score, forecast and evidence; use the top tabs for
   **Priorities**, **Deploy** (move the officer slider) and **Forecast**; scroll/pinch to zoom the map.

**To regenerate everything from the raw data (optional, for reviewers):**
1. `python -m venv .venv && pip install -e ".[dev,ml]"`  (or `make setup`)
2. Place the provided parking-violation CSV in `data/raw/` (see `data/raw/README.md`).
3. `make aggregates` — rebuilds `web/data.js`; prints the FACT check (evening 0.85%, top junction
   Safina Plaza, ~3,489 repeat offenders) and the MODEL line (R² ≈ 0.84).
4. `make test` — runs the unit suite; `python scripts/e2e_check.py` runs data-integrity checks.
5. Open `web/index.html`.
