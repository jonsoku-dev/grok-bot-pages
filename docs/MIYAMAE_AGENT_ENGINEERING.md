---
{}
---

# Miyamae Agent Engineering Standard

> This document is the engineering contract for agentic behavior in the Miyamae newsroom. It is intentionally stricter than a prompt-style guide: prompts may evolve, but state transitions, safety gates, provenance, publication serialization and evaluation contracts must remain deterministic and testable.

# Miyamae Agent Engineering Standard

This document is the engineering contract for agentic behavior in the Miyamae newsroom. It is intentionally stricter than a prompt-style guide: prompts may evolve, but state transitions, safety gates, provenance, publication serialization and evaluation contracts must remain deterministic and testable.

## 1. Decision boundary

Use an agent only where semantic judgment is materially useful: discovery interpretation, relevance reasoning, evidence comparison, drafting, anomaly explanation, coverage-gap interpretation and escalation summaries.

Use deterministic code for anything that changes durable operational state or enforces a policy invariant:

- source scheduling, adaptive backoff, circuit state and cursors;
- community lifecycle and SLA timestamps;
- verification-quality lifecycle and measurement timestamps;
- follow-up lifecycle and correction deadlines;
- reserve freshness/utility eligibility;
- publication enqueue, idempotency, freshness preflight, locking and marking;
- browser task claiming/completion;
- metrics and audit ledgers;
- capability evidence and recovery classification.

An agent must never bypass a deterministic tool by writing the underlying SQLite table or workspace ledger directly.

## 2. Agent responsibility rule

Each Bot should have one primary semantic responsibility and one explicit output boundary. A Bot may request work from another responsibility, but it should not silently absorb that responsibility.

Examples:

- Source Scout discovers; Evidence Verifier decides evidentiary confidence.
- Local Pulse detects research triggers; it never upgrades factual confidence.
- Community Triage classifies and routes; it does not verify submitted claims itself.
- Follow-up Watcher compares changed evidence; Publication Arbiter owns final queue serialization.
- Reserve Curator maintains reusable verified utility; it cannot delay breaking verified utility.
- Coverage Auditor identifies blind spots; it cannot manufacture filler or lower verification thresholds.

## 3. Tool contract rule

Every state-mutating tool must provide:

1. a narrow command or function with explicit required inputs;
2. policy validation before mutation;
3. idempotency or duplicate protection where a retry is plausible;
4. fail-closed behavior for missing evidence, stale state or invalid transitions;
5. an auditable output describing what changed;
6. no credential/session material in logs or persisted state;
7. an import-safe pure-function surface for unit tests when policy calculations are involved.

Prompts should reference the command, not reproduce SQL or ask the model to emulate the state machine.

## 4. Handoff contract

A handoff is a typed work transfer, not a conversational suggestion. The sender must preserve provenance and state and must not pre-decide the receiver's responsibility.

Required handoff semantics:

- discovery -> verification: candidate, source provenance, observed timestamp, geography relevance, warnings;
- community -> verification: lead id, intent, public source pointers, no trust-based confidence upgrade;
- verification -> publication: verified story reference, R/U/C/I axes, freshness, source check time, human-review requirement;
- follow-up -> publication: original story/post reference, changed evidence, correction/retraction classification;
- coverage -> discovery: missing dimension and measurement window, never a prewritten conclusion.

## 5. Guardrails

Guardrails are enforced in deterministic policy/tool layers wherever possible.

Hard invariants:

- trends and Local Pulse are discovery/timing signals, never evidence;
- resident reports remain leads until independently verified;
- contributor history can only affect verification queue priority;
- R2/R3 require human review;
- C0 cannot become a factual READY publication;
- publication is globally serialized and idempotent;
- stale or non-revalidated publication candidates fail closed;
- correction and retraction work outrank ordinary reserve work;
- `FALSE_ALARM` is a distinct verified outcome and must not be used as a synonym for an unresolved or merely unconfirmed lead;
- recovery never bypasses authentication, CAPTCHA, approval or evidence retention;
- the shared Grok VM is an execution host, not a security boundary between Bots.

## 6. State ownership

Durable state has one authoritative owner:

| State | Authoritative mechanism |
| --- | --- |
| Source health / polling | `miyamae:vm:scheduler` + SQLite |
| Browser task ownership | browser task ledger/tool |
| Community lifecycle | `miyamae:vm:community` + `community_event` |
| Verification/quality instrumentation | `miyamae:vm:quality` + `story_quality_event` |
| Follow-up lifecycle | `miyamae:vm:followup` + `followup_watch` |
| Publication lifecycle | `miyamae:vm:publication` + queue/event ledger |
| Reserve inventory | `miyamae:reserve` + validated YAML items |
| Operational metrics | `miyamae:vm:metrics` + `metric_daily` |
| Recovery evidence | probe/recovery/evidence pipeline |

Agents may read authoritative state and propose semantic conclusions, but should mutate it only through the corresponding tool.

## 7. Quality instrumentation contract

Quality metrics must be derived from explicit lifecycle events rather than reconstructed from prose or model confidence.

The Evidence Verifier records `OBSERVED`, `VERIFICATION_STARTED`, then exactly one terminal verification outcome: `CONFIRMED`, `REJECTED`, or `FALSE_ALARM`. The original candidate observation timestamp must be preserved for `OBSERVED`; recording the verifier's current time instead would corrupt time-to-inform measurement.

Follow-up correction/retraction decisions create `CORRECTION_REQUIRED` instrumentation only for a story that has an authoritative `PUBLISHED` event. `CORRECTED` must follow a recorded correction requirement. Publication timestamps remain authoritative in `publication_event`; they are not duplicated as synthetic quality events.

Canonical metric semantics are exposed by `npm run miyamae:vm:quality -- definitions`:

- `verification_precision = CONFIRMED / (CONFIRMED + REJECTED + FALSE_ALARM)`;
- `false_alarm_rate = FALSE_ALARM / resolved verification outcomes`;
- `median_time_to_inform_minutes = median(first publication - first observation)` for first-published stories in the measurement day;
- `correction_rate = stories receiving CORRECTION_REQUIRED that day / stories published on or before that day`;
- `median_correction_latency_minutes = median(CORRECTED - latest preceding CORRECTION_REQUIRED)` for completed corrections that day.

No denominator means `UNAVAILABLE`, not zero. Missing timestamps or unmatched lifecycle events must be surfaced as degraded/unavailable instrumentation, never silently discarded as healthy performance.

## 8. Evaluation strategy

Evaluate workflows at three levels.

### Deterministic contract tests

Test policy calculations and state transitions without a model:

- adaptive polling bounds/backoff;
- Local Pulse same-window baseline math;
- publication stale/revalidation/review preflight;
- community SLA lookup and valid verifier routing;
- verification-quality transition validity and metric math;
- follow-up correction deadlines and overdue behavior;
- reserve freshness/utility gates;
- idempotency and duplicate handling.

### Agent workflow evals

Use fixed fixtures to score whether the agent:

- calls the correct tool instead of mutating state directly;
- hands off to the correct responsibility;
- preserves provenance and uncertainty;
- refuses confidence upgrades from trend/social/trust signals;
- records verification lifecycle through the quality tool;
- escalates R2/R3 and ambiguous correction cases;
- produces no external write before Publication Arbiter approval.

### Production observability

Track tool calls and resulting state transitions, not only final prose. Operational metrics should distinguish `0` from `UNAVAILABLE`; missing instrumentation must never look like healthy performance.

## 9. Coverage-audit prerequisite

Coverage analysis must operate on structured publication metadata, not re-infer dimensions from post text. Before making `coverage_recall_proxy` authoritative, the publication contract must persist at least:

- neighborhoods/area dimensions;
- category/topic;
- audience tags;
- source classes;
- publication timestamp and story id.

Until those fields are retained in the publication ledger, Coverage Auditor output is diagnostic only and the metric must remain `UNAVAILABLE` rather than fabricating precision.

## 10. No-CI validation model

Miyamae agent and runtime acceptance is local and VM-based. CI, required GitHub status checks, and remote runners are intentionally not part of the correctness model.

- `npm run verify:runtime` is the deterministic acceptance profile for Bot responsibilities, typed handoffs, runtime tools, policy, schemas, and agent workflow eval fixtures.
- `npm run verify:local` is the complete repository profile, including all tests and the documentation build.
- `npm run verify:vm` adds the live Grok VM self-test and probe after bootstrap.
- A non-zero exit rejects the change.
- A profile that was not executed is `UNVERIFIED`; static inspection or model confidence cannot turn it into a pass.
- Acceptance evidence must retain the exact command, exit status, environment, timestamp, and source commit SHA, plus relevant probe, plan, snapshot, and audit references.
- Agents must not create, re-enable, retry, poll, or reason from GitHub Actions validation workflows.
- Documentation/report workflows may automate delivery, but they never own correctness or approval.

The canonical operator procedure is `docs/LOCAL_VALIDATION.md`.

## 11. Change checklist

Any new Bot, Routine or tool must answer:

- What semantic judgment requires an agent?
- What durable state changes?
- Which deterministic tool owns that state?
- What is the retry/idempotency behavior?
- What is the fail-closed path?
- Which other Bot receives a typed handoff?
- Which hard guardrail applies?
- What unit test and agent workflow eval prove the behavior?
- Which local/VM validation profile covers the change?
- What production metric can detect regression?

If these questions cannot be answered, the feature is not ready to enter the autonomous newsroom workflow.
