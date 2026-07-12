# Michael Ichikawa

### I build AI agents and the multi-agent systems that coordinate them.

**AI / ML Engineer** · Portland, OR · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com) · [mtichikawa.github.io](https://mtichikawa.github.io) · [Resume](https://mtichikawa.github.io/resume.html)

MS Mathematics · BS Mechanical Engineering (UC Berkeley) · three years of semiconductor physical design at Intel · eight years teaching college math.

---

## Flagship work

Two builds, one identity: a **dedicated production agent** I shipped, and a **from-scratch multi-agent engine** that orchestrates many. One proves I can ship real production AI; the other proves I can build the coordination layer.

### 🟢 [Microclaw](https://microclaw.app) — a production AI agent for Microsoft 365

**[Live on the Microsoft Commercial Marketplace.](https://marketplace.microsoft.com/en-us/product/saas/microclaw.microclaw?tab=Overview)** Built solo, end to end. One AI agent that works across 12 Microsoft 365 services through 85 function-calling tools, inside a single Teams conversation. The headline isn't the commerce, it's the agent.

- **Agent loop** — iterative plan/act/observe over 85 tools (Azure OpenAI, function-calling) with multi-layer failure recovery.
- **KNN tool retrieval** — k=7, cosine-similarity fallback; **95.0% recall vs a 92.7% embedding-only baseline** (benchmarked at 1,020 examples), ~6 tools selected per request vs 18, ~33% fewer input tokens.
- **RAG semantic memory** — per-user persistent memory retrieved by cosine similarity; structured tool-call compression preserves entity references across turns.
- **Smart model router** — GPT-4o-mini default, escalates to GPT-4o on complexity; ~17× cheaper on simple queries.
- **In-house eval framework** — 107 hand-written tests with expected-facts scoring and A/B against a baseline bot; gated every release.
- **Natural-language automations** — plain-English rules parsed to structured Postgres rules, fired in real time via Microsoft Graph webhooks.
- **Multi-tenant** — Microsoft Entra delegated auth, Postgres row-level security, `tenantId` on every row.

`TypeScript` · `Azure OpenAI` · `Microsoft Graph` · `Teams Bot Framework SDK` · `Azure Postgres (RLS)` · `Bicep` · `Docker → GHCR` · `374 Vitest tests`. Transactable SaaS on the Marketplace (Standard + Self-Hosted).

### 🔷 [Multi-Agent Workflow Engine](https://mtichikawa.github.io/workflow-engine/) — built from scratch

**[Interactive writeup →](https://mtichikawa.github.io/workflow-engine/)** Modular AI specialists that each do one job with fixed input/output contracts, composed into validated control-flow graphs and run on a concurrency-safe single-writer board with human approval gates and a per-example learning loop.

- A **static validator** rejects unsound graphs before they run (loop-termination guards, contract compatibility, reachability).
- A **composer** writes new workflows from plain English and refuses to mark one runnable when a required specialist is missing — it doesn't fake capability.
- **Measured learning loop** — a deliberately weak specialist went **50% → 100%** on a held-out eval from six curated examples, no fine-tuning.

`Python` · `agent orchestration` · `contracts + recipes` · `static graph validation` · `few-shot retrieval` · `LLM-as-judge`. Engine source private; walkthrough on request.

---

## The broader body of work

Beyond the two flagships, a dozen self-directed public projects across the data and ML stack. Live interactive demos for #2 and #5 at [mtichikawa.github.io](https://mtichikawa.github.io).

| # | Project | Stack | Focus |
|---|---------|-------|-------|
| 1 | [GitHub Trend Forecaster](https://github.com/mtichikawa/github-trend-forecaster) | Prophet · GitHub API · pandas | Time-series forecasting · changepoint detection |
| 2 | [Multi-Armed Bandit A/B Testing](https://github.com/mtichikawa/bandit-ab-testing) | Thompson Sampling · UCB1 · Streamlit · Bayesian inference | Adaptive experimentation · explore/exploit |
| 3 | [LLM Data Analysis Assistant](https://github.com/mtichikawa/llm-data-assistant) | Anthropic API · hybrid routing · multi-turn | Applied LLM · rule-based fast path |
| 4 | [Bias Detection in LLMs](https://github.com/mtichikawa/llm-bias-detection) | ANOVA · Cohen's d · lexicon scoring | Statistical research methodology |
| 5 | [Real-Time Anomaly Detection](https://github.com/mtichikawa/anomaly-detection) | IsolationForest · LSTM · LightGBM · FastAPI · Docker · ensemble voting | Streaming ML · production packaging |
| 6 | [Financial NLP Parser](https://github.com/mtichikawa/financial-nlp) | SEC EDGAR · regex · sentiment lexicon | NLP · financial data extraction |
| 7 | [SQL Analytics Pipeline](https://github.com/mtichikawa/sql-analytics-pipeline) | PostgreSQL · SQLAlchemy · dbt-style transforms | Data engineering · layered transforms |
| 8 | [Dockerized ML API](https://github.com/mtichikawa/dockerized-ml-api) | Docker · FastAPI · Redis · Pydantic v2 · async | MLOps · REST inference · caching |
| 9 | [Cloud ETL Pipeline](https://github.com/mtichikawa/cloud-etl-pipeline) | AWS S3 · Lambda · DynamoDB · Parquet · in-pipeline DQ | Cloud infrastructure · data lake · data quality |
| 10 | [Databricks Lakehouse](https://github.com/mtichikawa/databricks-lakehouse) | Delta Lake · medallion · row-level quality gates | Lakehouse architecture · 10M-row NYC taxi dataset |
| 11 | [GCP RAG Pipeline](https://github.com/mtichikawa/gcp-rag-pipeline) | BigQuery Vector Search · Vertex AI Gemini · LangChain · LlamaIndex · Cloud Run | Production-shape RAG · SEC EDGAR corpus · 6-combo eval |
| 12 | [Streaming Analytics Pipeline](https://github.com/mtichikawa/streaming-analytics-pipeline) | Redpanda · Spark Structured Streaming · Delta Lake · Streamlit | Real-time streaming · 5m OHLCV · z-score anomaly · exactly-once recovery |

---

## Trading System Arc · complete

Five interconnected repos: live market data → chart generation → dual-path signals (technical indicators + FinBERT sentiment) → backtesting → an oversight dashboard, with losing trades feeding back to tune signal parameters. Free to run, no paid APIs. (An engineering showcase, not a claim of market edge.)

| # | Repo | Stack | Status |
|---|------|-------|--------|
| T1 | [crypto-data-pipeline](https://github.com/mtichikawa/crypto-data-pipeline) | ccxt · Kraken · PostgreSQL · SQLAlchemy | 🟢 Live |
| T2 | [trading-chart-generator](https://github.com/mtichikawa/trading-chart-generator) | mplfinance · PNG + JSON sidecars · 43/43 tests | 🟢 Live |
| T3 | [trading-signal-engine](https://github.com/mtichikawa/trading-signal-engine) | EMA · RSI · MACD · BB · FinBERT · 84/84 tests | 🟢 Live |
| T4 | [trading-backtester](https://github.com/mtichikawa/trading-backtester) | pandas · Sharpe · Sortino · drawdown · 72/72 tests | 🟢 Live |
| T5 | [trading-dashboard](https://github.com/mtichikawa/trading-dashboard) | Streamlit · Plotly · parameter review UI | 🟢 [Live demo](https://mtichikawa-trading.streamlit.app) |

---

[mtichikawa.github.io](https://mtichikawa.github.io) · [Resume](https://mtichikawa.github.io/resume.html) · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com)
