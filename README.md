# Brent / DXY Correlation Analysis

An empirical investigation into the relationship between Brent crude and the US dollar index (DXY), and the conditions under which that relationship breaks down.

Built as part of an ongoing effort to develop Python-based market analysis skills alongside my economics degree, with a focus on commodity markets.

---

## Research Question

Brent crude and the US dollar typically exhibit a negative correlation: a stronger dollar makes oil more expensive for non-dollar buyers, dampening demand and pushing prices down. This project asks when and why that relationship inverts — and what the mechanism is.

---

## Findings

The negative correlation inverted on two distinct occasions between 2021 and 2024, each driven by a different macro regime:

**Early 2022 — Russian Invasion of Ukraine**
Both Brent and DXY rose simultaneously. Brent was driven higher by supply shock fears, sanctions risk, and tight pre-war inventories. DXY strengthened on aggressive Fed tightening relative to a lagging ECB and BoJ, compounded by safe-haven demand following the invasion. Two independent upward drivers overwhelmed the normal mechanical link.

**Late 2023 — Global Growth Softening**
Both assets fell together. DXY weakened as markets priced Fed rate cuts and easing inflation. Brent fell on weak Chinese demand, broader manufacturing slowdown, and rising non-OPEC supply from the US, Brazil, and Norway. The October 7th attack briefly triggered a geopolitical risk premium, but investors concluded the supply impact would be short-lived.

In both cases, the 'normal' relationship was overwhelmed by a dominant macro regime driving both assets in the same direction.

---

## Structure

```
brent-dxy-analysis/
│
├── Brent_DXY_relationship.ipynb   # Main analysis notebook
└── README.md
```

**Notebook structure:**
- Data ingestion — Brent and DXY via `yfinance`
- EDA — price levels, moving averages, rolling volatility
- Methodology — why returns are used over price levels for correlation
- Rolling correlation construction — 60-day window on daily returns
- Visualisation — annotated price and correlation charts with breakdown windows marked
- Interpretation — written analysis of each breakdown episode

---

## Methods

- **Data:** Daily OHLC via `yfinance` (`BZ=F` for Brent, `DX-Y.NYB` for DXY), January 2021 – January 2024
- **Returns:** Log-percentage daily returns to ensure stationarity and remove heteroscedasticity
- **Correlation:** 60-day rolling Pearson correlation on returns
- **Visualisation:** `matplotlib` with dual y-axis, shaded breakdown windows, and event markers

---

## Dependencies

```
yfinance
pandas
matplotlib
```

Install with:

```bash
pip install yfinance pandas matplotlib
```

---

## Limitations

- Rolling correlation is sensitive to window length — 60 days is a deliberate choice balancing responsiveness and noise, but results shift with different windows
- Correlation does not imply causation; the analysis is descriptive, not causal
- DXY is a trade-weighted index dominated by EUR (~58%) — it is not a perfect proxy for broad dollar strength

---

*Part of an ongoing series of market analysis projects. Feedback welcome.*
