# Mike Ichikawa

### I'm the engineer for a small manufacturer, building whatever software and AI the business needs.

**Lead AI Engineer** · Portland, OR · Remote · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com) · [mtichikawa.github.io](https://mtichikawa.github.io) · [Résumé](https://mtichikawa.github.io/resume.html)

MS Mathematics, City College of New York · BS Mechanical Engineering, UC Berkeley · three years of semiconductor physical design at Intel · eight years teaching college mathematics.

---

## Now: software and AI for a small manufacturer

I report to the owners, and I design, develop, deploy, secure and run all of the company's software. The platform comes first. It runs on Azure, with a delivery pipeline and a self-hosted AI assistant. The first app on it is a quoting app for the sales team, and production scheduling comes next. The client is confidential, so there's no code or name here.

- **The quoting app.** A customer's request for a quote arrives however they send it: emails with attachments, PDFs and drawings, spreadsheets, photos and scans, and notes from a phone call. The app reads all of it and returns product model numbers in seconds, with every value linked to the line it came from. The owners say finding that information can take a salesperson half a day.
- **Extraction separate from decisions.** The model only extracts and quotes its sources word for word. Every product decision is deterministic rules code built from the company's quoting guide, and where information is missing or conflicting, the app stops for a person.
- **Changing a rule.** An owner changes a quoting rule in one plain-English sentence. Before it takes effect, the app reruns every open and approved quote and 50,000 generated requests under the old and new rules, shows what would change, and a second person approves it.
- **The platform.** Each app gets staging and live environments, rollback, a managed identity with no stored secrets, and private networking, and no change merges or deploys until its tests pass.

`Python` · `Azure` · `GitHub Actions`

## Before this: a production AI agent for Microsoft 365

**[Published on the Microsoft Commercial Marketplace](https://marketplace.microsoft.com/en-us/product/saas/microclaw.microclaw?tab=Overview)** and the Teams Store. I built it solo: product, engineering, infrastructure and compliance. It lives in Microsoft Teams: you ask for something in plain language and it works out which actions to take across mail, calendar and files, checks what comes back, and keeps going until the job is done. It passed Microsoft's Marketplace certification and its Teams Store validation. **[Code and evals →](https://github.com/mtichikawa/m365-agent)**

- **Tool selection.** 87 function-calling tools across 12 skill modules. Sending all of them costs about 33,900 prompt tokens per message, so retrieval narrows the list first. On **362 blind-written test requests** (written by an agent that could see only the tool catalog, scored once), the redesigned selector offered every tool a request needed **98.1%** of the time (95% CI 96.1–99.1), up from 87.0%. On a 142-case agent eval it called the right tools on 134 of 142 cases on average over three runs (range 132–136), the same as sending every tool, with **49% fewer prompt tokens** per message. An earlier 95% figure is retired: it averaged per-tool recall for a version of the selector that production rarely used.
- **Evaluation.** A hand-written suite scoring each answer on the facts it must contain and the claims it must never make. A case asking for a *draft* fails if the answer says "email sent", however good the rest reads. 142 cases replayed offline with tool-call assertions and a held-out split, priced from measured tokens. Run on demand, not in CI.
- **Failure handling.** Backoff honoring `Retry-After`; rate-limit waits bounded twice over, because an earlier version retried forever and left a reply hanging for hours; timeout compaction; a repeat guard that blocks a looping call and tells the model to try another approach rather than killing the turn; a hard cap at 35 tool calls.
- **Multi-tenant isolation.** Postgres row-level security with `FORCE` on all 27 tenant tables, fail-closed: a tenant-scoped query with no tenant context throws instead of running, and a test fails if any tenant table lacks the policy. About 20 system paths (cron, retention, metering, webhook entry) bypass it deliberately, as a separate role, each listed with its reason.
- **RAG semantic memory**, natural-language automations fired by Graph change notifications or timers, and model routing: a small model by default, escalating to a large one only when a turn needs it (87% of eval messages never did).

`TypeScript` · `Azure OpenAI` · `Microsoft Graph` · `Azure Postgres (RLS)` · `Azure Container Apps` · `Bicep` · `Docker → GHCR via GitHub Actions` · `Vitest`

## Side projects

- **[A multi-agent workflow engine](https://mtichikawa.github.io/workflow-engine/).** A Python engine, built from scratch, that turns a plain-English request into a graph of small single-purpose agents. Every workflow is checked before it runs, and any step that acts outside the engine has to sit behind a person's approval. It learns a team's unwritten rules from their corrections, with no fine-tuning: on a clinic's routing rules it was never shown, accuracy on 150 synthetic test messages rose from 59% to 97%.
- **[What it takes to stump a coding agent](https://github.com/mtichikawa/klavis-tb3-submission).** I built 138 probe environments looking for one task a frontier coding agent couldn't solve. It solved 31 of 33. The two it couldn't solve both had misleading evidence, so I built the final task around that. On the benchmark's own harness, Claude Code on Claude Opus 5 and Codex on GPT-5.6 failed all six trials.

---

Earlier work sits in the repositories below: forecasting, anomaly detection, NLP, cloud ETL, a medallion lakehouse, streaming analytics and a trading backtest system. I built it while I was learning the ropes.
