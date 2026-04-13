# MRT-3 Crowd Patterns Dataset

**Author:** Dharl Russell C. Perez
**Date:** April 2026
**License:** MIT

Crowd busyness estimates for all 13 MRT-3 stations in Metro Manila by station, day of week, and hour of day. Derived from official DOTr ridership figures (baseline: 468,000 daily commuters, April 2026) using a weighted distribution model across 18 operating hours and 13 station-level load factors. Busyness scores (0–100) map to four crowd classes across confirmed weekday peaks (6–8 AM, 5–7 PM) and weekend afternoon surges. 1,638 rows. April 2026.

---

## What's in this dataset

| File | Description |
|---|---|
| `mrt3_crowd_patterns.csv` | Full dataset, 1,638 rows (13 stations x 18 hours x 7 days) |
| `mrt3_crowd_pattern_analysis.ipynb` | Full methodology notebook, sources, formulas, charts |
| `ridership_trend.png` | MRT-3 ridership trend from 2024 to April 2026 |
| `hourly_distribution.png` | Hourly weight distribution used in the model |
| `station_shares.png` | Passenger load share per station |
| `station_busyness.png` | Busyness heatmap for key stations |

---

## CSV Structure

| Column | Description |
|---|---|
| `station` | Station name |
| `hour` | Hour of day (5 to 22) |
| `hour_label` | Time (e.g. 8:00 AM) |
| `day` | Monday to Sunday |
| `busyness` | Busyness percentage (0 to 100) |
| `crowd_label` | Not busy / Moderately busy / Busy / Very busy |

---

## Methodology Summary

This is a **data-driven estimate**, not a real-time measurement. The methodology combines three components:

**1. Official ridership data**
Daily ridership figures sourced from DOTr-MRT3 press releases and news reports spanning 2024 to April 2026. The April 2026 baseline is 468,000 daily commuters, reflecting the 50% fare discount implemented on March 23, 2026 due to the Philippine energy crisis.

**2. Hourly distribution model**
Commuters are distributed across 18 operating hours (5AM to 10PM) using weighted curves based on confirmed peak windows:
- Morning peak: 6AM to 8AM (confirmed by MRT-3 GM Michael Capati, DZRH March 26, 2026)
- Evening peak: 5PM to 7PM
- Weekend: mall-driven afternoon surge (12PM to 6PM), no morning rush

**3. Station weight model**
Not all 13 stations carry equal loads. Terminus stations (North Avenue, Taft Avenue) and interchange stations (Araneta Center-Cubao, Ayala) are weighted higher. Smaller catchment stations (Kamuning, Boni) are weighted lower.

**Busyness formula:**
busyness % = (daily commuters x station share x hour weight x adjustment factor) / platform capacity x 100
Capped at 100%. Platform capacity estimated at 2,000 commuters per station based on train capacity and frequency data from GM Capati (Philstar, March 27, 2026).

Full methodology with all sources, formulas, and charts is documented in `mrt3_crowd_pattern_analysis.ipynb`.

---

## Data Sources

| # | Source | Data Used |
|---|---|---|
| 1 | DOTr-MRT3 Official Press Release (Jan 2026) | 2024 avg daily ridership: 375,474 |
| 2 | Philstar.com (Jan 5, 2026) | 2025 avg daily ridership: 388,000 |
| 3 | Philstar.com (Mar 27, 2026) | Post-fare cut daily ridership: 466,735 to 468,000 |
| 4 | DZRH News (Mar 26, 2026) | Peak hours confirmed by MRT-3 GM Michael Capati |
| 5 | Rappler.com (Mar 19, 2026) | 50% fare discount details |
| 6 | Expressway.ph (2026) | System at 120 to 150% capacity during peaks |
| 7 | Wikipedia (MRT Line 3) | Design capacity: 350,000 passengers/day |

---

## Stations Covered

North Avenue, Quezon Avenue, Kamuning, Araneta Center-Cubao, Santolan-Annapolis, Ortigas, Shaw Boulevard, Boni, Guadalupe, Buendia, Ayala, Magallanes, Taft Avenue

---

## Built For

This dataset powers **[Siksik](https://github.com/russperez/siksik-mrt-commuter-app)**, a React Native app that helps Filipino MRT-3 commuters check crowd busyness by station, day, and time.

---

## Disclaimer

This dataset is a data-driven estimate, not a real-time measurement. All figures are derived from cited public sources. The methodology is fully documented for transparency and reproducibility.
