📊 Fear & Greed Index vs Real Trading Performance  
### A Large-Scale Empirical Study on Market Sentiment and Executed Trades

---

## Author Information

| Field | Value |
|-------|-------|
| **Candidate Name** | Yash_Maheshwari |
| **Analysis Date** | 2026-01-11 |
| **Submission Type** | Data Science Assignment |

---

## 📁 Directory Structure
ds_Yash_Maheshwari/
│
├── 📓 notebook_1.ipynb # Main analysis notebook (Google Colab)
│
├── 📂 csv_files/ # All CSV data outputs
│ ├── merged_data.csv # Combined trader + sentiment data
│ ├── sentiment_statistics.csv # Performance statistics by sentiment
│ ├── trader_performance.csv # Individual trader metrics
│ ├── statistical_tests.csv # Statistical test results
│ └── analysis_summary.csv # Executive summary data
│
├── 📂 outputs/ # All visualizations
│ ├── eda_dashboard.png # Exploratory Data Analysis dashboard
│ ├── sentiment_analysis.png # Sentiment-performance analysis
│ ├── correlation_matrix.png # Variable correlation heatmap
| ├── trade_count_validation.png # Trade count
│ └── trading_patterns.png # Trading pattern visualizations
| 
│
├── 📄 ds_report.pdf # Final analysis report
│
└── 📄 README.md # This file

---

---

## 1. Motivation & Background

Market sentiment indicators such as the **Crypto Fear & Greed Index** are widely used by traders, analysts, and media outlets as a proxy for crowd psychology.  
The common belief is:

> *“Extreme fear creates buying opportunities, and extreme greed signals overbought markets.”*

While numerous studies analyze **price returns**, very few evaluate whether sentiment actually improves **real trading performance after execution**.

This project addresses that gap by answering a more difficult and practical question:

> **Does market sentiment meaningfully affect actual trader profitability, win rates, and risk outcomes once trades are executed?**

This study is **execution-aware**, **distribution-aware**, and **statistically rigorous**, focusing on *real PnL* rather than theoretical returns.

---

## 2. Research Objectives

The analysis is designed to answer five core questions:

1. Does trading during **Greed** outperform trading during **Fear**?
2. Is sentiment predictive of **individual trade outcomes**?
3. Does sentiment influence **risk-taking behavior** (trade size)?
4. Are there **time-based sentiment interactions** (hour/day effects)?
5. Are observed differences **tradeable edges or statistical artifacts**?

---

## 3. Dataset Overview

### 3.1 Fear & Greed Index Data

| Attribute | Description |
|---------|------------|
| Source | Crypto Fear & Greed Index |
| Frequency | Daily |
| Range | 0 (Extreme Fear) – 100 (Extreme Greed) |
| Period | 2018 – 2025 |
| Nature | Macro-level sentiment indicator |

**Sentiment Interpretation:**
- 0–25: Extreme Fear
- 25–50: Fear
- 50–75: Greed
- 75–100: Extreme Greed

---

### 3.2 Trading Execution Data

| Attribute | Value |
|---------|-------|
| Total Trades | 211,224 |
| Traders | 32 |
| Trading Pairs | 246 |
| Period | May 2023 – May 2025 |
| Asset Class | Cryptocurrency |
| Data Type | Real executed trades |

Each trade includes:
- Timestamp
- Trade size (USD)
- Realized PnL
- Direction
- Execution outcome

> **No rows were removed**, ensuring zero survivorship bias.

---

## 4. Data Engineering & Feature Construction

### 4.1 Sentiment Features

The Fear & Greed Index was transformed into:

- Categorical regimes (`fear`, `neutral`, `greed`)
- Binary indicators (`is_fear`, `is_greed`)
- Temporal features (day of week, hour, month)

This allows:
- Regime comparison
- Hypothesis testing
- Time-sentiment interaction analysis

---

### 4.2 Trading Features

Trades were enriched with:

- Outcome labels (`win`, `loss`, `breakeven`)
- Risk metrics (profit factor, risk-reward)
- Trade size normalization
- Time-of-day segmentation

A critical observation emerged early:

> **50.6% of all trades end at breakeven (PnL = 0).**

This heavily shapes all downstream analysis.

---

## 5. Trade Outcome Structure

### 5.1 Outcome Distribution

| Outcome | Percentage |
|------|------------|
| Breakeven | 50.6% |
| Winning | 41.1% |
| Losing | 8.3% |

Among **non-zero PnL trades**:
- **83% are winners**
- Losses are rare but larger in magnitude

This indicates a strategy characterized by:
- Aggressive downside control
- Breakeven exits
- Rare but meaningful losses
- Occasional large winners

This structure explains why **median PnL = 0** across all sentiment regimes.

---

## 6. Sentiment vs Performance Analysis

### 6.1 Aggregate Performance by Sentiment

| Metric | Fear | Neutral | Greed |
|------|------|--------|-------|
| Average PnL | $49.21 | $34.31 | **$54.35** |
| Median PnL | $0 | $0 | $0 |
| Win Rate | 40.8% | 39.7% | **42.0%** |
| Profit Factor | 4.33 | 4.32 | **4.69** |
| Risk-Reward | 0.80 | 0.92 | **0.998** |

**Key Observation:**  
Greed outperforms Fear consistently, but the magnitude is modest.

---

## 7. Distributional Analysis

Despite higher means during Greed:
- **Medians are identical**
- Distributions overlap heavily
- Differences occur almost entirely in the tails

This indicates:
- Typical trades behave the same
- Performance differences arise from **rare outlier trades**

---

## 8. Statistical Testing

### 8.1 Hypothesis Tests

| Test | Result |
|----|----|
| Mann-Whitney U | Statistically significant |
| Chi-Square (Outcome vs Sentiment) | Statistically significant |
| Pearson Correlation (PnL vs F&G) | Near zero |
| Cohen’s d | ~0.005 |
| Cramér’s V | 0.023 |

### 8.2 Interpretation

- Large sample size makes small effects statistically significant
- Effect sizes are **negligible**
- Sentiment explains **almost none of PnL variance**

> **Statistical significance does not imply a tradeable edge**

---

## 9. Trade Size & Risk Behavior

Trade size distributions under Fear and Greed:
- Are nearly identical
- Share the same mode and tail behavior
- Show no evidence of sentiment-based risk scaling

This implies:
- Traders do not size up during Greed
- Traders do not size down during Fear
- Risk management is systematic and sentiment-agnostic

---

## 10. Temporal & Pattern Analysis

### 10.1 Hour-of-Day Effects
- Market open hours perform best
- Late nights and weekends underperform

### 10.2 Friday Hour 12 Deep Dive

Initial heatmaps suggested exceptional performance.  
Deeper analysis showed:

| Metric | Value |
|------|------|
| Trades | 572 |
| Mean PnL | $37 |
| Median PnL | $0 |
| Std Dev | $508 |
| Outlier Impact | 70% of mean |

**Conclusion:**  
This “hot spot” is driven by a small number of extreme trades and is **not a reliable edge**.

---

## 11. Correlation Analysis

| Feature | Correlation with PnL |
|------|----------------------|
| Trade Size | 0.124 |
| Fear & Greed Index | 0.008 |
| Hour / Day | ~0 |

Even the strongest variable explains **<2% of variance**.

---

## 12. Key Findings Summary

| Insight | Conclusion |
|------|------------|
| Sentiment improves averages | Yes |
| Sentiment predicts trades | No |
| Risk behavior changes | No |
| Edges are consistent | Yes |
| Differences are outlier-driven | Yes |

---

## 13. Limitations

- Observational (not causal)
- Strategy-specific
- Crypto bull market overlap (2024–2025)
- No transaction cost modeling
- Daily sentiment applied to intraday trades

---

## 14. Practical Implications

- Sentiment is **context**, not a signal
- Strategy robustness matters more than regime timing
- Avoid over-fitting to sentiment-based filters
- Focus on execution quality and asymmetric payoffs

---

## 15. Final Conclusion

> **The Fear & Greed Index reflects market conditions but does not provide a reliable trading edge when evaluated on real executed trades.**

Profitability in this dataset is driven by **risk control, execution mechanics, and tail events**, not sentiment timing.

---

## 16. Reproducibility

- Fully reproducible notebook
- No external data leakage
- Deterministic transformations
- Transparent statistical tests

---

## 17. Disclaimer

This project is for educational and research purposes only.  
It does not constitute financial or investment advice.

## 🛠️ Setup Instructions

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scipy gdown
