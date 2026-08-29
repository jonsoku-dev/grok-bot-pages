---
{}
---

# Miyamae Local Media v1 Release Gates

> Scope is frozen. New ideas are POST_V1 unless they repair a blocker below.

# Miyamae Local Media v1 Release Gates

Scope is frozen. New ideas are POST_V1 unless they repair a blocker below.

## Definition of Done
Repository v1 is DONE when G0-G8 repository gates are PASS with P0 blockers=0. Capabilities that can only be proven inside the Grok Bot app/VM are allowed to remain `PENDING_RUNTIME_VERIFICATION`; they must never be represented as PASS without evidence.

| Gate | Requirement | Evidence |
|---|---|---|
| G0 Constitution | editorial/privacy/R-U-C-I/correction policy fixed | policy + schemas |
| G1 Sources | free-first official/API/RSS/web/browser sources, health/cursor/fallback | source registry/runtime |
| G2 Story Pipeline | candidate→LEAD→VERIFYING→CONFIRMED/REJECTED/DISPUTED; claims≠facts | story lifecycle tests |
| G3 Intelligence | Local Pulse/trend/reserve/coverage are typed; trend is not evidence | runtime contracts |
| G4 Community | intent triage, SLA, verifier routing, correction intake | community ledger/evals |
| G5 Publication | one queue, freshness, review, collision, idempotency, correction | publication ledger/tests |
| G6 Grok Handoff | bootstrap/runbook/capability experiments prepared | Grok docs/experiments |
| G7 Acceptance | deterministic tests + workflow evals + metrics + fail-closed validators | `npm run verify:runtime` |
| G8 Operational Handoff | local/VM validation and recovery procedure documented | operator docs |
| G9 Freeze | P0=0, known limitations recorded, post-v1 work moved out of scope | this document + backlog |

## Numeric acceptance thresholds
- P0 blockers: 0
- critical deterministic workflow contracts: 100%
- safety fixture pass rate: 100%
- normal scenario fixture pass rate: >=95%
- duplicate publication fixture pass rate: 100%
- R2/R3 review bypass: 0
- trend/Local Pulse evidence upgrades: 0
- correction/retraction lifecycle fixtures: 100%
- factual publication without provenance: 0

## Four-round closure
1. Pipeline Closure — no new product features.
2. Acceptance/Eval — scenario fixtures and blocker repair only.
3. Grok Operational Handoff — runtime-only checks and bootstrap instructions only.
4. Release Audit/Freeze — classify remaining findings as BLOCKER or POST_V1.

## Truthfulness rule
`PASS` requires executed evidence. Static inspection is `UNVERIFIED`. Grok-only functionality is `PENDING_RUNTIME_VERIFICATION` until executed in Grok. No percentage may be reported as 100% while a required repository gate is unexecuted or failing.
