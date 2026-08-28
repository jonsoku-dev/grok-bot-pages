---
{}
---

# Local and Grok VM Validation

> This repository intentionally does **not** use CI, required status checks, or remote runners as correctness gates.

# Local and Grok VM Validation

## Policy: No CI

This repository intentionally does **not** use CI, required status checks, or remote runners as correctness gates.

GitHub remains the desired-state Source of Truth, but acceptance evidence is produced on the developer workstation or the Grok VM. Do not create or re-enable `.github/workflows/validate.yml`, retry or poll GitHub Actions validation runs, or infer correctness from a GitHub check status.

Hosted workflows are absent. The local macOS executor performs exact-SHA PR validation and report/site publication from isolated clones, then commits `local-execution-receipt/v1` evidence. Its npm/test/build children run with an empty environment and temporary `HOME`; Grok Bots only read committed receipts through the connected GitHub plugin.

## Validation profiles

### Runtime, agent, and policy changes

Run this profile for changes under `bots/`, `groups/`, `routines/`, `skills/`, Miyamae policy/schema files, or `tooling/miyamae-*`:

```bash
npm run verify:runtime
```

It executes the Miyamae test suite, Bot/schema validation, runtime-contract validation, agent workflow eval fixtures, and TypeScript checking without requiring a live VM database.

### Full repository changes

Run this profile when the change can affect generic control-plane behavior, reports, the documentation site, or multiple domains:

```bash
npm run verify:local
```

This is the complete workstation validation profile. It runs all tests followed by the repository-wide validation chain, including the documentation build.

### Live Grok VM validation

Run this profile from the checked-out repository on the Grok VM:

```bash
npm run verify:vm
```

Equivalent explicit sequence:

```bash
npm run verify:runtime
npm run miyamae:vm:probe
```

The probe is authoritative. It checks the shared current runtime-version contract, bootstraps or migrates an absent/stale runtime marker, seeds the scheduler, runs a bounded deterministic tick, executes the VM self-test, and validates capability evidence. Do not run the standalone self-test before the probe on an unseeded first boot.

For an explicit operator-controlled first bootstrap:

```bash
npm ci
npm run miyamae:vm:bootstrap
npm run miyamae:vm:probe
```

Do not install missing system packages implicitly. Report the missing prerequisite and stop.

### Documentation-only changes

For an isolated documentation/site change, the minimum focused check is:

```bash
npm run validate:docs
```

Use `npm run verify:local` when the documentation change also modifies commands, policy, schemas, generated records, or runtime contracts.

## Fail-closed acceptance rule

A change is accepted only when the selected validation profile exits with status `0` and any required live-runtime checks also pass.

- A non-zero exit means the change is rejected until corrected.
- A command that was not executed is **UNVERIFIED**, not passed.
- Static inspection, model confidence, GitHub commit success, or a delivery workflow result does not substitute for execution.
- Do not apply Grok UI/runtime mutations or publish externally from an UNVERIFIED change.

## Validation evidence

Preserve the following for every applied runtime or policy change:

- exact Git commit SHA;
- validation profile and exact command;
- execution environment (`workstation` or `grok-vm`);
- timestamp with timezone;
- process exit status;
- relevant self-test, probe, plan, and runtime-snapshot references;
- any degraded or skipped check, explicitly marked `UNVERIFIED`;
- no credentials, cookies, tokens, or browser-session material.

For Grok reconciliation, acceptance additionally requires the existing exact-state evidence: final UI re-read, correlated audit/UI observation, current runtime snapshots, and `SYNCED` plans for all managed entities.

## Operator sequence

```text
change
  -> select validation profile
  -> execute locally or on Grok VM
  -> preserve command/result and commit SHA
  -> plan
  -> approve when required
  -> apply exact plan
  -> re-read and verify runtime state
  -> preserve snapshot/audit evidence
  -> require final SYNCED plan
```

No GitHub Actions validation stage exists in this sequence.
