---
{}
---

# Grok Bot Capability Playbook for Miyamae Community Media

> Last researched: 2026-08-27

# Grok Bot Capability Playbook for Miyamae Community Media

Last researched: 2026-08-27

This document records capabilities that are unusually valuable because the runtime is Grok Bot, not merely a stateless LLM. It separates confirmed Grok Bot product capabilities from broader Grok/xAI platform capabilities that must not be assumed to exist inside a Bot until verified in the app.

## Capability confidence

- `BOT-CONFIRMED`: documented specifically for Grok Bot.
- `GROK-PLATFORM`: documented for Grok/xAI generally; useful as a possible integration, but not automatically assumed available inside Grok Bot.
- `EXPERIMENTAL`: observed/community technique that requires an explicit safe test before becoming a routine.

## 1. Persistent user-scoped cloud computer — BOT-CONFIRMED

Official Grok Bot documentation states that each user gets a persistent cloud computer. Bots run with a browser, filesystem and terminal. All Bots for the user share that computer, its files, browser sessions and sign-ins; individual Bots get separate screens but are not security boundaries.

Miyamae use:

- keep signed-in X and Threads sessions available to the Bot roster;
- keep hot operational files under `/workspace/miyamae/` for fast handoffs;
- let deterministic collection jobs write candidate packets to the shared workspace;
- let source/trend/community Bots consume the same browser sessions without repeated authentication;
- use browser login persistence for pages whose useful public surface is only available after ordinary account login;
- keep GitHub as authoritative configuration/history, not as a substitute for fast runtime state.

Operational filesystem proposal:

```text
/workspace/miyamae/
  inbox/              # newly collected candidate packets
  verified/           # verified local-story packets pending editorial choice
  reserve/            # hot cache/index of READY evergreen items
  trends/             # short-lived trend observations
  community-leads/    # replies/mentions awaiting verification
  drafts/             # X/Threads drafts pending approval/publication
  evidence/           # bounded screenshots/exports when useful
  locks/              # cooperative ownership/lease files between Bots
  health/             # last-run/source-health summaries
```

Security consequence: never place secrets in this workspace merely because one Bot appears private. Every Bot can potentially access the same computer state.

## 2. Persistent browser sessions — BOT-CONFIRMED

The user can take over the Bot computer to enter a password, passkey, 2FA or CAPTCHA, then return control. The authenticated browser session persists and can be reused by other Bots when appropriate.

Miyamae use:

- one intentional human sign-in to X;
- one intentional human sign-in to Threads;
- optionally sign in to other public/local services only when their terms and value justify it;
- never store cookies, passwords, tokens, profile directories or authorization headers in GitHub;
- if the session expires, request takeover rather than attempting authentication bypass.

This is materially better than building brittle credential automation.

## 3. Multiple Bots can coordinate independently — BOT-CONFIRMED

Bots can message each other, share context in threads/group chats and pass ownership. They may run in parallel on separate screens while sharing the same user computer.

Miyamae use:

- `miyamae-source-scout` owns broad discovery;
- `miyamae-evidence-verifier` independently verifies and risk-classifies;
- `miyamae-community-triage` owns community editing, follow-ups, and coverage review;
- `miyamae-publication-arbiter` owns the single external queue;
- `miyamae-vm-healthkeeper` owns browser tasks, health, and safe recovery;
- `miyamae-newsroom-analyst` owns metrics and editorial review.

Keep these six roles until measured reliability, permission, or independent-verification evidence requires another boundary. Platform capacity is not a reason to add a Bot.

## 4. Group chat as an operations room — BOT-CONFIRMED

A group chat can preserve visible handoffs between specialist Bots rather than forcing the human to relay every result.

Miyamae use:

Create/maintain one `Miyamae Community Media` group. Handoffs should be structured:

```text
Scout -> Verifier: candidate packet + source URLs + observedAt
Verifier -> Host: OFFICIAL/CONFIRMED local-story + risk + source-visible facts
Trend Scout -> Host: trend packet only; never factual corroboration
Reserve Curator -> Host: READY reserve candidates + freshness metadata
Host -> Human: external publish approval when required
Host -> Verifier: resident reply/mention as LEAD
```

The group is an operational conversation, not the authoritative database. Durable rules stay in GitHub.

## 5. Skills are reusable across Bots — BOT-CONFIRMED

Grok Bot skills capture repeatable steps, decision rules, expected output, validation and approval boundaries. Private installed skills can be enabled per Bot.

Miyamae use:

Repository-managed skills should be mirrored/tested in Grok Bot for:

- resilient public web research;
- authorized browser observation;
- trend-to-local natural-join logic;
- local evidence verification;
- privacy/risk classification;
- X post drafting;
- Threads discussion drafting;
- visible correction publishing;
- reserve revalidation;
- source-health diagnosis.

A skill should be tested as a one-time task before becoming a routine.

## 6. Teach a task by live browser demonstration — BOT-CONFIRMED, rollout-dependent

When `Teach a task` is available, Grok Bot can record up to ten minutes of visible browser interaction and turn the demonstration into a draft skill. The feature may roll out gradually.

This is one of the highest-value Grok-specific capabilities for this project.

Teach these tasks manually once:

### A. Publish an X post

Demonstrate:

1. open the already-signed-in X account;
2. start a post;
3. paste a prepared Japanese draft;
4. inspect link preview/media if present;
5. stop before final publish if approval must remain human;
6. after approval, publish;
7. reopen the post and copy the canonical post URL;
8. write publication evidence to the conversation/workspace.

Then edit the generated skill so risk rules, source requirements and idempotency are explicit.

### B. Publish a Threads post

Teach the equivalent Threads workflow separately. Do not assume DOM/layout or posting constraints match X.

### C. Inspect X Explore/Trending

Teach navigation to the exact current trend surface and how to collect only topic/scope/context without treating it as truth.

### D. Inspect replies/mentions

Teach the Bot how to open notifications/replies, extract bounded lead information and avoid private/irrelevant personal data.

Never expose passwords or one-time codes in a teaching recording. Use secure takeover for credentials.

## 7. Background routines while the laptop is closed — BOT-CONFIRMED

Scheduled Grok Bot routines run in the cloud and can continue while the user's laptop is closed. Each Bot may own up to 50 routines; the app keeps the 20 most recent run records for each routine. Long inactivity may cause Grok Bot to ask whether routines should continue and may pause them if there is no response.

Miyamae use:

- frequent local radar;
- trend radar;
- daily reserve refresh;
- morning/evening/weekend digests;
- periodic follow-up checks for unresolved stories;
- source-health audits;
- correction checks on previously published volatile stories.

Every routine needs explicit `no data`, stale-data, retry and partial-failure behavior. Never post solely because a routine ran.

## 8. Event-triggered routines — BOT-CONFIRMED where integration supports events

Cursor account integrations can start routines after supported events such as a Slack message or GitHub notification. This is separate from ordinary plugins and may require connection setup.

Miyamae use today:

- GitHub change events can trigger validation/reconciliation work when supported;
- do not invent an X/Threads event trigger unless Grok Bot exposes one;
- browser-polled replies/mentions remain scheduled observation until a supported event source exists.

Future possibility: an MCP/webhook ingestion service could normalize external civic alerts into an integration that triggers Grok work, but this is optional and should not replace cheap deterministic feeds.

## 9. Connectors and custom MCP — BOT/GROK-CONFIRMED ecosystem capability

Grok supports connectors and custom MCP servers. A custom MCP can expose APIs/databases/tools under controlled schemas. Grok Bot itself can use connectors/MCP where available.

Miyamae use later:

Expose a small `miyamae-local-intel` MCP only when the deterministic local collector becomes mature. Candidate tools:

- `list_recent_candidates`
- `get_source_health`
- `list_ready_reserve`
- `mark_story_verified`
- `list_unresolved_leads`
- `search_local_archive`
- `record_publication`

Do not build MCP merely to move YAML around. Start with files/CLI and add MCP when cross-Bot querying or typed mutation provides real value.

## 10. Local-computer execution — BOT-CONFIRMED, normally unnecessary

Grok Bot cloud-computer access and execution on the user's physical Mac/Windows machine are different permissions. Local execution can be Always ask, Always allow or Never allow; default is Ask every time.

Miyamae policy:

- prefer the cloud computer;
- keep local execution disabled unless a task genuinely needs a local-only resource;
- do not make the Miyamae routine depend on the operator's Mac being online.

## 11. Durable memory/preferences — BOT-CONFIRMED

A named Bot can retain stable preferences, facts and summaries over time. Official docs explicitly warn that memory is not a substitute for an authoritative source.

Miyamae use:

Good memory:
- preferred Japanese voice;
- editorial conventions;
- common neighborhood aliases;
- recurring workflow preferences;
- which kinds of drafts the operator usually rejects.

Bad memory-as-authority:
- store hours;
- event date;
- transport state;
- current office holder;
- whether a business is still open;
- any breaking incident.

Changing facts must be reopened from source evidence.

## 12. Evidence-rich files/results — BOT-CONFIRMED

Grok Bot can work with many file types and shared `/workspace` files. Official guidance recommends source links, screenshots, timestamps, filenames, concise action logs and explicit unverified items.

Miyamae use:

Every sensitive or consequential handoff should remain independently reviewable. Screenshots are supplemental evidence, not the sole source for rapidly changing information.

## 13. Grok/xAI real-time Web Search — GROK-PLATFORM

xAI documents a real-time `web_search` tool for Grok models in its developer APIs. This confirms that real-time web research is a native xAI capability, but this repository must not assume a Grok Bot conversation automatically exposes the developer API tool under that exact interface.

Miyamae use:

- if the Bot UI exposes equivalent Grok web research, benchmark it as a discovery lane;
- preserve actual source URLs, not just model summaries;
- deterministic official feeds remain preferred for repeated collection.

## 14. Grok/xAI X Search — GROK-PLATFORM, especially interesting

xAI developer docs expose `x_search` supporting keyword search, semantic search, user search and thread fetch against real-time X content.

This is potentially the most strategically relevant xAI-native capability for Miyamae, because X is also the account/community surface.

Do not silently assume Grok Bot has this developer tool. Run a product test. If available natively in Grok Bot or through an approved connector, use it for:

- `宮前区`, `宮前平`, `宮崎台`, `鷺沼`, neighborhood names;
- opening/closure reports;
- local event chatter;
- transport/road observations;
- replies around this account;
- semantic discovery of posts that omit exact keywords;
- fetching an entire X thread rather than isolated posts.

All non-official social results remain `LEAD`. Official public authority/operator accounts may establish what that authority claims, subject to risk policy.

If the only available path is paid xAI API, keep it disabled by default until the free/browser approach is measured and a deliberate budget decision is made.

## 15. Best Grok-native architecture

```text
                        GitHub SoT
        policies / schemas / skills / routines / source registry
                              |
                              v
                   Grok shared cloud computer
                /workspace/miyamae operational bus
                              |
       +----------------------+----------------------+
       |              |              |              |
 Source Scout      Verifier      Trend Scout    Reserve Curator
       |              |              |              |
 public web/API   web/browser    X + Threads     archive + sources
       +--------------+--------------+--------------+
                              |
                        Community Host
                              |
                X / Threads signed-in browser
                              |
                    replies / mentions / trends
                              |
                         new LEAD packets
```

The distinguishing feature is not a single giant autonomous Bot. It is a small persistent team sharing one operational computer, browser sessions and files while GitHub keeps the explicit control plane.

## 16. High-value experiments before autonomous posting

Run and record these tests in order:

1. Shared browser session test: sign in once, verify two Miyamae Bots can reuse the authorized X session without sharing credentials in chat/Git.
2. Parallel-screen test: Source Scout and Trend Scout research simultaneously without corrupting shared state.
3. `/workspace` handoff test: Scout writes one packet; Verifier reads and adds verification result; Host consumes it.
4. Teach-X test: teach draft/publish verification path, keeping final publish human-approved.
5. Teach-Threads test.
6. Trend test: compare browser X Explore observation vs any native Grok X-search capability actually exposed in Bot.
7. Mention/reply intake test: turn one safe reply into a community-lead/v1 record with privacy review.
8. Routine-while-offline test: close the laptop and verify a non-writing radar routine completes in the cloud.
9. Failure test: expire X session and verify the Bot asks for takeover instead of bypassing authentication.
10. Idempotency test: rerun the same publication workflow and verify it detects an existing canonical post rather than double-posting.

## Official references

- https://docs.x.ai/grok-bot/overview
- https://docs.x.ai/grok-bot/get-started
- https://docs.x.ai/grok-bot/bots
- https://docs.x.ai/grok-bot/chat-and-collaboration
- https://docs.x.ai/grok-bot/skills-routines-and-automations
- https://docs.x.ai/grok-bot/files-and-results
- https://docs.x.ai/grok-bot/approvals-security-and-privacy
- https://docs.x.ai/grok-bot/settings-and-notifications
- https://docs.x.ai/grok-bot/troubleshooting
- https://docs.x.ai/developers/tools/web-search
- https://docs.x.ai/developers/tools/x-search
- https://docs.x.ai/grok/connectors

Re-check these references before relying on product limits or rollout-dependent features because Grok Bot is changing rapidly.
