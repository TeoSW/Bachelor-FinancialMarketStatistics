# Statistical Analysis of Walmart Stock, Ethereum, and the NASDAQ Composite Index

**Academia de Studii Economice din București**  
Faculty of Cybernetics, Statistics and Economic Informatics  
Course: Statistics of Financial Markets

**Authors:** Nistor Matei, Ofrim Gabriel, Constantin Teodor, Dumitrescu Andrei

---

## Overview

This project performs a comparative statistical analysis of three financial assets with distinct risk profiles:

- **Walmart Inc. (WMT)** — a large-cap retail stock listed on NYSE, representative of stable consumer markets
- **Ethereum (ETH-USD)** — a major cryptocurrency known for high volatility and speculative trading
- **NASDAQ Composite (^IXIC)** — a broad market index heavily weighted toward the technology sector

The goal is to evaluate return distributions, test market efficiency and fractal structure, identify extreme values, and model conditional volatility using quantitative methods in **Python**.

Data: daily adjusted closing prices from [Yahoo Finance](https://finance.yahoo.com).

---

## Project Structure

```
1. Introduction & asset definitions
2. Return distribution analysis
   2.1 Descriptive statistics
   2.2 Adjusted price evolution
   2.3 Daily log-returns
   2.4 Return quantiles
   2.5 Distribution shape & skewness
   2.6 Kolmogorov-Smirnov normality test
3. Extreme value identification
4. Pareto distribution fit (left tail)
5. Weak-form Efficient Market Hypothesis (EMH) testing
   5.1 Ljung-Box, Breusch-Godfrey, Wald-Wolfowitz tests
   5.2 Variance Ratio test
6. Fractal Market Hypothesis testing
   6.1 Hurst exponent estimation
7. GARCH(1,1) volatility modeling
8. Conclusions
```

---

## Methodology

### Log-Returns
Returns are computed as log-differences of closing prices:
```
r_t = ln(P_t) - ln(P_{t-1})
```

### Distribution Analysis
Descriptive statistics reveal that Ethereum has the highest volatility (σ = 0.046), followed by NASDAQ and Walmart. All three series exhibit negative skewness and excess kurtosis (leptokurtic distributions), indicating fat tails and frequent extreme values. The Kolmogorov-Smirnov test rejects normality for all three (p ≈ 0.000).

### Extreme Values
Ethereum recorded the most dramatic swings: a single-day loss of **–55.07%** (2020) and a gain of **+23.47%** (2017). NASDAQ's worst single-day drop was **–13.15%**, while Walmart's was **–18.42%** (1973).

### Pareto Distribution (Extreme Value Modeling)
A Generalized Pareto distribution is fitted to the left tail (bottom 5% of returns) for each asset. KS test p-values well above 0.05 confirm a good fit in all cases — the Pareto model significantly outperforms the normal distribution in capturing tail risk:

| Asset    | Shape param (b) | KS p-value |
|----------|----------------|------------|
| Walmart  | 4.39           | 0.6583     |
| Ethereum | 5.02           | 0.7290     |
| NASDAQ   | 6.82           | 0.7533     |

### Weak-Form EMH Testing
Three tests are applied to evaluate whether returns follow a random walk:

- **Ljung-Box** — rejects white noise for all three assets (p < 0.05), indicating serial autocorrelation
- **Breusch-Godfrey** — confirms correlated residuals
- **Wald-Wolfowitz** — confirms non-randomness for ETH and NASDAQ
- **Variance Ratio Test** — variance ratios deviate significantly from 1 under both homoskedastic and heteroskedastic assumptions, rejecting random walk behavior

All tests collectively indicate that **none of the three markets satisfy weak-form efficiency**.

### Fractal Market Hypothesis — Hurst Exponent
The Hurst exponent H measures long-term memory. H > 0.5 indicates persistence (trending behavior):

| Asset    | Hurst Exponent | Interpretation         |
|----------|---------------|------------------------|
| Walmart  | H = 0.6799    | Strong long-term memory|
| NASDAQ   | H = 0.6292    | Moderate persistence   |
| Ethereum | H = 0.5616    | Mild persistence       |

All values exceed 0.5, supporting the **Fractal Market Hypothesis**.

### GARCH(1,1) Volatility Modeling
Conditional heteroscedasticity is modeled using GARCH(1,1):

| Asset    | ω (omega)  | α (alpha) | β (beta) | α + β |
|----------|-----------|-----------|---------|-------|
| Walmart  | very small | 0.10      | 0.88    | 0.98  |
| Ethereum | larger     | 0.058     | 0.93    | 0.988 |
| NASDAQ   | ~3.24e-06  | 0.10      | 0.88    | 0.98  |

High α + β values across all assets confirm **strong volatility persistence**. Ethereum shows the most reactive and elevated conditional volatility, especially around the 2017–2018 bull run and the 2020 pandemic crash.

---

## Key Findings

| Analysis | Walmart | Ethereum | NASDAQ |
|---|---|---|---|
| Normality (KS test) | Rejected | Rejected | Rejected |
| Pareto tail fit | Good | Good | Good |
| Weak-form EMH | Rejected | Rejected | Rejected |
| Hurst exponent | 0.68 (persistent) | 0.56 (mild) | 0.63 (persistent) |
| GARCH α+β | 0.98 | 0.988 | 0.98 |

---

## Tools & Technologies

- **Language:** Python
- **Libraries:** `pandas`, `numpy`, `scipy`, `statsmodels`, `arch`, `matplotlib` (or similar)
- **Data source:** Yahoo Finance

---

## Data Sources

- [Walmart Inc. (WMT)](https://finance.yahoo.com/quote/WMT)
- [Ethereum (ETH-USD)](https://finance.yahoo.com/quote/ETH-USD)
- [NASDAQ Composite (^IXIC)](https://finance.yahoo.com/quote/%5EIXIC)

---

## Conclusions

The analysis reveals clear differences between the three asset classes. All return series deviate significantly from normality and exhibit serial dependence, contradicting the weak-form efficient market hypothesis. The Pareto distribution provides a more realistic model of extreme downside risk than the normal distribution for all three assets. Hurst exponents above 0.5 confirm the presence of long-term memory, consistent with the Fractal Market Hypothesis. GARCH(1,1) models capture persistent volatility clustering across all assets, with Ethereum showing the highest and most reactive conditional volatility — characteristic of speculative cryptocurrency markets.
