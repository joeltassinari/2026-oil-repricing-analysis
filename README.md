# 2026 Oil Repricing Analysis
**Joel Tassinari · April 2026**

An interactive research tool examining the divergence between WTI crude oil prices and equity market valuations across four sectors during the 2026 Hormuz disruption. Built entirely in a single self-contained HTML file — no server, no dependencies beyond a browser.

---

## What It Does

Oil opened 2026 at $57/bbl and reached $112 by early April — a 96% move in under three months. This tool asks a simple question: **have equity multiples moved to reflect that?**

For Airlines and Industrials, the answer is largely no. The model back-calculates the oil price implied by each sector's current EV/EBITDA multiples and compares it to actual WTI. The gap is the unpriced exposure.

A forward Monte Carlo simulation then models 2,000 oil price paths through December 31, 2026 across three geopolitical regimes, translating each path into WACC and equity impact estimates by sector.

---

## The Four Sectors

| Sector | Proxy | Sensitivity | Implied Oil (Apr 3) | Gap |
|--------|-------|-------------|---------------------|-----|
| Airlines | JETS | 90bps/$10 | ~$54/bbl | **+$58 unpriced** |
| Industrials | XLI | 42bps/$10 | ~$52/bbl | **+$60 unpriced** |
| Data Centers | MSFT/AMZN/META/GOOGL avg | 40bps/$10 | ~$92/bbl | +$20 unpriced |
| Software | IGV | 20bps/$10 | ~$138/bbl | −$26 over-corrected |

---

## How to Use

Open `entropy_trap_2026.html` in any modern browser. Best viewed on desktop.

- **Tab 1 — Repricing Gap:** Daily WTI vs. equity-implied oil prices, Jan 1 – Apr 3. Forward simulation fan through Dec 31. Hover any date for all four sector implied values and gaps.
- **Tab 2 — WACC Distribution:** Box plots showing total WACC expansion from the Jan 2 baseline across M3/M6/M9 intervals. Compare view shows all four sectors simultaneously. Detail view adds sector-specific analysis.
- **Tab 3 — Equity Impact:** DCF translation of WACC changes to equity value impact. Same Compare/Detail structure.
- **Tab 4 — Methodology:** Full source documentation, derivation arithmetic, and limitations. Collapsible sections.

Select Bull, Base, or Bear scenario in the sidebar and click **Run Simulation** to update all three chart tabs simultaneously.

---

## Data Sources

All data has a hard cutoff of **April 3, 2026**.

- **FactSet** — NTM EV/EBITDA daily: JETS, XLI, IGV, META, AMZN, MSFT, GOOGL (Jan 1 – Apr 3, 2026)
- **CME** — WTI front-month continuous (CL00-USA) daily close
- **FRED DGS10** — 10Y Treasury yield
- **EIA STEO** — March 10, 2026
- **Dallas Fed** — "Middle East Geopolitical Risk," Spellman & Zhou, Aug 2025
- **SF Fed** — "Changing Sensitivity of Interest Rates to Oil Supply News," Dec 2025
- **Damodaran** — Cost of Capital by Sector, January 2026
- **BLS** — Total Factor Productivity Table 11, December 2025
- **IATA** — Global Outlook & Fuel Fact Sheet, December 2025
- **Polymarket** — CL Jun-2026, $7.2M volume, retrieved April 3, 2026
- **CBOE OVX** — April 1, 2026

Full bibliography with URLs in the Methodology tab.

---

## Methodology Notes

**Implied oil derivation:** Gordon Growth WACC inversion on NTM EV/EBITDA (g=5%), net of 10Y Treasury rate moves, mapped back to oil via sector sensitivity coefficients.

**Forward simulation:** Ornstein-Uhlenbeck mean-reverting process on log price, 2,000 paths, 9 monthly steps (Apr–Dec 2026). Three regimes anchored to EIA STEO and Dallas Fed scenario analysis. Initial regime weights from Polymarket touch probabilities.

**WACC sensitivities** are derived estimates — not regression-estimated from time-series data. Components are verified against primary sources; aggregation involves judgment. Full derivation in Methodology Tab, Section 4.

**Equity translation** captures the discount rate effect only (100bps WACC ↑ ≈ 17% equity ↓, g=8%, terminal 25×, capped ±100%). Does not capture earnings estimate revisions from higher fuel costs, which would amplify headwinds for Airlines and Industrials beyond what the model shows.

---

## Disclaimer

This tool is for **educational and informational purposes only**. It does not constitute investment advice or a solicitation to buy or sell any security. Model outputs are illustrative and interpretive — not forecasts. Data is static as of April 3, 2026 and does not update in real time. See the in-app disclaimer for full terms.

---

## Feedback

Open to methodology critique, data corrections, and sector coverage suggestions. Pull requests welcome.
