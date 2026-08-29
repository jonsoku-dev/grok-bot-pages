---
{}
---

# Grok VM Newsroom Runbook

> This is the execution runbook for the Miyamae local newsroom on Grok Bot's shared user-scoped Linux cloud computer.

# Grok VM Newsroom Runbook

This is the execution runbook for the Miyamae local newsroom on Grok Bot's shared user-scoped Linux cloud computer.

The durable desired state lives in GitHub. Runtime state lives under `/workspace/miyamae`. The Grok browser session is an authorized execution surface, not a place to export credentials.

## 1. First boot

From the checked-out `jonsoku-dev/grok-bot` repository on the Grok VM:

```bash
npm ci
npm run validate:miyamae-runtime
npm run miyamae:vm:bootstrap
npm run miyamae:vm:scheduler -- seed
npm run miyamae:vm:tick -- run 25
```

Expected runtime marker:

```text
/workspace/miyamae/state/runtime-ready.json
```

Expected database:

```text
/workspace/miyamae/state/miyamae.db
```

If `sqlite3` is unavailable, stop and report the prerequisite. Do not silently install system packages.

## 2. Authoritative wake-up

The `miyamae-vm-wakeup` Grok Routine is the correctness layer. It runs every five minutes and invokes the deterministic tick.

Manual equivalent:

```bash
npm run miyamae:vm:tick -- run 25
```

The tick will:

1. seed the scheduler automatically if the health table is empty;
2. select only sources whose `next_due_at` is due;
3. run RSS/Atom/JSON API collectors directly;
4. append newly discovered candidates to `/workspace/miyamae/inbox`;
5. record source health and adaptive next-run time;
6. create prioritized browser tasks for browser-only sources.

## 3. Inspect source scheduling

```bash
npm run miyamae:vm:scheduler -- due 50
npm run miyamae:vm -- health
```

Record a manual source result only when needed:

```bash
npm run miyamae:vm:scheduler -- record <sourceId> success true 250 rss <contentHash>
```

Source tiers:

```text
S emergency
A transport / essential service
B official local updates
C business / web / trend discovery
D evergreen / open data
```

Circuit breakers and adaptive polling are runtime state. Do not hard-code temporary failure observations back into GitHub policy.

## 4. Browser work on Grok's computer

Browser work is a separate claimed queue because all Bots share one computer and can work in parallel.

List work:

```bash
npm run miyamae:vm:browser-tasks -- pending 10
```

Claim before using the browser:

```bash
npm run miyamae:vm:browser-tasks -- claim <taskId> miyamae-vm-healthkeeper
```

Then use Grok's shared authorized private/incognito browser window. Every Grok-side login requires human takeover in that window; never authenticate in a normal window or copy session material. Preserve the canonical URL and observed time. Never export cookies, tokens, credentials, OTP values or raw browser session material.

When a repeatable public JSON/XHR endpoint is visible, record structural evidence only:

```bash
npm run miyamae:vm:browser -- observe \
  <sourceId> \
  <pageUrl> \
  <endpointUrl> \
  GET \
  200 \
  application/json \
  true \
  'keys:id,title,updated_at'
```

Do not pass raw response bodies as the shape signature.

Complete the task:

```bash
npm run miyamae:vm:browser-tasks -- complete <taskId> DONE <canonicalResultUrl>
```

Other completion states:

```text
NO_CHANGE
AUTH_REQUIRED
BLOCKED
FAILED
```

If authentication, 2FA or CAPTCHA is required, use `AUTH_REQUIRED` and request human takeover.

## 5. Adapter promotion

Review accumulated endpoint evidence:

```bash
npm run miyamae:vm:browser -- candidates
```

Promotion requires all of the following:

- repeated observation;
- no authentication dependency;
- stable response shape;
- explicit terms/access review;
- no access-control bypass;
- deterministic implementation in GitHub with tests.

Terms review:

```bash
npm run miyamae:vm:browser -- review <candidateId> terms-ok
```

After a deterministic adapter is merged and verified:

```bash
npm run miyamae:vm:browser -- review <candidateId> adopted
```

## 6. Local Pulse

The Browser Worker or Trend Scout records only public observation metadata required for Local Pulse.

```bash
npm run miyamae:vm:pulse -- observe 宮前平 x <publicHandle> 3 1 <publicPostUrl> 開店 パン屋
```

Daily aggregation:

```bash
npm run miyamae:vm:pulse -- aggregate
```

Anomaly detection:

```bash
npm run miyamae:vm:pulse -- anomalies 60
```

Every result has `evidenceEligible: false`. A pulse anomaly is a research trigger, never confirmation.

## 7. Publication queue

Miyamae external publishing runs unattended under standing user authorization. Per-post approval is not requested. Only source-revalidated R0/R1 C2/C3 Japanese candidates for `@Roseliafam` can be claimed; every other candidate fails closed.

Inspect:

```bash
npm run miyamae:vm:publication -- queue
```

Claim next eligible item:

```bash
npm run miyamae:vm:publication -- claim miyamae-publication-arbiter
```

A result may be:

```text
EMPTY
COOLDOWN
POLICY_HOLD
DEFERRED_COLLISION
CLAIMED
LOST_RACE
```

After actual platform publication, provide a receipt containing `postReReadAt` after opening the canonical URL and re-reading the exact account and text:

```bash
npm run miyamae:vm:publication -- mark <queueId> published <canonicalPostUrl>
```

Never mark a post published before the canonical URL, `@Roseliafam`, and exact Japanese text are verified.

For an ambiguous browser write, inspect the exact live account and post for the idempotency key before retrying. Never issue a blind second write.

Every publication payload is one Japanese post and one idempotency unit. It needs a useful verified lead, two to three verified facts, why it matters or a resident action, an honest caveat and a primary-source link. One bounded answerable question is optional; never use engagement bait. English and Korean translations may remain internal but are not posted. Account, authentication, source, or write ambiguity keeps the candidate `POLICY_HOLD`.

## 8. Metrics

```bash
npm run miyamae:vm:metrics -- calculate
npm run miyamae:vm:metrics -- report 7
npm run miyamae:vm:metrics -- report 30
```

Metrics that are not instrumented must stay `UNAVAILABLE`. Never fabricate values to make the scorecard complete.

## 9. Experimental one-minute daemon

The Grok docs guarantee the cloud computer and background routines, but do not guarantee arbitrary long-running process survival across VM maintenance. Therefore the daemon is experimental.

Do not make production correctness depend on it.

Before the `vm-daemon-survival` experiment passes, only run it manually for evidence collection:

```bash
npm run miyamae:vm:daemon
```

Heartbeat:

```text
/workspace/miyamae/state/daemon-heartbeat.json
```

Lock:

```text
/workspace/miyamae/state/daemon.lock
```

The daemon performs deterministic collection/pulse/recovery/metrics work only. It never publishes externally.

If it dies, the five-minute `miyamae-vm-wakeup` Routine remains authoritative and the newsroom continues operating.

## 10. Recovery rules

Do not delete a lock just because it exists. Prove it is stale first.

Recover stale browser task locks:

```bash
npm run miyamae:vm:browser-tasks -- recover 30
```

Recover stale publication claims:

```bash
npm run miyamae:vm:publication -- recover
```

For an expired X/Threads login or a closed incognito window, request human takeover in a new private/incognito window. Never attempt credential recovery, normal-window fallback or CAPTCHA bypass.

## 11. Security boundary

All Miyamae Bots share the same user VM. Bot identity is not a security boundary.

Never persist the following in GitHub, SQLite, logs, browser observation records or Bot handoffs:

- passwords;
- cookies;
- bearer/session tokens;
- private keys;
- OTP/2FA codes;
- exported browser profiles;
- raw authenticated response bodies containing account data.

Use stable record IDs, hashes and canonical public URLs for handoff instead.

## 12. Definition of healthy

The runtime is healthy when:

- `runtime-ready.json` exists and matches the current runtime schema;
- SQLite is queryable in WAL mode;
- source scheduler is seeded;
- no unexplained stale locks exist;
- Tier S/A sources are not silently stale;
- browser task backlog is bounded;
- AUTH_REQUIRED tasks are surfaced to the operator;
- publication claims are not stale;
- metrics calculate without invented values;
- the Routine wake-up works with the founder laptop closed;
- the daemon, when enabled experimentally, is treated only as an optimization.
