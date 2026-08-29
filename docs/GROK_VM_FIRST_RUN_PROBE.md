---
{}
---

# Grok VM First-Run Probe

> Use this procedure on the actual Grok Bot cloud computer before treating the Miyamae newsroom runtime as operational.

# Grok VM First-Run Probe

Use this procedure on the actual Grok Bot cloud computer before treating the Miyamae newsroom runtime as operational.

## Deterministic probe

From the repository checkout on the Grok VM:

```bash
npm ci
npm run validate:miyamae-runtime
npm run miyamae:vm:bootstrap
npm run miyamae:vm:scheduler -- seed
npm run miyamae:vm:tick -- run 25
npm run miyamae:vm:selftest
npm run miyamae:vm:evidence -- validate
npm run miyamae:vm:evidence -- status
```

The self-test must not inspect browser cookies, passwords, tokens, OTP values or raw authenticated session material. It must not publish externally.

Expected evidence is written under:

```text
/workspace/miyamae/evidence
```

A single PASS is not enough to change capability policy. Re-run after a later Bot turn or VM lifecycle event and require repeated recent PASS evidence. Promotion remains human-reviewed.

## Computer-use probe

After deterministic checks pass, test the actual Grok browser separately.

1. Confirm X is reachable in the existing authorized profile.
2. If login is required, use human takeover; do not automate credential recovery.
3. From a second Miyamae Bot, confirm the same authorized session can be reused without exporting session material.
4. Claim one browser task with `miyamae-vm-healthkeeper` and verify that another worker cannot claim the same task.
5. Open one public JavaScript-rendered local source and record only structural network observations with `miyamae:vm:browser`.
6. Complete the task with a canonical public URL or `AUTH_REQUIRED`/`BLOCKED` as appropriate.
7. Repeat independently before changing any capability confidence.

These observations require a `grok-capability-evidence/v1` record with provenance `grok_bot_manual_experiment` or `operator_verified`.

## Background-runtime probe

Do not assume an arbitrary daemon is durable.

1. Verify the five-minute `miyamae-vm-wakeup` Routine runs while the operator computer is offline.
2. Verify `/workspace/miyamae` state remains available in a later Bot turn.
3. Run the one-minute daemon only as an experiment.
4. Observe its heartbeat across multiple turns and, when possible, a normal Grok VM/app lifecycle event.
5. If the daemon disappears, classify that as expected experimental behavior unless xAI documentation explicitly guarantees process survival. The Routine remains the correctness layer.

## Promotion gate

A capability is only a promotion candidate when all applicable conditions hold:

- evidence schema validation passes;
- at least two PASS observations exist within 30 days;
- no later unresolved FAIL exists for the same experiment;
- safety fields confirm no credential material was recorded and no access control was bypassed;
- behavior is consistent with current xAI documentation;
- a human reviews the evidence before changing `config/grok-capabilities.yaml`.

Run:

```bash
npm run miyamae:vm:evidence -- promotion-candidates
```

The command only recommends human review. It never edits capability confidence automatically.
