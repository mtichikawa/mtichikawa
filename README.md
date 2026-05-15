# Mike Ichikawa

**Data Scientist · ML Engineer · Data Engineer**

Portland, OR · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com)

---

## Founded · Microclaw

### [Microclaw](https://microclaw.app): production AI agent for Microsoft 365

Submitted to the Microsoft Commercial Marketplace. A retrieval-augmented AI agent that lives inside Microsoft Teams and operates across Microsoft 365 (email, calendar, tasks, files, notes, channels) through a single conversation. Built solo end-to-end. **The headline isn't the commerce; it's the agent.**

**KNN tool selection.** k=7, 0.80 confidence threshold, cosine-similarity fallback over 1,020 synthetic training examples (using `text-embedding-3-small`). 95.0% recall vs 92.7% embedding-only baseline. 6.4 tools selected per request vs 18. ~60% input-token reduction.

**Semantic memory retrieval (RAG).** Per-user persistent memory with cosine-similarity retrieval. Conversation-history compression preserves entity references through structured tool-call summaries.

**Smart model router.** GPT-4o-mini default, escalates to GPT-4o on complexity signals or mid-conversation tool-call escalation. **17× cheaper for simple queries** vs always-on 4o.

**In-house eval framework.** 75 tests with expected-facts scoring, accuracy and quality grading, A/B comparison against a baseline bot. 29 iterative testing rounds before submission.

**Natural-language automations.** Users describe IFTTT-style rules in plain English; the agent parses intent into structured rules in Postgres, fired in real-time via Microsoft Graph change-notification webhooks.

**Multi-tenant SaaS.** Microsoft Entra delegated auth, per-tenant database isolation (tenantId on every row), two-layer permission system (Microsoft org-level plus per-user app-level toggles).

**Stack:** TypeScript · Node.js · Azure OpenAI (`gpt-4o`, `gpt-4o-mini`, `text-embedding-3-small`) · Microsoft Graph (85 tools across 12 M365 services) · Teams Bot Framework SDK · MSAL · Azure Database for PostgreSQL · `node-postgres` · Bicep (IaC) · Docker (multi-stage) · GitHub Actions → GHCR · Vitest (290 unit tests) · KNN retrieval · cosine similarity · cron-parser

**Marketplace integration:** Standard + Self-Hosted offerings · Fulfillment API v2 + Marketplace Metering Service · 8-tier bracket pricing (Solo through Team-100) · $25 per seat · 1,500 pooled messages per seat · per-message metered overage · Microsoft as merchant of record

Built solo end-to-end: product, engineering, Oregon LLC, EIN, USPTO trademark, Microsoft Partner Center onboarding (D&B DUNS), brand identity, three product videos, and go-to-market.

---

## Portfolio Projects

Sixteen public projects built over the past eighteen months: ten portfolio projects below, the five-repo trading arc that follows, and the [ml-experiments](https://github.com/mtichikawa/ml-experiments) sandbox. Live interactive demos for Projects 2 and 5 at [mtichikawa.github.io](https://mtichikawa.github.io).

| # | Project | Stack | Focus |
|---|---------|-------|-------|
| 1 | [GitHub Trend Forecaster](https://github.com/mtichikawa/github-trend-forecaster) | Prophet · GitHub API · pandas | Time series forecasting · changepoint detection |
| 2 | [Multi-Armed Bandit A/B Testing](https://github.com/mtichikawa/bandit-ab-testing) | Thompson Sampling · UCB1 · Streamlit · Bayesian inference | Adaptive experimentation · explore/exploit |
| 3 | [LLM Data Analysis Assistant](https://github.com/mtichikawa/llm-data-assistant) | Anthropic API · hybrid routing · multi-turn | Applied LLM · rule-based fast path |
| 4 | [Bias Detection in LLMs](https://github.com/mtichikawa/llm-bias-detection) | ANOVA · Cohen's d · lexicon scoring | Statistical research methodology |
| 5 | [Real-Time Anomaly Detection](https://github.com/mtichikawa/anomaly-detection) | IsolationForest · LSTM · LightGBM · FastAPI · Docker · ensemble voting | Streaming ML · production packaging |
| 6 | [Financial NLP Parser](https://github.com/mtichikawa/financial-nlp) | SEC EDGAR · regex · sentiment lexicon | NLP · financial data extraction |
| 7 | [SQL Analytics Pipeline](https://github.com/mtichikawa/sql-analytics-pipeline) | PostgreSQL · SQLAlchemy · dbt-style transforms | Data engineering · layered transforms |
| 8 | [Dockerized ML API](https://github.com/mtichikawa/dockerized-ml-api) | Docker · FastAPI · Redis · Pydantic v2 · async | MLOps · REST inference · caching |
| 9 | [Cloud ETL Pipeline](https://github.com/mtichikawa/cloud-etl-pipeline) | AWS S3 · Lambda · DynamoDB · Parquet · in-pipeline DQ layer | Cloud infrastructure · data lake · data quality |
| 10 | [Databricks Lakehouse](https://github.com/mtichikawa/databricks-lakehouse) | Delta Lake · medallion architecture · pandas · row-level data quality gates | Lakehouse architecture · 10M-row NYC taxi dataset |

---

## Trading System Arc · Complete ✅

Five interconnected repos building an end-to-end paper trading system: live market data, chart generation, dual-path signal analysis (technical indicators + FinBERT sentiment), backtesting, and an oversight dashboard. Entirely free to run, no paid APIs.

| # | Repo | Stack | Status |
|---|------|-------|--------|
| T1 | [crypto-data-pipeline](https://github.com/mtichikawa/crypto-data-pipeline) | ccxt · Kraken · PostgreSQL · SQLAlchemy | 🟢 Live |
| T2 | [trading-chart-generator](https://github.com/mtichikawa/trading-chart-generator) | mplfinance · PNG + JSON sidecars · 43/43 tests | 🟢 Live |
| T3 | [trading-signal-engine](https://github.com/mtichikawa/trading-signal-engine) | EMA · RSI · MACD · BB · FinBERT · 51/51 tests | 🟢 Live |
| T4 | [trading-backtester](https://github.com/mtichikawa/trading-backtester) | pandas · Sharpe · Sortino · drawdown · 72/72 tests | 🟢 Live |
| T5 | [trading-dashboard](https://github.com/mtichikawa/trading-dashboard) | Streamlit · Plotly · parameter review UI | 🟢 [Live demo](https://mtichikawa-trading.streamlit.app) |

---

## Most Recent Ship · [bandit-ab-testing](https://github.com/mtichikawa/bandit-ab-testing) smoke tests + CI (May 1)

Added 19 smoke tests parametrized across all three algorithms (Thompson Sampling, UCB1, Epsilon-Greedy) covering construction, arm selection, update + best-arm, end-to-end simulation, seed reproducibility, and high-rate-arm-wins sanity. Added the GitHub Actions CI workflow. Closes the test-coverage gap left by the Apr 9 Streamlit upgrade.

---

## Recent and Scheduled Upgrades

| Project | Upgrade | Target |
|---------|---------|--------|
| [Anomaly Detection](https://github.com/mtichikawa/anomaly-detection) | Dockerize + FastAPI REST endpoint | ✅ Mar 12 |
| [Dockerized ML API](https://github.com/mtichikawa/dockerized-ml-api) | Async endpoints + request queuing | ✅ Mar 19 |
| [ml-experiments](https://github.com/mtichikawa/ml-experiments) | C++ pybind11 rolling window extension | ✅ Apr 6 |
| [Bandit A/B Testing](https://github.com/mtichikawa/bandit-ab-testing) | Streamlit interactive simulator | ✅ Apr 9 |
| [databricks-lakehouse](https://github.com/mtichikawa/databricks-lakehouse) | Medallion architecture + Delta Lake (NEW BUILD) | ✅ Apr 16 |
| [crypto-data-pipeline](https://github.com/mtichikawa/crypto-data-pipeline) | T1→T2 integration | ✅ Apr 22 |
| [trading-chart-generator](https://github.com/mtichikawa/trading-chart-generator) | Live T1 feed | ✅ Apr 23 |
| [Bias Detection](https://github.com/mtichikawa/llm-bias-detection) | Second dataset + cross-model comparison | ✅ Apr 25 |
| [Cloud ETL Pipeline](https://github.com/mtichikawa/cloud-etl-pipeline) | In-pipeline data quality layer + Lambda quarantine cross-check | ✅ Apr 28 |
| [Anomaly Detection](https://github.com/mtichikawa/anomaly-detection) | LightGBM as fourth ensemble detector (supervised) | ✅ Apr 30 |
| [Bandit A/B Testing](https://github.com/mtichikawa/bandit-ab-testing) | Smoke tests + GitHub Actions CI | ✅ May 1 |
| [trading-signal-engine](https://github.com/mtichikawa/trading-signal-engine) | FinBERT threshold tuning | ✅ May 4 |
| [LLM Data Assistant](https://github.com/mtichikawa/llm-data-assistant) | Newer model + conversation history | ✅ May 7 |
| [trading-backtester](https://github.com/mtichikawa/trading-backtester) | Walk-forward validation + buy-and-hold benchmark | ✅ May 12 |
| [GitHub Trend Forecaster](https://github.com/mtichikawa/github-trend-forecaster) | PyTorch LSTM comparison model | May 14 |
| [SQL Analytics Pipeline](https://github.com/mtichikawa/sql-analytics-pipeline) | dbt transforms layer | May 21 |
| [trading-dashboard](https://github.com/mtichikawa/trading-dashboard) | WebSocket feed | May 26 |
| [Financial NLP](https://github.com/mtichikawa/financial-nlp) | PostgreSQL backend + Streamlit dashboard | May 28 |

---

## Roadmap · New Builds (Jun-Jul 2026)

| Project | Stack | Target |
|---------|-------|--------|
| streaming-analytics-pipeline | Redpanda · Spark Structured Streaming · Delta Lake · Streamlit | Jun 1 |
| recommendation-system | Collaborative filtering · content-based hybrid · NDCG/MAP eval | Jun 15 |
| mlops-pipeline | MLflow · DVC · model registry · automated retraining | Jun 29 |
| graph-analytics | NetworkX · Louvain community detection · PageRank · centrality | Jul 13 |

---

## Tinkering · [ml-experiments](https://github.com/mtichikawa/ml-experiments)

A running notebook sandbox of model comparisons, paper replications, and dataset explorations. Not portfolio pieces; just thinking out loud.

| Notebook | What I was exploring |
|----------|---------------------|
| [XGBoost vs LightGBM vs RF, Wine Quality](https://github.com/mtichikawa/ml-experiments/blob/main/comparisons/2026-03-02-xgboost-lgbm-rf-wine-quality.ipynb) | Accuracy, AUC, training time, feature importance comparison |
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

**Native Extensions:** C++ · pybind11 · CMake · Python/C++ interop for performance-critical paths

**Tools:** Git · GitHub Actions (CI) · Jupyter · Docker Compose · Vitest · ESLint · Prettier

---

## Background

BS Mechanical Engineering (UC Berkeley), then three years as a Physical Design Engineer at Intel on Ivy Bridge (22nm). MS Mathematics (CCNY), then nine years as Mathematics Faculty at Santa Rosa Junior College, teaching algebra through calculus III, linear algebra, differential equations, and statistics.

---

## Contact

Talking with teams about data science, ML engineering, data engineering, and AI engineering roles.

[projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com) · [LinkedIn](https://www.linkedin.com/in/mike-ichikawa-9144a73b5/)
