---
{}
---

# Architecture

> ```text
GitHub private repository
  desired state + canonical knowledge
            |
            +--> deterministic local-host executor / SHA-bound receipts
            |
            +--> botctl plan/export
            |
            +--> human or computer-use apply
                         |
                         v
                    Grok runtime
                         |
                         v
                  runtime snapshot
```

# Architecture

## Control plane vs runtime

```text
GitHub private repository
  desired state + canonical knowledge
            |
            +--> deterministic local-host executor / SHA-bound receipts
            |
            +--> botctl plan/export
            |
            +--> human or computer-use apply
                         |
                         v
                    Grok runtime
                         |
                         v
                  runtime snapshot
```

GitHub is authoritative. Runtime snapshots are observations only.

## Classification axes

### Kind
`scout | verifier | evaluator | reviewer | synthesizer | maintainer | publisher | notifier`

### Trigger
- `on_demand`: explicit human invocation
- `scheduled`: time-based recurring execution
- `event_driven`: narrow external event trigger
- `hybrid`: scheduled/event execution plus manual invocation

### Direction
`ingest | process | persist | publish`

### Execution
- `deterministic`: no semantic judgment required; prefer scripts/actions
- `agentic`: reasoning, synthesis, classification, or contextual adaptation required

### Scope
`personal | company | shared_template`

## Trigger guidance

Use `on_demand` for architecture reviews, security reviews, technology comparisons, deep dives, and experiment design.

Use `scheduled` when time itself creates useful new input: daily signals, weekly releases, monthly landscapes.

Use `event_driven` only for narrow high-signal events. Avoid broad listeners such as every Slack message.

Use `hybrid` for research/delivery functions that are valuable both periodically and interactively.

## Artifact roles

The repository keeps facts, reader output, and execution proof in different roots.

```text
intelligence/signals/**  factual_sot
publications/pending/**  reader_facing_derivative pending exact-content approval
reports/**               reader_facing_derivative published output
docs/**, runtime/**,
audit/**                 execution_evidence
```

Execution evidence can prove that a Bot ran or a delivery occurred. It cannot substitute for a
source-bound factual record. A report references record paths; it does not become the record.

## Simple active topology

The user-facing runtime has two Groups and ten Bots. Small source variants and maintenance stages are internal tasks, not separate Bots.

```text
AI Engineering Radar (4)
  Open Signal Scout -> Intelligence Editor -> Knowledge Publisher
                                          -> Publication Verifier

Miyamae Community Media (6)
  Scout -> Evidence Verifier -> Community Editor -> Publisher
                         Runtime Keeper -> Analyst
```

Use one Routine for each complete scheduled outcome. A new Bot or Routine requires a measured permission, reliability, or independent-verification boundary that cannot fit an existing owner.

## AI Engineering Radar architecture

One bounded group owns the complete pipeline.

```text
External sources -> Open Signal Scout -> Intelligence Editor
                                              |
                                              v
                                     Knowledge Publisher
                              factual records + approved documents
                                      |
                       exact hash + target approval
                                      |
                                      v
                          reports/** -> Docusaurus
                                      |
                                      v
                         Blog Publication Verifier
```

Knowledge Publisher uses policy-separated record and document modes so their approval rules stay distinct.
Publication Verifier remains read-only and independently checks the live article, source links, record IDs, and LLM outputs.

The daily public path is policy-authorized automation: one complete public-only `VERIFIED` record
is enough for GitHub SoT Writer to persist through the connected GitHub plugin. The operator-owned
local-host executor creates a missing report with `EMPTY` sections for absent regions, validates it,
commits it, and deploys the public Docusaurus build from an isolated temporary clone. It records a
`local-execution-receipt/v1` bound to the exact source subject SHA and command set. Its audit commit
must descend from that subject, because a receipt cannot equal the main HEAD created by committing itself.
The launchd publisher runs at 07:45 Asia/Tokyo and the PR validator reads open PR number, allowed
head prefix, and exact head SHA through the local host's read-only GitHub CLI every five minutes;
a Bot can inspect the receipt through the GitHub plugin but cannot invoke the executor.

The publisher has priority over the 5-minute validator: a stale-recoverable pending marker prevents another
validator head from starting once a publisher is waiting. Lock ownership records pid, start time, and operation;
dead or overdue owners are recovered without recursive deletion.

Private clone/fetch operations use the host credential boundary, but every npm/test/build process runs through
an `env -i` child with an isolated temporary `HOME` and no inherited SSH, GitHub, shell, or user credentials.
Automatic PR execution remains restricted to diffs whose merge-base range contains only
`intelligence/signals/**`; the local host never merges a PR.

For publication, `source.sha` remains the checkout that completed the full validation command set, while
`subject.sha` may be the later deterministic report commit. PR discovery admits only currently open
`radar-` or `keyword-radar-` heads and rechecks the fetched pull ref against the metadata head SHA.
Only the Grok Bot's connected GitHub plugin checks review and merge conditions; the local host never merges.
Existing approved records and reports are preserved rather than overwritten.

## Security boundaries

- Never treat separate bots as a security boundary.
- Company confidential knowledge must not enter the personal repository.
- Shared templates may contain methodology and public research only.
- External writes default to human approval. The only standing exception is the typed public-only
  record and blog path authorized by `config/policies.yaml` and `config/reporting.yaml`.
- Manual Document Publisher writes require approval bound to the exact content hash and target path;
  deterministic public-blog creation is authorized by the policy gate and remains append-only.
- Operational evidence is never admitted as a factual source record.
- Destructive lifecycle actions default to `retain`.
