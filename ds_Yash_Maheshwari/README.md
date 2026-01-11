# 📊 Decoding Trader Behavior
## Bitcoin Trading Analysis

---

## Author Information

| Field | Value |
|-------|-------|
| **Candidate Name** | Yash_Maheshwari |
| **Analysis Date** | 2026-01-11 |
| **Submission Type** | Data Science Assignment |

---

## 📌 Executive Summary

This project analyzes **211,224 Bitcoin trades** executed by **32 Hyperliquid traders** between **May 2023 and May 2025**, evaluated against the **Bitcoin Fear & Greed Index** to understand sentiment-driven performance dynamics.

### Key Discoveries

- **Greed Outperforms Fear (Marginally)**  
  Greed periods produced **+$811K higher total profit**, **+10.4% higher per-trade PnL**, a **win-rate advantage of +1.25%**, and a **balanced 1.00 risk-reward ratio** compared to Fear’s **0.80**.

- **Extreme Greed is Optimal**  
  Contrary to contrarian assumptions, *Extreme Greed* delivered the **highest win rate (46.5%)**, **best profit factor (11.02)**, and **superior risk-reward (1.34)**.

- **Limited Predictive Power**  
  Sentiment explains **<0.01% of individual trade variance**. Despite strong statistical significance, the Fear & Greed Index **cannot predict single-trade outcomes**.

- **The Breakeven Edge**  
  **50.6% of trades closed at $0**, indicating systematic stop-loss-to-breakeven strategies. Among resolved trades, **83.2% were winners**, yielding a **5:1 win-loss ratio**.

- **Trader Heterogeneity**  
  **90.6% of traders were profitable**, with win rates spanning **26%–81%**. Profitability was driven by **risk-reward discipline**, not win frequency.

---

## 🧠 Research Objectives

- Compare trading performance across Fear and Greed regimes  
- Identify sentiment conditions that maximize profitability  
- Analyze trader behavior under different sentiment states  
- Discover time-sentiment-performance interaction patterns  

---

## 🗂️ Data Sources

### Bitcoin Fear & Greed Index
- 2,644 daily observations (2018–2025)
- Scale: 0–100
- Categories: Extreme Fear, Fear, Neutral, Greed, Extreme Greed

### Hyperliquid Trading Data
- 211,224 trades
- 32 traders, 246 trading pairs
- Fields include timestamps, trade size, direction, and realized PnL

---

## 🔬 Methodology

**Pipeline:**  
Data Collection → Preprocessing → Feature Engineering → EDA → Statistical Testing → Pattern Discovery → Synthesis

**Statistical Techniques:**
- Mann–Whitney U Test  
- Chi-Square Test  
- Pearson & Spearman Correlations  
- Cohen’s d, Cramér’s V  
- Bonferroni correction  

**Core Principles:**
- Effect size over p-values  
- Multi-scale analysis (trade → trader → regime)  
- Actionability focus  

---

## 📈 Key Analytical Insights

- Greed regimes generated **higher profits with lower position sizes**
- Fear regimes showed **emotional over-positioning with inferior returns**
- Extreme sentiment regimes outperformed moderate ones (U-shaped effect)
- Most apparent temporal anomalies were **outlier-driven artifacts**

---

## 👥 Trader-Level Findings

- 29 of 32 traders profitable (90.6%)
- Win rate ≠ profitability
- Best trader: 33.7% win rate, +$2.14M
- Worst loser: 38.3% win rate, −$167K
- 67.7% traders perform better in Greed
- 32.3% specialize in Fear (contrarian strategies)

---

## 🎯 Strategic Implications

- Do **not** use sentiment as a trade signal
- Use sentiment for **regime-level exposure control**
- Risk management dominates outcome consistency
- Extreme Greed is **not** an exit signal in this market

---

## ⚠️ Limitations

- Trader sample size limited (32)
- Bull-market biased window (2023–2025)
- Platform-specific behavior (Hyperliquid)
- Survivorship bias likely present

---

## 🚀 Future Scope

- Bear-market validation
- Cross-exchange replication
- Leverage-aware analysis
- Non-linear ML modeling
- Sentiment momentum vs sentiment level
- Multi-asset expansion

---

## 📁 Directory Structure
ds_Yash_Maheshwari/

│

├── 📓 Traders_behaviour_analysis_notebook.ipynb

│

├── 📂 csv_files/

│ ├── merged_data.csv

│ ├── sentiment_statistics.csv

│ ├── trader_performance.csv

│ ├── statistical_tests.csv

│ └── analysis_summary.csv

│

├── 📂 outputs/

│ ├── eda_dashboard.png

│ ├── sentiment_analysis.png

│ ├── correlation_matrix.png

│ ├── trade_count_validation.png

│ └── trading_patterns.png

│

├── 📄 ds_report.pdf

│

└── 📄 README.md


---

## ⚙️ Prerequisites & Libraries

### Environment
- Python ≥ 3.9
- Google Colab / Jupyter Notebook
- Git (optional)

### Core Libraries
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scipy  
- statsmodels  

### Statistical & ML
- scikit-learn  
- pingouin  

### Installation
```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn pingouin
