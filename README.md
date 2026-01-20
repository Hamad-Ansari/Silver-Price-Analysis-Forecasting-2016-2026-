# Silver Price Analysis & Forecasting (2016–2026)

**Author:** *Hammad zahid*  
**Role:** Data Scientist & Market Analyst  
**Data Source:** Yahoo Finance (via `yfinance` – pre-downloaded as CSV)  
**Ticker:** `SI=F` (COMEX Silver Futures)  

---

## 1. Project Overview

This notebook performs a **full end-to-end analysis** and **forecasting** of COMEX Silver Futures prices from **Jan 2016 to Jan 2026**, using:

- **Python stack:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `Prophet`, `statsmodels`
- **Methods:**
  - Exploratory Data Analysis (EDA)
  - Time Series Analysis (trend, seasonality, stationarity tests)
  - Feature Engineering (returns, volatility, technical indicators, calendar features)
  - Machine Learning Forecasting (Tree-based model)
  - Probabilistic Time Series Forecasting (Prophet)
  - Model Evaluation & Error Metrics
  - Future Price Projections & Market Interpretation

**Files used:**
- `silver_prices_data.csv` – Historical daily silver futures prices (2016–2026)
- `silver_price_forecast_2026.csv` – Predicted daily prices for Q1 2026 (Jan–Mar) from another model / file

We aim to produce **Kaggle & GitHub–ready** code: clean, modular, and error-free, with high-quality plots.

---
![b_creat_a_image_for_Si (1)](https://github.com/user-attachments/assets/28711d33-1be6-4add-97ae-3d2fe29ead70)



### 3.4. Initial Observations & Hypotheses

**Observations (Raw Data):**
- Data spans roughly **10 years** with **daily frequency** (weekdays, plus holiday gaps).
- Standard OHLCV structure with `Open`, `High`, `Low`, `Close`, `Adj Close`, `Volume`.
- No catastrophic missingness after basic filling.

**Hypotheses:**
1. **Macro-driven trends:** Silver prices will show clear **upward spikes** during periods of macro uncertainty (e.g., COVID-19 period, inflation waves) and may correlate with broader risk sentiment.
2. **Seasonality:** There may be **annual** or **monthly** seasonal components, possibly driven by industrial demand cycles and investment flows.
3. **Volatility clustering:** Periods of high volatility likely follow macro shocks; daily returns should exhibit volatility clustering.
4. **Stationarity:** Raw prices will be **non-stationary**, but **log-returns** are expected to be closer to stationary, suitable for modeling and forecasting volatility or short-term movements.
<img width="1384" height="584" alt="3f9b4579-468f-451b-8599-c9fd66e75ead" src="https://github.com/user-attachments/assets/3f3acbf3-9740-48f7-803e-def7eae147ef" />
<img width="1584" height="584" alt="c5f726c8-b964-4164-a4a4-4aad7d8c0b55" src="https://github.com/user-attachments/assets/35f1710b-d009-495f-a245-27730af1bf4d" />

<img width="1384" height="584" alt="35f68fb2-3c6c-4a45-9ef2-b8dd6983daf7" src="https://github.com/user-attachments/assets/5ad4a59d-2b8b-4661-9f48-d145c0f20199" />
<img width="1384" height="584" alt="ab6dd7d9-1e0c-4c6e-8a5d-867d69362819" src="https://github.com/user-attachments/assets/a6f7b224-0cc5-45a4-871f-3edb81e80a9a" />
<img width="1384" height="584" alt="0b4dea25-f789-4639-8247-f3563a79e9bb" src="https://github.com/user-attachments/assets/bb1773bf-4642-4ee0-a05e-aa63e5dd36a9" />
<img width="1384" height="584" alt="0b60be73-69f1-493f-9702-6a9c7ed3ed69" src="https://github.com/user-attachments/assets/5d75d49c-5e76-4949-a855-5ac7dd6088d6" />
### 11.3. Market Interpretation (High-Level)

**Trend Outlook (Based on Model):**
- The model suggests a **moderately bullish to stable trend** over the coming months, conditional on historical patterns.
- Prediction intervals widen over time, reflecting **uncertainty accumulation**.

**Macro & Market Considerations (Non-quantitative, interpretive):**
- **Upside drivers:**
  - Persistent or resurging **inflation** boosting demand for precious metal hedges.
  - Industrial expansion (electronics, solar) supporting **physical demand**.
  - Geopolitical tensions driving **safe-haven flows**.

- **Downside risks:**
  - Stronger USD and higher real yields can **pressure precious metals**.
  - Slowing global manufacturing would reduce **industrial usage**.
  - Mean-reversion after strong rallies.

**Strategic Takeaways:**
- For **investors**, silver appears as a **cyclical hedge** with significant upside in stress periods.
- For **industrials**, cost planning should consider the model’s **upper interval** as a risk-budgeting reference.
- For **traders**, short-term forecasts from RF and structural trends from Prophet can be combined into a **tactical strategy**.

All projections are **model-based** and must be complemented by **contemporary macro data and news flow** before real-world decisions.
