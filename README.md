# 📈 Statistical Analysis of Walmart Stock, Ethereum, and the NASDAQ Composite Index

🏛️ **Academia de Studii Economice din București**  
📚 Faculty of Cybernetics, Statistics and Economic Informatics  
💹 Course: Statistics of Financial Markets

**👨‍🎓 Authors:** Nistor Matei, Ofrim Gabriel, Constantin Teodor, Dumitrescu Andrei

---

## 🌟 Overview

This project performs a comparative statistical analysis of three financial assets representing different risk profiles and market structures:

- 🛒 **Walmart Inc. (WMT)** — a large-cap retail stock representing mature consumer markets
- 🪙 **Ethereum (ETH-USD)** — a leading cryptocurrency characterized by high volatility and speculative trading
- 💻 **NASDAQ Composite (^IXIC)** — a technology-focused market index tracking thousands of publicly traded companies

The objective is to analyze return distributions, evaluate market efficiency, investigate long-term memory, identify extreme events, and model conditional volatility using advanced quantitative methods implemented in **Python**.

📊 **Data Source:** Yahoo Finance

---

# 📋 Project Structure

```text
1. Introduction & Asset Definitions
2. Return Distribution Analysis
   ├── Descriptive Statistics
   ├── Adjusted Price Evolution
   ├── Daily Log-Returns
   ├── Return Quantiles
   ├── Distribution Shape & Skewness
   └── Kolmogorov-Smirnov Test

3. Extreme Value Identification

4. Pareto Distribution Fit

5. Weak-Form EMH Testing
   ├── Ljung-Box Test
   ├── Breusch-Godfrey Test
   ├── Wald-Wolfowitz Test
   └── Variance Ratio Test

6. Fractal Market Hypothesis
   └── Hurst Exponent Estimation

7. GARCH(1,1) Volatility Modeling

8. Conclusions
```

---

# 🔬 Methodology

## 📈 Log-Returns

Returns are computed using logarithmic differences:

```math
r_t = \ln(P_t) - \ln(P_{t-1})
```

### Why Log Returns?

- ✅ Time additive
- ✅ Common in financial econometrics
- ✅ Better statistical properties than simple returns

---

# 📊 Distribution Analysis

## 📉 Descriptive Statistics

Analysis of daily returns revealed significant differences in volatility across assets.

### Volatility Ranking

🥇 Ethereum → Highest Volatility (σ = 0.046)

🥈 NASDAQ Composite

🥉 Walmart

### Distribution Characteristics

All three return series exhibit:

- ⬅️ Negative skewness
- 📈 Excess kurtosis
- ⚠️ Fat tails (Leptokurtic behavior)

These characteristics imply a higher probability of extreme market events compared to a normal distribution.

---

## 🧪 Kolmogorov-Smirnov Normality Test

### Results

| Asset | Normal Distribution |
|---------|---------|
| 🛒 Walmart | ❌ Rejected |
| 🪙 Ethereum | ❌ Rejected |
| 💻 NASDAQ | ❌ Rejected |

### Conclusion

All p-values are approximately zero, strongly rejecting the assumption of normally distributed returns.

---

# 🚨 Extreme Value Analysis

## 📉 Largest Single-Day Losses

| Asset | Maximum Loss |
|---------|---------|
| 🪙 Ethereum | **−55.07%** |
| 💻 NASDAQ | **−13.15%** |
| 🛒 Walmart | **−18.42%** |

---

## 📈 Largest Single-Day Gains

| Asset | Maximum Gain |
|---------|---------|
| 🪙 Ethereum | **+23.47%** |
| 💻 NASDAQ | Significant Positive Outliers |
| 🛒 Walmart | Moderate Positive Outliers |

### Key Insight

Ethereum experiences substantially larger price swings than traditional financial assets.

---

# 📉 Pareto Distribution & Tail Risk Modeling

To better model extreme downside events, a **Generalized Pareto Distribution (GPD)** was fitted to the bottom 5% of returns.

---

## 📊 Results

| Asset | Shape Parameter (b) | KS p-value |
|---------|---------|---------|
| 🛒 Walmart | 4.39 | 0.6583 |
| 🪙 Ethereum | 5.02 | 0.7290 |
| 💻 NASDAQ | 6.82 | 0.7533 |

---

## 🔍 Interpretation

### ✅ Good Fit

All KS test p-values exceed 0.05.

This indicates:

- Pareto adequately models extreme losses
- Tail behavior differs substantially from normality
- Extreme risk is underestimated by Gaussian assumptions

---

# 💹 Weak-Form Efficient Market Hypothesis (EMH)

The project evaluates whether prices follow a random walk, as predicted by weak-form market efficiency.

---

## 🧪 Ljung-Box Test

### Result

❌ Rejects white noise

All assets exhibit significant serial dependence.

---

## 🧪 Breusch-Godfrey Test

### Result

❌ Correlated residuals detected

Returns are not fully independent over time.

---

## 🧪 Wald-Wolfowitz Runs Test

### Result

❌ Non-random patterns identified

Particularly evident for:

- 🪙 Ethereum
- 💻 NASDAQ

---

## 🧪 Variance Ratio Test

### Result

❌ Random walk hypothesis rejected

Variance ratios differ significantly from 1 under both:

- Homoskedastic assumptions
- Heteroskedastic assumptions

---

## 📌 EMH Conclusion

All statistical tests consistently indicate that:

> ❌ Walmart, Ethereum, and NASDAQ do not satisfy weak-form market efficiency.

---

# 🌀 Fractal Market Hypothesis

## 📏 Hurst Exponent Analysis

The Hurst exponent measures long-term memory and persistence.

### Interpretation

| H Value | Meaning |
|----------|----------|
| H < 0.5 | Mean Reversion |
| H = 0.5 | Random Walk |
| H > 0.5 | Persistence / Trend Following |

---

## 📊 Results

| Asset | Hurst Exponent | Interpretation |
|---------|---------|---------|
| 🛒 Walmart | 0.6799 | Strong Persistence |
| 💻 NASDAQ | 0.6292 | Moderate Persistence |
| 🪙 Ethereum | 0.5616 | Mild Persistence |

---

## 🔍 Conclusion

All values exceed 0.5.

✅ Evidence supports the **Fractal Market Hypothesis (FMH)**.

Markets display long-term memory and trending behavior.

---

# 📈 GARCH(1,1) Volatility Modeling

To capture volatility clustering and conditional heteroskedasticity, a GARCH(1,1) model was estimated for each asset.

---

## 📊 Results

| Asset | ω | α | β | α + β |
|---------|---------|---------|---------|---------|
| 🛒 Walmart | Very Small | 0.10 | 0.88 | 0.98 |
| 🪙 Ethereum | Larger | 0.058 | 0.93 | 0.988 |
| 💻 NASDAQ | ~3.24e−06 | 0.10 | 0.88 | 0.98 |

---

## 🔍 Interpretation

### Volatility Persistence

All assets show:

```text
α + β ≈ 1
```

This indicates:

- 📈 Strong volatility clustering
- ⏳ Long-lasting volatility shocks
- 🔄 Persistent market uncertainty

---

## 🚨 Ethereum's Volatility

Ethereum demonstrates:

- Highest conditional volatility
- Strongest reaction to market events
- Pronounced volatility spikes

Notable periods:

- 🚀 2017–2018 Crypto Bull Market
- 🦠 2020 Pandemic Shock

---

# 📊 Summary of Findings

| Analysis | Walmart | Ethereum | NASDAQ |
|------------|------------|------------|------------|
| Normality (KS Test) | ❌ Rejected | ❌ Rejected | ❌ Rejected |
| Pareto Tail Fit | ✅ Good | ✅ Good | ✅ Good |
| Weak-Form EMH | ❌ Rejected | ❌ Rejected | ❌ Rejected |
| Hurst Exponent | 0.68 | 0.56 | 0.63 |
| Long-Term Memory | Strong | Mild | Moderate |
| GARCH α+β | 0.98 | 0.988 | 0.98 |

---

# 🛠️ Tools & Technologies

### 💻 Programming Language

- Python

### 📚 Libraries

- Pandas
- NumPy
- SciPy
- Statsmodels
- ARCH
- Matplotlib

### 📊 Data Source

- Yahoo Finance

---

# 📂 Financial Assets Analyzed

### 🛒 Walmart Inc.

Ticker:

```text
WMT
```

Sector:

- Retail
- Consumer Staples

---

### 🪙 Ethereum

Ticker:

```text
ETH-USD
```

Category:

- Cryptocurrency
- Digital Assets

---

### 💻 NASDAQ Composite

Ticker:

```text
^IXIC
```

Category:

- Broad Market Index
- Technology-Oriented Equity Market

---

# 🎯 Key Conclusions

### 📉 Non-Normal Markets

All return series significantly deviate from normality and exhibit fat-tailed distributions.

### 🚨 Extreme Risk Matters

The Pareto distribution captures downside risk more effectively than the normal distribution.

### ❌ Weak-Form EMH Rejected

All tests indicate serial dependence and predictable structures within returns.

### 🌀 Fractal Behavior Exists

Hurst exponents above 0.5 reveal persistent long-term memory and support the Fractal Market Hypothesis.

### 📈 Volatility Clustering Persists

GARCH(1,1) models confirm strong volatility persistence across all assets.

### 🪙 Ethereum Remains the Riskiest Asset

Ethereum exhibits:

- Highest volatility
- Largest extreme returns
- Strongest conditional volatility response

making it fundamentally different from both Walmart stock and the NASDAQ Composite.

---

⭐ **Main Contribution:** This study provides a comparative econometric analysis of equity, cryptocurrency, and market index behavior, demonstrating the presence of fat tails, volatility clustering, long-term memory, and weak-form market inefficiency across all three financial assets.
