# Mike Ichikawa

**Data Scientist · ML Engineer · Data Engineer**

Portland, OR · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com)

---

## Background

BS Mechanical Engineering, MS Mathematics. Three years as a Physical Design Engineer at Intel (Ivy Bridge / 22nm). Nine years as Mathematics Faculty at Santa Rosa Junior College (statistics, calculus, linear algebra).

Now applying that foundation — quantitative rigor, systems thinking, production engineering experience — to data science and machine learning.

---

## Portfolio Projects

Sixteen public projects across a seven-month window, covering the full data science and engineering stack. Live interactive demos for Projects 2 and 5 at [mtichikawa.github.io](https://mtichikawa.github.io).

| # | Project | Stack | Focus |
|---|---------|-------|-------|
| — | M365 Enterprise Software *(private)* | TypeScript · Node.js · Azure OpenAI · Microsoft Graph · MSAL · Bot Framework | Full-stack enterprise software · Microsoft 365 ecosystem |
| 1 | [GitHub Trend Forecaster](https://github.com/mtichikawa/github-trend-forecaster) | Prophet · GitHub API · pandas | Time series forecasting · changepoint detection |
| 2 | [Multi-Armed Bandit A/B Testing](https://github.com/mtichikawa/bandit-ab-testing) | Thompson Sampling · UCB1 · Streamlit · Bayesian inference | Adaptive experimentation · explore/exploit |
| 3 | [LLM Data Analysis Assistant](https://github.com/mtichikawa/llm-data-assistant) | Anthropic API · hybrid routing · multi-turn | Applied LLM · rule-based fast path |
| 4 | [Bias Detection in LLMs](https://github.com/mtichikawa/llm-bias-detection) | ANOVA · Cohen's d · lexicon scoring | Statistical research methodology |
| 5 | [Real-Time Anomaly Detection](https://github.com/mtichikawa/anomaly-detection) | IsolationForest · LSTM · FastAPI · Docker · ensemble voting | Streaming ML · production packaging |
| 6 | [Financial NLP Parser](https://github.com/mtichikawa/financial-nlp) | SEC EDGAR · regex · sentiment lexicon | NLP · financial data extraction |
| 7 | [SQL Analytics Pipeline](https://github.com/mtichikawa/sql-analytics-pipeline) | PostgreSQL · SQLAlchemy · dbt-style transforms | Data engineering · layered transforms |
| 8 | [Dockerized ML API](https://github.com/mtichikawa/dockerized-ml-api) | Docker · FastAPI · Redis · Pydantic v2 · async | MLOps · REST inference · caching |
| 9 | [Cloud ETL Pipeline](https://github.com/mtichikawa/cloud-etl-pipeline) | AWS S3 · Lambda · DynamoDB · Parquet | Cloud infrastructure · data lake |

---

## Trading System Arc — Complete ✅

Five interconnected repos building an end-to-end paper trading system: live market data → chart generation → dual-path signal analysis (technical indicators + FinBERT sentiment) → backtesting → oversight dashboard. Entirely free to run — no paid APIs.

| # | Repo | Stack | Status |
|---|------|-------|--------|
| T1 | [crypto-data-pipeline](https://github.com/mtichikawa/crypto-data-pipeline) | ccxt · Kraken · PostgreSQL · SQLAlchemy | 🟢 Live |
| T2 | [trading-chart-generator](https://github.com/mtichikawa/trading-chart-generator) | mplfinance · PNG + JSON sidecars · 25/25 tests | 🟢 Live |
| T3 | [trading-signal-engine](https://github.com/mtichikawa/trading-signal-engine) | EMA · RSI · MACD · BB · FinBERT · 51/51 tests | 🟢 Live |
| T4 | [trading-backtester](https://github.com/mtichikawa/trading-backtester) | pandas · Sharpe · Sortino · drawdown · 72/72 tests | 🟢 Live |
| T5 | [trading-dashboard](https://github.com/mtichikawa/trading-dashboard) | Streamlit · Plotly · parameter review UI | 🟢 [Live demo](https://mtichikawa-trading.streamlit.app) |

---

## Now Building — databricks-lakehouse (Apr 13–16)

Medallion architecture (bronze → silver → gold) on Databricks Community Edition with Delta Lake. Reusing the NYC Airbnb dataset from sql-analytics-pipeline as the source, demonstrating how the same data flows through a modern lakehouse.

---

## Scheduled Upgrades (Apr–May 2026)

| Project | Upgrade | Target |
|---------|---------|--------|
| [Anomaly Detection](https://github.com/mtichikawa/anomaly-detection) | Dockerize + FastAPI REST endpoint | ✅ Mar 12 |
| [Dockerized ML API](https://github.com/mtichikawa/dockerized-ml-api) | Async endpoints + request queuing | ✅ Mar 19 |
| [ml-experiments](https://github.com/mtichikawa/ml-experiments) | C++ pybind11 rolling window extension | ✅ Apr 6 |
| [Bandit A/B Testing](https://github.com/mtichikawa/bandit-ab-testing) | Streamlit interactive simulator | ✅ Apr 9 |
| **databricks-lakehouse** | **Medallion architecture + Delta Lake (NEW BUILD)** | **Apr 13** |
| [crypto-data-pipeline](https://github.com/mtichikawa/crypto-data-pipeline) | T1→T2 integration | Apr 21 |
| [trading-chart-generator](https://github.com/mtichikawa/trading-chart-generator) | Live T1 feed | Apr 21 |
| [Bias Detection](https://github.com/mtichikawa/llm-bias-detection) | Second dataset + cross-model comparison | Apr 24 |
| [Cloud ETL Pipeline](https://github.com/mtichikawa/cloud-etl-pipeline) | Data quality validation layer | Apr 28 |
| [trading-signal-engine](https://github.com/mtichikawa/trading-signal-engine) | FinBERT threshold tuning | May 4 |
| [LLM Data Assistant](https://github.com/mtichikawa/llm-data-assistant) | Newer model + conversation history | May 7 |
| [trading-backtester](https://github.com/mtichikawa/trading-backtester) | Walk-forward validation + buy-and-hold benchmark | May 12 |
| [GitHub Trend Forecaster](https://github.com/mtichikawa/github-trend-forecaster) | PyTorch LSTM comparison model | May 14 |
| [SQL Analytics Pipeline](https://github.com/mtichikawa/sql-analytics-pipeline) | dbt transforms layer | May 21 |
| [trading-dashboard](https://github.com/mtichikawa/trading-dashboard) | WebSocket feed | May 26 |
| [Financial NLP](https://github.com/mtichikawa/financial-nlp) | PostgreSQL backend + Streamlit dashboard | May 28 |

---

## Roadmap — New Builds (Jun–Jul 2026)

| Project | Stack | Target |
|---------|-------|--------|
| streaming-analytics-pipeline | Redpanda · Spark Structured Streaming · Delta Lake · Streamlit | Jun 1 |
| recommendation-system | Collaborative filtering · content-based hybrid · NDCG/MAP eval | Jun 15 |
| mlops-pipeline | MLflow · DVC · model registry · automated retraining | Jun 29 |
| graph-analytics | NetworkX · Louvain community detection · PageRank · centrality | Jul 13 |

---

## Tinkering — [ml-experiments](https://github.com/mtichikawa/ml-experiments)

A running notebook sandbox — model comparisons, paper replications, dataset deep dives. Not portfolio pieces; just thinking out loud.

| Notebook | What I was exploring |
|----------|---------------------|
| [XGBoost vs LightGBM vs RF — Wine Quality](https://github.com/mtichikawa/ml-experiments/blob/main/comparisons/2026-03-02-xgboost-lgbm-rf-wine-quality.ipynb) | Accuracy, AUC, training time, feature importance comparison |
| [C++ Rolling Window via pybind11](https://github.com/mtichikawa/ml-experiments) | Performance comparison: C++ extension vs NumPy vs pandas rolling |

---

## Technical Skills

**Languages:** Python · SQL · C++ · R · TypeScript · Node.js

**ML / Statistics:** scikit-learn · Prophet · PyTorch · XGBoost · LightGBM · scipy · statsmodels · ANOVA · Bayesian inference · ensemble methods

**Data Engineering:** PostgreSQL · SQLAlchemy · dbt · Apache Parquet · Delta Lake · Databricks · pandas · NumPy

**Cloud / Infrastructure:** AWS (S3 · Lambda · DynamoDB · CloudWatch) · Azure OpenAI · Microsoft Graph API · MSAL · Bot Framework SDK · Docker · FastAPI · Redis · Pydantic · boto3

**LLM / NLP:** Anthropic API · Claude Code · HuggingFace · FinBERT · multi-turn conversation · tool use · prompt engineering · RAG · sentiment analysis · SEC EDGAR parsing

**Visualization:** Matplotlib · mplfinance · Streamlit · Plotly

**Trading Systems:** ccxt · Kraken API · OHLCV pipelines · technical indicators · FinBERT sentiment · pandas backtesting · signal parameter optimization

**Native Extensions:** C++ · pybind11 · CMake — Python/C++ interop for performance-critical paths

**Tools:** Git · GitHub Actions (CI) · Jupyter · Docker Compose · Vitest · ESLint · Prettier

---

## Contact

Open to data science, data engineering, ML engineering, and analytics roles.

[projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com) · [LinkedIn](https://www.linkedin.com/in/mike-ichikawa-9144a73b5/)
