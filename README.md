# Mike Ichikawa

### I build production AI agents, and the evaluations that show whether they work.

**Founding AI/ML Engineer** · Portland, OR · Remote · [projects.ichikawa@gmail.com](mailto:projects.ichikawa@gmail.com) · [mtichikawa.github.io](https://mtichikawa.github.io) · [Résumé](https://mtichikawa.github.io/resume.html)

MS Mathematics, City College of New York · BS Mechanical Engineering, UC Berkeley · three years of semiconductor physical design at Intel · eight years teaching college mathematics.

---

An AI agent that picks the wrong action doesn't crash. It does something adjacent, reports success, and looks exactly like one that got it right. Everything below is either a system with that property, or the measurement that catches it.

## A production AI agent for Microsoft 365

**[Published on the Microsoft Commercial Marketplace](https://marketplace.microsoft.com/en-us/product/saas/microclaw.microclaw?tab=Overview)** and the Teams Store. I built it solo: product, engineering, infrastructure and compliance. It lives in Microsoft Teams: you ask for something in plain language and it works out which actions to take across mail, calendar and files, checks what comes back, and keeps going until the job is done. It passed Microsoft's Marketplace and Teams Store certifications. The hosted service is paused for now, and it has no paying customers.

- **Tool selection.** 85 function-calling tools across 12 skill modules. Sending all of them costs about 46,600 prompt tokens per message, so retrieval narrows the list first. On **362 blind-written test requests** (written by an agent that could see only the tool catalogue, scored once), the redesigned selector offered every tool a request needed **98.3%** of the time (95% CI 96.4–99.2), up from 87.3%. On a 142-case agent eval it called the right tools on 134 of 142 cases on average over three runs (range 132–136), with **63% fewer prompt tokens** per message than sending all 85. An earlier 95% figure is retired: it averaged per-tool recall for a version of the selector that production rarely used.
- **Evaluation.** A hand-written suite scoring each answer on the facts it must contain and the claims it must never make. A case asking for a *draft* fails if the answer says "email sent", however good the rest reads. 142 cases replayed offline with tool-call assertions and a held-out split, priced from measured tokens. Run on demand, not in CI.
- **Failure handling.** Backoff honouring `Retry-After`; rate-limit waits bounded twice over, because an earlier version retried forever and left a reply hanging for hours; timeout compaction; a repeat guard that blocks a looping call and tells the model to try another approach rather than killing the turn; a hard cap at 35 tool calls.
- **Multi-tenant isolation.** Postgres row-level security with `FORCE` on all 27 tenant tables, fail-closed: a tenant-scoped query with no tenant context throws instead of running, and a test fails if any tenant table lacks the policy. About 20 system paths (cron, retention, metering, webhook entry) bypass it deliberately, as a separate role, each listed with its reason.
- **RAG semantic memory**, natural-language automations fired by Graph change notifications or timers, and model routing: a small model by default, escalating to a large one only when a turn needs it (87% of eval messages never did).

`TypeScript` · `Azure OpenAI` · `Microsoft Graph` · `Azure Postgres (RLS)` · `Azure Container Apps` · `Bicep` · `Docker → GHCR via GitHub Actions` · `Vitest`

## [A multi-agent workflow engine](https://mtichikawa.github.io/workflow-engine/)

Plain-English requests become validated control-flow graphs of single-purpose agents. **[Interactive walkthrough →](https://mtichikawa.github.io/workflow-engine/)**

- A **learning loop** works out a team's unwritten rules from their corrections, with no fine-tuning. A clinic's message-routing protocol was never shown to it: on 150 blind-written test messages, accuracy rose from **59% to 97%** (95% CI 93–99%) as it learned from 291 corrections, cutting errors by 93%.
- **Triage that holds the medical line:** on 320 blind-written synthetic patient messages, it sent **all 160 medical ones to a person with no false alarms**. The same model without the engine's written policy raised false alarms on 17%.
- A **static validator** checks every workflow before any agent runs, and any step that acts outside the engine must sit behind a human approval gate. On 615 seeded faults from an independently written list it caught 26%; with new data-flow checks it now catches **93%** with no false alarms (the new checks were written after seeing that list).
- The composer **refuses to fake a capability**: on 120 blind-written requests, it flagged 41 of the 48 it couldn't serve as gaps instead of faking them.
- **Specialists are a shared library**: every workflow resolves the same registered instance by name.
- Speaks **MCP in both directions**: calls external MCP tools, and publishes every specialist as an MCP tool, plus one that composes and runs a workflow from a plain-English request.
- Every test set was written and labelled by Claude models blind to the code, then scored once. The engine is also Claude, so they could share blind spots.

## [What it takes to stump a coding agent](https://github.com/mtichikawa/klavis-tb3-submission)

138 probe environments built to find a task a frontier coding agent could not solve.

- **The finding: complexity does not defeat comprehension.** 31 of 33 probes were solved, in one pass, with no iteration language in the logs. Adding defects or coupling them changes nothing. What worked was motion, opacity, and systematically misleading evidence.
- **The resulting task fails `claude-opus-5` at max reasoning and `gpt-5.6-sol` at xhigh, three trials each**, under the benchmark's own CI configuration. Oracle 1.000, no-op 0.000, and 22 of 22 repository static checks pass.
- **My measurements went wrong twice, and both are in the record.** A background process that died in three seconds produced 71 runs that looked like results, and an over-strict verifier failed a correct answer on the sixteenth significant digit, which made a probe look like a survivor.

---

Earlier work sits in the repositories below: forecasting, anomaly detection, NLP, cloud ETL, a Databricks lakehouse, streaming analytics and a trading backtest system. I built it while I was learning the ropes.
