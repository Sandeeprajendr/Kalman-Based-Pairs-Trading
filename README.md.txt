# 📊 Adaptive Statistical Arbitrage using Kalman Filter

## 🧩 Overview

This project implements a **market-neutral pairs trading strategy** using a **dynamic hedge ratio** estimated via a **Kalman Filter**.

Unlike traditional approaches that assume a constant relationship between assets, this model adapts to **time-varying market conditions** using a **state-space framework**.

---

## 🧠 Motivation

Traditional pairs trading relies on a **static hedge ratio (OLS regression)**, which fails in dynamic markets where relationships between assets evolve over time.

This project addresses that limitation by:

* Modeling the hedge ratio as a **latent time-varying state**
* Using a **Kalman Filter** to update it sequentially
* Capturing short-term deviations while maintaining long-term equilibrium

---

## 📈 Strategy Overview

### 🔁 Pairs Trading

Pairs trading is a **statistical arbitrage strategy** that exploits temporary deviations between two related assets.

* Long undervalued asset
* Short overvalued asset
* Profit from **mean reversion of the spread**

---

### ⚖️ Hedge Ratio

The hedge ratio defines the relative position sizes:

spread_t = price1_t - β_t · price2_t

* Ensures **market neutrality**
* In this project, β_t is **time-varying**

---

### 🔗 Correlation vs Cointegration

| Concept       | Meaning                            |
| ------------- | ---------------------------------- |
| Correlation   | Short-term co-movement             |
| Cointegration | Long-term equilibrium relationship |

✔️ Cointegration is used to validate tradable pairs
✔️ Correlation is used for initial filtering

---

## 🧮 Methodology

### 1️⃣ Data Collection

* Historical price data using `yfinance`

### 2️⃣ Pair Selection

* Correlation filtering
* Cointegration testing (Engle-Granger)

### 3️⃣ State-Space Model

State Equation:
β_t = β_{t-1} + noise

Observation Equation:
price1_t = β_t · price2_t + α_t + noise

---

### 4️⃣ Kalman Filter

* Predict → Update cycle
* Estimates **dynamic hedge ratio (β_t)**
* Adapts to market changes

---

### 5️⃣ Signal Generation

* Compute spread
* Normalize using Z-score
* Trading signals:

| Condition      | Action       |
| -------------- | ------------ |
| Z > +threshold | Short spread |
| Z < -threshold | Long spread  |
| Z ≈ 0          | Exit         |

---

### 6️⃣ Backtesting

* Entry/exit logic
* PnL calculation
* Performance metrics

---

## 📊 Results

(Add your plots here)

* Spread vs time
* Z-score
* Entry/exit signals
* Equity curve

---

## 🔥 Key Features

* ✅ Dynamic hedge ratio using Kalman Filter
* ✅ State-space modeling approach
* ✅ Market-neutral strategy
* ✅ Mean reversion based trading
* ✅ Extendable to multi-pair portfolios

---

## 🛠️ Tech Stack

* Python
* NumPy / Pandas
* Matplotlib
* statsmodels
* pykalman
* yfinance

---

## ▶️ How to Run

```bash
git clone https://github.com/yourusername/adaptive-stat-arb-kalman.git
cd adaptive-stat-arb-kalman
pip install -r requirements.txt
python main.py
```

---

## 📂 Project Structure

adaptive-stat-arb-kalman/
│
├── notebooks/
│   └── kalman_stat_arb.ipynb
│
├── src/
├── README.md
├── requirements.txt

---

## 🚀 Future Improvements

* Multi-pair portfolio optimization
* Transaction cost modeling
* Dynamic noise covariance tuning (Q & R)
* Walk-forward validation
* Risk management enhancements

---

## 🧠 Key Takeaway

This project demonstrates how **state-space models and Kalman filtering** can be used to build **adaptive trading strategies** that outperform static methods in evolving markets.

---

## 📬 Contact

Feel free to reach out for discussions on:

* Quantitative finance
* Statistical arbitrage
* State-space modeling

---
