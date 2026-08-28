---
{}
---

# Codex App Handoff

> Maintain one Git-backed Grok Bot pipeline: AI Engineering Radar. GitHub is desired state and factual SoT; Grok is runtime state.

# Codex App Handoff

## Mission

Maintain one Git-backed Grok Bot pipeline: AI Engineering Radar. GitHub is desired state and factual SoT; Grok is runtime state.

## Active roster

- Discovery: Open Signal Scout, GitHub Scout, Release Scout
- Verification and judgment: Evidence Verifier, Relevance Judge
- Persistence and recovery: GitHub SoT Writer, SoT PR Reconciler
- Output and proof: Document Publisher, Blog Publication Verifier
- On-demand intake: Keyword Radar

The only active Group is `ai-engineering-radar`. The active Routines are daily research, daily PR reconciliation, daily publication verification, and weekly review.

## Required workflow

```text
manifest change
  -> npm test
  -> npm run validate
  -> botctl plan
  -> approved Computer Use apply
  -> exact UI re-read
  -> verified runtime snapshot
```

Use only Codex App built-in Computer Use for Grok Desktop. Never use Orca. Desired Bots that access the private repository use only the connected GitHub plugin.

## Publication path

```text
06:30 research
07:30 signal PR reconciliation
07:45 deterministic publish and Docusaurus deploy
08:15 live publication verification
```

The local macOS launchd executor is the only publisher. It runs deterministic scripts from an isolated temporary clone and emits a SHA-bound `local-execution-receipt/v1`; hosted CI is not an execution dependency.

## Completion gates

- Every active manifest and reference validates.
- No deleted Bot, Group, Routine, or Skill appears in the active registry.
- Factual records remain separate from reader output and audit evidence.
- Live pages expose every expected record ID and source link.
- `llms-results.txt` and `llms-sot.txt` contain the published record set.
