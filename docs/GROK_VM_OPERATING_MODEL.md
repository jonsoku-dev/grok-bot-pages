---
{}
---

# Grok VM Operating Model for Miyamae Newsroom

> Grok Bot runs on a persistent user-scoped Linux cloud computer with browser, filesystem and terminal. All Bots on the account share that computer, including browser sessions and logins. Background turns and routines continue when the founder laptop is closed.

# Grok VM Operating Model for Miyamae Newsroom

## Why the VM is first-class

Grok Bot runs on a persistent user-scoped Linux cloud computer with browser, filesystem and terminal. All Bots on the account share that computer, including browser sessions and logins. Background turns and routines continue when the founder laptop is closed.

For Miyamae this means the cloud computer is not a scratchpad. It is the continuously running newsroom execution host.

## Authority split

GitHub is the durable source of truth for:

- policies
- schemas
- Bot/Group/Routine manifests
- source registry
- deterministic runtime source code
- skills and reference research

The Grok VM is authoritative for ephemeral operational state:

- source health and cursors
- current queues
- browser observations
- cached source bodies
- Local Pulse raw windows
- computed metrics
- active locks
- transient evidence packets

Never copy credentials, cookies, session tokens, OTP values, passkeys or browser-profile secrets into GitHub or the operational database.

## VM bootstrap

From the repository checkout on the Grok VM:

```bash
npm ci
npm run validate:miyamae-runtime
npm run miyamae:vm:bootstrap
```

The bootstrap creates `/workspace/miyamae`, initializes SQLite with WAL mode, creates state/cache/log/queue directories and writes a readiness marker.

## Deterministic-first runtime

Use terminal code for stable machine-readable sources:

- RSS / Atom / XML
- official JSON APIs
- conditional HTTP with ETag / Last-Modified
- hashing and dedupe
- source cursors and health
- publication arbitration
- retention and pruning
- metrics and coverage calculations

Use the agent/browser for work that actually benefits from a computer-using model:

- X and Threads observation in an authorized signed-in session
- JavaScript-only pages
- ambiguous local discovery
- interactive site navigation
- publication and canonical URL verification
- visual changes that are not exposed in structured data
- investigating repeated browser workflows for a safer deterministic adapter

## Browser -> deterministic adapter promotion

Browser work should become cheaper and more reliable over time.

When a Bot repeatedly reads the same public page through Chrome:

1. Inspect the rendered page and DevTools/network activity.
2. Look for stable public JSON, XHR, GraphQL, RSS or document endpoints.
3. Record only endpoint metadata, never auth headers/cookies/tokens.
4. Confirm the endpoint is public without authentication and automation is not disallowed.
5. Observe the same endpoint successfully more than once.
6. Create an `adapter_candidate` record with status `OBSERVE`.
7. After review, implement a deterministic adapter in GitHub with fixtures/tests.
8. Only then reduce browser usage for that source.

Never use this process to bypass CAPTCHA, authentication, paywalls, access controls or rate limits.

## Shared-VM concurrency

Bots are not isolated processes or security boundaries. Use:

- SQLite WAL for shared operational indexes
- atomic file replacement for record files
- advisory lock files for browser publication and migrations
- single global publication queue
- stable record IDs in Bot-to-Bot messages instead of copying full payloads

The publication browser is a serialized critical section even if research Bots run in parallel.

## Browser session policy

Authentication is completed through human takeover when needed. Once authorized, other Bots may reuse the same session because the VM is shared.

Bots must:

- never export cookies or session storage
- never place credentials in prompts or logs
- request takeover on expired sessions or CAPTCHA
- sign out/remove access when the service should no longer be available

## Offline operation

The steady-state design must keep useful operation running with the founder laptop offline:

- urgent source radar
- normal source collection
- reserve refresh
- trend/local-pulse observation where session remains valid
- follow-up checks
- coverage audit
- newsroom metrics

Local-computer execution is exceptional and not part of production availability.

## Recovery

On Bot VM startup/update/reset:

1. update the repository checkout
2. validate SoT
3. run VM bootstrap/migrations
4. recover stale locks
5. inspect source health
6. verify required browser sessions without exporting secret material
7. resume due routines

A VM rebuild must not be treated as permission to silently weaken publication or authentication gates.
