---
{}
---

# Miyamae Implementation Backlog

> Turn the existing Git-backed Grok control plane into a second domain: an independent AI-assisted Miyamae local information/community account.

# Miyamae Implementation Backlog

## Goal

Turn the existing Git-backed Grok control plane into a second domain: an independent AI-assisted Miyamae local information/community account.

Do not delete the existing AI Engineering Radar. Introduce domain isolation so both can coexist.

## P0 — repository/domain model

- [ ] Generalize hard-coded `ai_engineering` assumptions in schemas/tooling.
- [ ] Add `miyamae_local` interest/profile taxonomy.
- [ ] Add bot group `miyamae-community-media`.
- [ ] Add source registry validation for `config/miyamae-sources.yaml`.
- [ ] Add story candidate schema with state/risk/provenance/follow-up fields.
- [ ] Add correction/retraction linkage.
- [ ] Ensure audit log records discovery, verification, editorial decision, publish attempt and correction.

## P0 — agents

Create narrowly scoped agents rather than one omnipotent bot:

1. `miyamae-source-scout` — detect changes across approved sources.
2. `miyamae-resident-lead-intake` — normalize mentions/replies into leads; never assert truth.
3. `miyamae-evidence-verifier` — gather primary/corroborating evidence and contradictions.
4. `miyamae-relevance-judge` — Miyamae materiality + geography + duplicate/story clustering.
5. `miyamae-risk-editor` — R0-R3 classification and privacy/reputation checks.
6. `miyamae-post-writer` — Japanese X/Threads-native drafts with source/time/state.
7. `miyamae-community-host` — questions, polls, follow-ups, contributor acknowledgements.
8. `miyamae-correction-watcher` — watch published stories for changed/corrected source facts.
9. `miyamae-digest-editor` — morning/evening/weekend/week summaries.

No agent may convert a single resident/social claim directly into `CONFIRMED`.

## P0 — dry-run routines

- [ ] frequent source-change discovery
- [ ] event-driven urgent candidate pipeline
- [ ] 07:00 morning digest
- [ ] 18:00 daily digest
- [ ] Friday weekend guide
- [ ] Sunday weekly recap/upcoming deadlines
- [ ] published-story follow-up/correction watch
- [ ] resident lead review queue

All start with `externalWrite: deny` / dry-run artifacts.

## P1 — source research

For every discovery backlog family, document:

- canonical operator/authority
- exact endpoint/feed/page
- robots/terms/access constraints
- polling/event mechanism
- geographic filtering method
- timestamp semantics
- outage/failure behavior
- evidence strength
- expected duplicate relationships

Never fill a missing endpoint by guessing.

## P1 — community operations

- [ ] mention/reply ingestion
- [ ] consent-aware contributor credit
- [ ] neutral local-question generator
- [ ] anti-pile-on guard for businesses/private people
- [ ] moderation policy enforcement
- [ ] unanswered-question queue
- [ ] recurring contributor metrics without public ranking

## P1 — publishing adapters

Separate content truth from platform rendering:

```text
Story -> EditorialDecision -> CanonicalPost
                         -> XRenderer
                         -> ThreadsRenderer
```

X: urgency, brevity, source-first, threads for updates when needed.
Threads: conversational context and community questions, without inventing personal experience.

## P1 — evaluation before automation

Create a labeled dry-run corpus covering at least:

- 50 official benign notices/events
- 20 commercial opening/closure/change cases
- 20 transport/infrastructure cases
- 20 resident-submitted leads including false/ambiguous ones
- 10 accident/fire/public-safety cases
- 10 political/controversial cases
- 10 privacy/adversarial cases
- 10 correction/update chains

Measure false confirmation, missed primary sources, wrong geography, duplicate publication, unsafe privacy leakage, sensational wording and stale-event publication.

R0 auto-publishing must not be enabled merely because implementation is complete.

## P2 — account launch

- [ ] create/rename X/Threads identity
- [ ] bio explicitly says independent/non-official + AI-assisted
- [ ] pinned editorial policy / correction policy
- [ ] publish initial explainer
- [ ] register approved publishing credentials outside Git
- [ ] enable assisted publishing
- [ ] collect resident source suggestions

## P2 — automation gate

Only enable autonomous R0 after an observed dry-run/assisted period demonstrates acceptable precision and correction behavior. Keep R2/R3 gated.

## P3 — optional product layer

Only if social usage proves demand:

- searchable story archive
- neighborhood pages
- event calendar
- map
- source transparency page
- correction log
- resident submission form

A standalone forum is deliberately deferred. Community should first form in X/Threads replies, mentions, reposts and recurring conversations.
