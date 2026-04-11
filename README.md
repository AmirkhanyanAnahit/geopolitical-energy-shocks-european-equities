# Geopolitical Energy Shocks and European Equities

## Overview
How do geopolitical energy shocks reshape performance across European equities?

This project studies how **energy-stress periods** affect firms across four economically sensitive sectors:

- **Airlines:** Ryanair, Lufthansa  
- **Transportation / Logistics:** DHL Group, Maersk  
- **Chemicals:** BASF, Covestro  
- **Energy:** Shell, TotalEnergies  

The notebook combines **cross-sector comparison**, **benchmark-relative analysis**, **Brent sensitivity analysis**, and **volatility-regime analysis** to understand which firms are most vulnerable, which are more resilient, and how oil-related stress transmits through European equity markets.

---

## Repository structure
- `geopolitical_energy_shocks_european_equities.ipynb` — main notebook with the full workflow
- `README.md` — project summary, methodology, and key findings

---
## Research Question
How do geopolitical energy-shock periods affect the relative performance and vulnerability of selected European firms across airlines, transportation/logistics, chemicals, and energy?

### Sub-questions
1. Which firms and sectors perform best and worst over the sample?
2. Which firms appear more resilient within the same sector?
3. How strongly are stock returns linked to **Brent** versus the **STOXX Europe 600**?
4. What changes during **high Brent-volatility** periods?
5. What investment-style conclusions can be drawn from the cross-sector evidence?

## Data
Daily market data is downloaded using `yfinance` for the following period:

- **Start:** 2022-01-01  
- **End:** 2026-03-11  

### Assets used
- Ryanair
- Lufthansa
- DHL Group
- Maersk
- BASF
- Covestro
- Shell
- TotalEnergies
- STOXX Europe 600
- Brent crude oil

---

## Methodology

### 1. Return construction
- Daily close prices are downloaded
- Missing values are forward-filled where needed
- Daily returns are computed

### 2. Absolute performance analysis
The notebook compares:
- cumulative returns,
- average daily returns,
- and return volatility.

### 3. Benchmark-relative analysis
Each company’s relative return is computed against the **STOXX Europe 600**:

\[
r^{rel}_{i,t} = r_{i,t} - r^{STOXX600}_t
\]

This helps isolate firm-specific or sector-specific performance from broad market movements.

### 4. Correlation analysis
The notebook measures:
- correlation with **Brent**
- correlation with **STOXX Europe 600**
- the balance between oil linkage and broad market linkage

### 5. Brent-volatility regime analysis
A 20-day rolling Brent-return volatility measure is used to define:
- **Low volatility:** bottom 30%
- **High volatility:** top 30%

Average returns and benchmark-relative returns are then compared across those two regimes.

### 6. Cross-sectional regression layer
For each company, daily returns are regressed on:
- **STOXX Europe 600 return**
- **Brent return**

This separates broad market exposure from direct oil sensitivity.

---

## Main Results

### Absolute performance
Final cumulative returns over the sample:

| Company | Final cumulative return |
|---|---:|
| TotalEnergies | 0.9148 |
| Shell | 0.8732 |
| Ryanair | 0.6683 |
| Lufthansa | 0.2761 |
| STOXX Europe 600 | 0.2269 |
| Maersk | 0.2161 |
| Covestro | 0.1599 |
| Brent | 0.0975 |
| BASF | -0.0856 |
| DHL Group | -0.0957 |

### Relative performance vs STOXX Europe 600
Final cumulative relative returns:

| Company | Final cumulative relative return |
|---|---:|
| TotalEnergies | 0.5275 |
| Shell | 0.4737 |
| Ryanair | 0.3674 |
| Lufthansa | 0.0512 |
| Maersk | -0.0073 |
| Covestro | -0.0774 |
| BASF | -0.2429 |
| DHL Group | -0.2463 |

### Oil sensitivity: simple correlation view
Correlation with Brent daily returns:

| Company | Corr. with Brent |
|---|---:|
| Shell | 0.4784 |
| TotalEnergies | 0.4311 |
| Maersk | 0.0735 |
| Covestro | 0.0258 |
| BASF | 0.0187 |
| DHL Group | -0.0508 |
| Lufthansa | -0.1376 |
| Ryanair | -0.1454 |

### Interpretation
- Energy names show the clearest **positive Brent sensitivity**.
- Airlines are **negatively exposed**.
- Chemicals show weaker and less direct oil sensitivity.
- Transportation/logistics appears more mixed.

### Brent-volatility regimes
High-Brent-volatility minus low-Brent-volatility average daily return:

| Company | High minus low |
|---|---:|
| Lufthansa | 0.002257 |
| Ryanair | 0.001722 |
| BASF | 0.001491 |
| Covestro | 0.000619 |
| Shell | -0.000094 |
| Maersk | -0.000211 |
| DHL Group | -0.000257 |
| TotalEnergies | -0.000269 |

A useful nuance appears here: **high oil volatility is not automatically best for oil equities**. Energy firms remain the strongest names overall, but in regime comparisons, airlines and some industrial names show stronger high-minus-low differences than expected.

### Regression layer
The regression summary classifies firms broadly as:

- **Positive Brent sensitivity:** Shell, TotalEnergies, Maersk
- **Negative Brent sensitivity:** Ryanair, Lufthansa, DHL Group
- **Weak / insignificant Brent sensitivity:** BASF, Covestro

---

## Key Findings
- **Energy is the strongest sector overall** in the sample.
- **TotalEnergies and Shell** combine the best absolute performance, strongest benchmark-relative outperformance, and the clearest positive Brent sensitivity.
- **Ryanair** stands out as a strong outperformer and clearly outperforms Lufthansa.
- **Chemicals appear weakest overall**, especially BASF.
- **DHL Group** is one of the weakest names in both absolute and relative terms.
- Most firms are still more strongly linked to the **broader European market** than to Brent on a day-to-day basis.
- The relationship between oil stress and equities is **not one-dimensional**: sector structure, market environment, and firm-specific resilience all matter.

---

## Why this project matters
This project combines:
- cross-sectional equity analysis,
- sector comparison,
- benchmark-relative performance measurement,
- regime analysis,
- and regression-based interpretation.

That makes it relevant for:
- **equity research**
- **asset management**
- **macro-financial analysis**
- **market and sector risk work**

## Tech Stack
- `pandas`
- `numpy`
- `yfinance`
- `matplotlib`
- `statsmodels`

## How to run
1. Install the required Python packages.
2. Open the notebook.
3. Run the cells from top to bottom.
4. The notebook downloads data directly from Yahoo Finance, so an internet connection is required.

## Possible extensions
- Add event-study windows around specific geopolitical shocks
- Use rolling regressions instead of static full-sample regressions
- Add downside-risk metrics such as drawdowns or tail-risk measures
- Compare single-name equities with sector ETF proxies
- Separate **price shocks** from **volatility shocks**
