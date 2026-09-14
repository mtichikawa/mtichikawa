# Mike Ichikawa

### I build production AI agents, and the evaluations every build has to pass.

**Founding AI/ML Engineer** · Portland, OR · Remote · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com) · [mtichikawa.github.io](https://mtichikawa.github.io) · [Résumé](https://mtichikawa.github.io/resume.html)

MS Mathematics · BS Mechanical Engineering, UC Berkeley · three years of semiconductor physical design at Intel · eight years teaching college mathematics.

---

An AI agent that picks the wrong action doesn't crash. It does something adjacent, reports success, and looks exactly like one that got it right. Everything below is either a system with that property, or the measurement that catches it.

## A production AI agent for Microsoft 365

**[Live on the Microsoft Commercial Marketplace.](https://marketplace.microsoft.com/en-us/product/saas/microclaw.microclaw?tab=Overview)** Built solo — product, engineering, infrastructure and compliance. It lives in Microsoft Teams: you ask for something in plain language and it works out which actions to take across mail, calendar and files, checks what comes back, and keeps going until the job is done. It passed AppSource certification. It has no paying customers.

- **Tool selection.** 85 function-calling tools across 12 skill modules. Retrieval narrows them to a mean of 26 per request before the model sees anything — a **46% cut in input tokens**, measured with tiktoken against the provider's own prompt counts, not estimated. KNN selection scored **95.0% recall against a 92.7% embedding-only baseline, on 1,020 synthetic queries**.
- **Evaluation.** A hand-written suite scoring each answer on the facts it must contain and the facts it must never claim — a case asking for a *draft* forbids "email sent," because an agent that sends it and reports success has done the wrong thing and sounded finished doing it. Run against a baseline every build.
- **Failure handling.** Backoff honouring `Retry-After`; rate-limit waits bounded twice over, because an earlier version retried forever and left someone waiting hours for a reply; timeout compaction; a repeat guard that blocks a looping call and tells the model to try another approach rather than killing the turn; a hard cap at 35 tool calls.
- **Multi-tenant isolation.** Postgres row-level security with `FORCE` on 27 tables, fail-closed by construction — with no tenant context bound, a forgotten `WHERE` returns zero rows rather than someone else's data. A small, named set of cron and metering paths bypasses it deliberately, as a separate role.
- **RAG semantic memory**, natural-language automations fired by Graph webhooks, and model routing that escalates only when a turn gets complicated.

`TypeScript` · `Azure OpenAI` · `Microsoft Graph` · `Azure Postgres (RLS)` · `Azure Container Apps` · `Bicep` · `Docker → GHCR via GitHub Actions` · 404 tests

## [A multi-agent workflow engine](https://mtichikawa.github.io/workflow-engine/)

Plain-English requests become validated control-flow graphs of single-purpose agents. **[Interactive walkthrough →](https://mtichikawa.github.io/workflow-engine/)**

- A **static validator** with nine checks rejects unsound graphs before a single model call. It distinguishes what should block from what should only warn — a step whose one exit is conditional still runs, because a deliberate endpoint is legitimate, but you are told before the run rather than discovering a short result afterwards.
- **Specialists are a shared library**, one instance each, reused across workflows — enforced by object identity in a test, not by convention.
- A **learning loop** improved a weak specialist from 4/8 to 8/8 on an independent eval from six curated examples, with no fine-tuning.
- Speaks **MCP in both directions**: calls external MCP tools, and publishes its own workflows as MCP tools.

## What it takes to stump a coding agent

138 probe environments built to find a task a frontier coding agent could not solve.

- **The finding: complexity does not defeat comprehension.** 31 of 33 probes were solved, in one pass, with no iteration language in the logs. Adding defects or coupling them changes nothing. What worked was motion, opacity, and systematically misleading evidence.
- **The resulting task fails `claude-opus-5` at max reasoning and `gpt-5.6-sol` at xhigh, three trials each**, under the benchmark's own CI configuration. Oracle 1.000, no-op 0.000, and 22 of 22 repository static checks pass.
- **The measurement lied twice and both are in the record** — a backgrounded process that died in three seconds voided 71 runs while looking like results, and an over-precise verifier failed a correct answer on the sixteenth significant digit and manufactured a survivor that was not one.

---

Earlier work — forecasting, anomaly detection, NLP, cloud ETL, a Databricks lakehouse, streaming analytics, a paper-trading arc — sits in the repositories below. It was built in a different era of the job, before agentic coding, while I was learning the ropes.
