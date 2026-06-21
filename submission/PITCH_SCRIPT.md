# Pravah — 3-minute pitch script (Flipkart GRiD · Round 2)

Live demo: **https://anpixelartist.github.io/pravah/**  ·  Repo: github.com/anpixelartist/pravah

Run the demo on screen throughout. One person drives the screen; speakers hand off cleanly.
Total ≈ 3:00. Timings are guides — keep energy up, don't read slides.

**Roles (play to each person's strength):**
- **Aditi** — narrator: the opening hook + the close (the parts that set tone and land the ask).
- **Nixita** — the problem & the data insight.
- **Pritipratyush** — the solution: the scoring engine + the AI model (and lead on technical Q&A).
- **Rashmi** — drives the live demo on screen + brings the energy.

---

## 0:00–0:20 — Hook  · **Aditi**
> "Bengaluru logs **298,445** parking violations in five months. But here's the number that
> matters: only **0.85%** are caught in the 3-to-9 PM rush — exactly when the city is gridlocked.
> Police are counting tickets. Commuters are losing hours. We built **Pravah** to fix that."

*(Screen — Rashmi: the live demo is open on the **Overview** panel.)*

## 0:20–0:55 — The problem & the blind spot  · **Nixita**
> "Today enforcement is reactive and measured in the wrong currency — tickets, not time. There's
> no impact map and no way to prioritise. And the data **lies by omission**: tickets only exist
> where officers already stood."
>
> "Look at the clock — enforcement peaks in the morning, then **goes dark after 3 PM**. The
> junctions that *are* watched in the evening still write 15% of their tickets then. So it's an
> **enforcement gap, not reality** — plus **12 phantom hotspots**, thousands of violations off the
> official radar." *(everything here is labelled FACT)*

*(Screen — Rashmi: close the panel → pan/zoom the **map** so the city + dots show.)*

## 0:55–1:30 — The solution: a score you can trust  · **Pritipratyush**
> "Pravah turns every violation into **hours of stuck traffic** and gives each junction one
> **pressure score, 0–100** — like an air-quality index for congestion. And it's a **glass box**."
>
> *(Rashmi taps **Safina Plaza**.)* "Tap any junction and the score breaks open: how bad the
> parking is, the evening blind spot, the volume — in points — plus the **raw tickets** behind it.
> Every number can be defended to a senior officer or an RTI request."

## 1:30–2:00 — The AI: it sees next week  · **Pritipratyush**
> *(Rashmi opens **Forecast** — the worsening junctions light up coral on the map.)*
> "This is our interpretable model. It predicts **next week's** pressure per junction — **84%
> accurate (R²) on weeks it never saw**, beating the naive baseline. Gradient-boosted trees with
> SHAP reasons — **never a neural net**, so every prediction is explainable. These coral junctions
> are the ones to **pre-position officers at before they blow up.**"

## 2:00–2:30 — From insight to action  · **Aditi**
> *(Rashmi opens **Deploy**, slides the officer count.)* "Set your real officer count and Pravah
> writes the plan — **a reason on every pick**, and an equity check so no area is starved."
>
> "We're honest about it: re-ranking alone adds a few percent. The decisive win is **structural** —
> Pravah's picks cover the evening blind hours and phantom spots that ticket-led patrols **never
> see**. And it runs **100% offline** — no internet at demo time."

## 2:30–3:00 — Close & ask  · **Aditi**
> "Good inputs, transparent reasoning, a human in the loop — Pravah recommends, the officer
> decides. It's built, validated end-to-end, and ready to pilot on the live feed."
>
> "**Stop counting tickets. Start recovering time.** That's Pravah."

---

## Key numbers (have these cold)
- **298,445** violations · **21.4 weeks** · 137 ranked junctions · **only 0.85%** in 3–9 PM (FACT)
- **12** phantom hotspots · **~3,489** repeat-offender vehicles (FACT)
- Model: **R² 0.844** on held-out weeks (vs 0.827 naive) · **35** junctions flagged worsening (AI)
- Every figure badged **FACT** (measured) · **EST** (modelled) · **AI** (predicted)

## Demo click-path (Rashmi)
Overview → close → zoom map → tap Safina Plaza → Forecast (watch coral light up) → Deploy (move slider) → close.
*Backup if Wi-Fi fails:* the same site runs offline — open `web/index.html` from the source zip.

## Likely judge questions (Pritipratyush leads; Aditi reframes)
- **Privacy?** Vehicle numbers are personal data — used only for the repeat-offender count, with hashing/
  access-control/retention rules noted; none of it ships to the browser.
- **Why not deep learning?** Buyers are police; decisions face RTI and senior review. We trade a little
  predictive ceiling for explainability — gradient boosting + SHAP. That's the point, not a limitation.
- **Is the model overfit?** No — validated **forward in time**: trained on early weeks, scored on weeks
  16–20 it never saw. Numbers regenerate from data; nothing is hardcoded.
- **Only a few percent better deployment?** Yes, and we say so — ticket-count and impact correlate 0.98.
  The real value is the blind-spot + phantom coverage and the forward forecast.
- **Does it use external/live data?** No — only the provided parking dataset for analysis; runs offline.
- **How does it productionise?** Same JSON, produced from the live parking feed instead of a static file —
  that's the only seam that changes.

## On-stage do's
- Let the **map and the coral forecast** do the talking — point, don't read.
- Say **FACT / EST / AI** out loud at least once — it signals rigor.
- End on the tagline. Smile. Stop talking.
