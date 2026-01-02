# U.S. Inflation Drivers & Forecasting (1958–2024+)  
A macroeconometric project studying the drivers of U.S. inflation and building forecasting + recession-warning models using monthly data.

🌐 **Project website:** https://dianaaleksieieva.github.io/inflation-project/

---

## Overview
This project analyzes the drivers of U.S. inflation and builds forecasting models to predict inflation direction and levels. It uses a **monthly macroeconomic dataset (1958–2024)** sourced from **FRED, BLS, BEA, EIA, and the U.S. Treasury**, including consumer prices, labor markets, GDP growth, energy markets, trade/external balances, interest rates, yield-curve spreads, and inflation expectations. :contentReference[oaicite:0]{index=0}

The analysis combines:
- **Structural econometrics** (Phillips Curve / Augmented Phillips Curve + regression)
- **Time-series forecasting** (SARIMAX with exogenous macro variables)
- **Dynamic multivariate modeling** (VAR)
- **Recession warning signals** (yield curve + macro-financial indicators) :contentReference[oaicite:1]{index=1}

---

## Key Findings (High level)
- The **classic Phillips Curve** (inflation ↔ unemployment) is weak in modern U.S. data; unemployment explains little variation in inflation. :contentReference[oaicite:2]{index=2}  
- In the **Augmented Phillips Curve**, **expected inflation** is a dominant driver, while the unemployment gap effect is comparatively small/fragile depending on specification. :contentReference[oaicite:3]{index=3}  
- A linear model highlights key predictors including **oil price changes, natural gas prices, GDP growth, and inflation persistence dynamics**. :contentReference[oaicite:4]{index=4}  
- For forecasting, **SARIMAX performed best** and is used to produce **two-year inflation forecasts**. :contentReference[oaicite:5]{index=5}  
- **VAR** is valuable for understanding **shock propagation** and shows stronger stability for medium/long horizons, even if short-run accuracy is lower. :contentReference[oaicite:6]{index=6}  

---

## Dataset
**File:** `economic_combined_data.csv` :contentReference[oaicite:7]{index=7}  
**Frequency:** Monthly  
**Sample period:** **February 1957 – September 2025** :contentReference[oaicite:8]{index=8}  

### What’s inside (examples)
The dataset integrates inflation metrics (CPI/Core CPI), labor market variables (unemployment, unemployment gap), policy rates (Fed funds), yield curve measures, energy prices (Brent oil, natural gas, gasoline), trade balance, GDP and growth, dollar index, and an NBER recession indicator. :contentReference[oaicite:9]{index=9}  

### Reproducible data pipeline (summary)
- Load & standardize major series (CPI/Core CPI, unemployment, earnings)
- Merge series by date (outer joins for full coverage)
- Compute derived metrics (inflation rates, YoY, logs, wage growth)
- Integrate commodities, rates, expectations, and CPI components
- Aggregate daily → monthly averages
- Trim unreliable edge dates :contentReference[oaicite:10]{index=10}  

---

## Methods
### 1) EDA + Phillips Curve
- Test whether inflation vs unemployment gap still holds in modern U.S. data
- Show why labor market slack alone is insufficient (structural changes, globalization, supply shocks, credibility of monetary policy, etc.) :contentReference[oaicite:11]{index=11}  

### 2) Augmented Phillips Curve (expectations-augmented)
- Add **expected inflation** to improve explanatory power
- Compare classic vs augmented interpretations :contentReference[oaicite:12]{index=12}  

### 3) Linear regression + subset selection
- Use subset selection to identify a compact set of strong predictors
- Emphasis on energy shocks + growth + inflation persistence :contentReference[oaicite:13]{index=13}  

### 4) SARIMAX forecasting (main forecasting model)
- Target: log annual change in core CPI (stationarity checked with ADF/KPSS)
- Grid search over SARIMA seasonal/non-seasonal parameters
- Multi-stage screening of exogenous predictors (levels/differences as appropriate)
- Robustness: **108-fold expanding-window** validation over **1–12 month** horizons
- Final chosen structure: **SARIMA(1,1,1)(0,0,2)[12]** + **3-month lag differential Fed funds rate**
- Used to generate **inflation forecasts for the next two years** :contentReference[oaicite:14]{index=14}  

### 5) VAR system model
- Captures dynamic interactions (inflation, labor, rates, energy)
- Useful for impulse/shock transmission and medium/long-run stability :contentReference[oaicite:15]{index=15}  

### 6) Recession prediction / warning model
- Builds recession warnings based on **yield curve signals** and macro-financial indicators :contentReference[oaicite:16]{index=16}  

---


## Limitations & Future Work
See the website’s **Limitations** and **Future Work** sections for planned extensions (robustness, alternative specifications, structural breaks, additional predictors, etc.). :contentReference[oaicite:17]{index=17}  

---

## Data Sources
- FRED (Federal Reserve Economic Data)
- BLS (Bureau of Labor Statistics)
- BEA (Bureau of Economic Analysis)
- EIA (Energy Information Administration)
- U.S. Treasury  
(Integrated into a single monthly dataset as described above.) :contentReference[oaicite:18]{index=18}

---

## Authors
Diana Aleksieieva
Hao Zhu
Hong Zhao