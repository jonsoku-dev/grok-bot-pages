---
{}
---

# Grok Bot Runtime Onboarding for Miyamae

> Last updated: 2026-08-27

# Grok Bot Runtime Onboarding for Miyamae

Last updated: 2026-08-27

This runbook is the bridge from GitHub desired state to the real Grok Bot product. Do not mark a capability or routine operational merely because its manifest exists in Git.

## 0. Preconditions

- Grok Bot desktop app is current.
- Agent Computer is current separately from the desktop app.
- Timezone is `Asia/Tokyo`.
- Local-computer execution is unnecessary for Miyamae and should remain disabled or Ask Every Time.
- GitHub access is authenticated through the intended Grok/Cursor plugin path.
- No secrets are stored in GitHub, ordinary Bot messages, `/workspace/miyamae`, screenshots or audit logs.

Official product notes: Grok Bot app updates and Agent Computer updates are separate. Routines use the configured timezone. Cloud-computer work does not require local-computer execution.

## 1. Create/sync the Bot roster

Desired Bots:

1. `Miyamae Source Scout`
2. `Miyamae Evidence Verifier`
3. `Miyamae Trend Scout`
4. `Miyamae Reserve Curator`
5. `Miyamae Community Host`
6. `Grok Capability Scout`

Desired groups:

- `Miyamae Community Media`
- `Grok Platform Research`

Use the repository's existing `botctl export`, `guided`, routine export and UI-observation workflow to compare desired fields with the real Grok Bot UI. Do not use Bot identity as a security boundary; all Bots share the same user computer.

## 2. Prepare the shared workspace

Ask one safe Bot to create:

```text
/workspace/miyamae/
  inbox/
  verified/
  reserve/
  trends/
  community-leads/
  drafts/
  evidence/
  locks/
  health/
```

Create a README inside `/workspace/miyamae` stating that the directory contains ephemeral operational state only and may never contain passwords, session cookies, auth headers, private DMs, secret tokens or unrelated personal data.

Test: Source Scout writes a harmless sample packet; Evidence Verifier reads it; Community Host reads the verified output. Record paths and timestamps.

## 3. Authenticate X safely

Use the Bot computer browser.

1. Navigate to X.
2. If authentication is needed, use Take Over.
3. Enter password/passkey/2FA/CAPTCHA personally.
4. Confirm the signed-in account is the intended Miyamae community account.
5. Return control to the Bot.
6. Ask Source Scout to open a read-only X page and report only the visible account handle and URL.
7. Ask Trend Scout, a different Bot, to open X Explore. This verifies cross-Bot reuse of the same persistent browser session.

Failure rule: if the session expires later, request takeover again. Never ask the Bot to extract or persist browser credentials.

## 4. Authenticate Threads safely

Repeat the same Take Over pattern for Threads. Verify read-only navigation from both Trend Scout and Community Host.

Do not assume X and Threads workflows are interchangeable. They receive separate taught skills and verification tests.

## 5. Test parallel screens

Because Grok Bot documents separate screens for Bots sharing one computer:

- Source Scout: open Miyamae/Kawasaki official information in its screen.
- Trend Scout: open X Explore or Threads search in its screen.
- Run both during the same period.
- Confirm neither Bot destroys the other's browser task or shared workspace packet.

If shared filesystem races occur, use `/workspace/miyamae/locks` cooperative leases. Browser tabs on different Bot screens should not be treated as globally locked unless field testing proves a shared conflict.

## 6. Teach X draft/publish workflow

Only when `Teach a task` is visible in the current Grok Bot rollout.

Use a harmless test post or a draft-only demonstration first.

Demonstrate within the documented ten-minute window:

1. open X compose;
2. paste a prepared Japanese draft from `/workspace/miyamae/drafts`;
3. inspect the exact text and link/media preview;
4. identify the human approval boundary;
5. for a safe test, publish only after explicit approval;
6. reopen the resulting post;
7. copy the canonical X post URL;
8. record completion evidence.

After Grok creates the draft skill, edit it to add:

- input story id;
- allowed risk classes;
- source-visible requirement;
- duplicate/canonical-URL pre-check;
- exact approval boundary;
- post-publish URL verification;
- partial/failure reporting;
- rule that a retry must not create a duplicate post.

Do not schedule the learned workflow until it succeeds safely on at least two distinct low-risk inputs.

## 7. Teach Threads workflow

Repeat the same process independently. Preserve platform-specific limits, preview behavior and canonical result URL handling discovered during the live demonstration.

## 8. Teach trend observation

Teach Trend Scout how to reach the current X Explore/Trending UI using the already-authorized session.

The learned output must be `miyamae-trend/v1`, never `local-story/v1`.

Required output:

- topic/query;
- observedAt;
- scope: Miyamae/Kawasaki/Kanagawa/Japan/personalized/unknown;
- source URL/surface when available;
- signals/context;
- `evidenceEligible: false`;
- matched verified/reserve ids, if any;
- recommended action or SKIP.

Do not infer that a personalized trend represents all X users or all Miyamae residents.

## 9. Teach reply/mention intake

Use a harmless reply or a test interaction.

The Bot should extract only what is needed for `miyamae-community-lead/v1`:

- canonical source URL;
- bounded lead text;
- observed time;
- optional public handle only when useful;
- area hints;
- risk hints;
- privacy-review flag;
- disposition `PENDING` or `VERIFY`.

Do not ingest private DMs, unrelated follower information, home addresses or excessive profile data.

## 10. Test native Grok X Search availability

xAI developer documentation exposes an X Search capability with keyword, semantic, user search and thread fetch. This does not prove Grok Bot exposes the same tool automatically.

Ask `Grok Capability Scout` in the Bot product to perform a harmless X discovery task such as:

- recent public posts mentioning `宮前区`;
- semantic equivalents that discuss Miyamae without the exact ward keyword;
- fetch a public thread from a known URL.

Record:

- exact product/tool surface used;
- whether it required paid API configuration;
- whether result links are canonical X URLs;
- whether search supports semantic vs exact keyword behavior;
- whether user/thread retrieval works;
- latency/coverage compared with browser X search.

If the Bot cannot do this natively, keep `grok_x_search` as `GROK_PLATFORM / benchmark_first` and use the free authorized-browser route.

## 11. Test background routine while operator device is offline

Create/test only a non-writing routine first, e.g. Source Scout radar.

- confirm next run time in Asia/Tokyo;
- close the local laptop or disconnect it after the routine is scheduled;
- later inspect recent routine history;
- verify current source timestamps and `/workspace` result;
- confirm no stale data was substituted silently.

Only after this succeeds should unattended Miyamae collection be treated as operational.

## 12. Auto-review / approval policy

Use Grok Bot's Auto Review controls conservatively.

Initial recommendation:

- read public web/browser: allow where appropriate;
- write temporary `/workspace/miyamae` state: allow;
- mutate GitHub SoT: review unless an existing tested GitHub policy grants a narrow path;
- publish X/Threads: require approval;
- send DMs/messages: require approval / normally deny;
- delete content: require approval;
- install plugins/MCP/authenticate new services: require approval;
- local-computer execution: deny or ask every time.

Require-approval rules should be tested because the product documents that Require rules take precedence over allow rules.

## 13. Plugin evaluation

Start with no extra community plugin merely for novelty.

The official xAI plugin marketplace is the preferred discovery registry. For each plugin considered:

1. inspect the actual plugin repository/manifest;
2. identify MCP endpoints, commands, hooks, skills and required variables;
3. determine shared-computer impact;
4. determine whether it can externally write;
5. test with non-sensitive data;
6. document exact permissions and removal procedure.

High-value future candidate: Chrome DevTools tooling if it materially improves browser reliability/inspection. It is not required for v1 local-information collection.

## 14. Completion gates before auto-publishing R0/R1

Do not enable autonomous publication until all are true:

- shared X session verified across at least two Bots;
- shared Threads session verified where Threads posting is intended;
- X publish learned workflow succeeds twice without duplicate posting;
- Threads workflow succeeds twice if enabled;
- canonical post URL captured after each test;
- session-expiry test correctly stops for takeover;
- social reply intake remains LEAD;
- trend observation remains evidence-ineligible;
- at least 100 representative content/risk evaluation cases pass policy gates;
- correction workflow has been tested;
- external-write approval behavior is verified in the actual app version;
- source-health/no-data behavior is explicit;
- operator understands that all Bots share the same cloud-computer security boundary.

Until then, automation may discover, verify, store, rank and draft, but publishing stays review-gated.
