---
{}
---

# Architecture

> ```text
GitHub private repository
  desired state + canonical knowledge
            |
            +--> deterministic validation / GitHub Actions
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
            +--> deterministic validation / GitHub Actions
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

## Delivery architecture

Research and delivery are separate responsibilities.

```text
External sources -> scouts -> verifier -> evaluator
                                      |
                                      v
                              GitHub SoT Writer
                              factual YAML records
                                      |
                                      v
                              Document Publisher
                        document-publication/v1 draft
                                      |
                       exact hash + target approval
                                      |
                                      v
                          reports/** -> Docusaurus
                                      |
                                      v
                               GitHub Reader
                              /             \
                     Slack Publisher   Gmail Publisher
```

GitHub SoT Writer changes records only. Document Publisher changes reader-facing documents only.
Slack and Gmail operate on an approved current document through `canonical-content/v1`. Simple
GitHub-to-channel copying should be deterministic. Semantic digesting, selection, or audience
adaptation can be agentic.

## Security boundaries

- Never treat separate bots as a security boundary.
- Company confidential knowledge must not enter the personal repository.
- Shared templates may contain methodology and public research only.
- External writes default to human approval.
- Document writes require approval bound to the exact content hash and target path.
- Operational evidence is never admitted as a factual source record.
- Destructive lifecycle actions default to `retain`.
