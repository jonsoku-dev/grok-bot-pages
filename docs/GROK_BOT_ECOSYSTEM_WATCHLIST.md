---
{}
---

# Grok Bot Ecosystem Watchlist

> Last reviewed: 2026-08-27

# Grok Bot Ecosystem Watchlist

Last reviewed: 2026-08-27

Purpose: continuously discover useful Grok Bot capabilities without letting hype or unverified community claims leak into production behavior.

## Tier A — primary/official

### xAI / SpaceXAI Grok Bot docs

- https://docs.x.ai/grok-bot/overview
- https://docs.x.ai/grok-bot/get-started
- https://docs.x.ai/grok-bot/bots
- https://docs.x.ai/grok-bot/chat-and-collaboration
- https://docs.x.ai/grok-bot/skills-routines-and-automations
- https://docs.x.ai/grok-bot/files-and-results
- https://docs.x.ai/grok-bot/approvals-security-and-privacy
- https://docs.x.ai/grok-bot/settings-and-notifications
- https://docs.x.ai/grok-bot/troubleshooting
- https://docs.x.ai/grok-bot/teams-and-enterprises

Use for product limits, security boundaries, routine behavior and supported capabilities.

### xAI Grok developer tools

- https://docs.x.ai/developers/tools/web-search
- https://docs.x.ai/developers/tools/x-search
- https://docs.x.ai/grok/connectors

These document broader Grok/xAI capabilities. Never assume exact developer-tool availability inside Grok Bot until tested in the Bot product.

### Official xAI plugin marketplace

- https://github.com/xai-org/plugin-marketplace

High-value categories to watch for this project:

- browser / Chrome / observability
- search and research
- social/media intelligence
- storage/databases
- automation/integration
- mapping/local/geospatial
- civic/open-data connectors

Treat marketplace inclusion as stronger provenance than a random community list, but still inspect plugin permissions and behavior before installation.

## Tier B — high-value upstream engineering references

### insane-search

- https://github.com/fivetaku/insane-search
- pinned research commit in config/grok-capabilities.yaml

Why watch: adaptive public-content access, public endpoint/feed-first escalation, rendered browser fallback, source blocking classification. Adopt procedure concepts conservatively; never interpret resilience as authorization to bypass access controls.

### browser-use

- https://github.com/browser-use/browser-use
- pinned research commit in config/grok-capabilities.yaml

Why watch: controlled persistent Chrome operation, live-browser reliability, browser-harness patterns. Our repository uses procedure inspiration; it does not automatically install or execute browser-use.

## Tier C — community discovery, verify before use

### ZeroPointRepo/awesome-grok-bot

- https://github.com/ZeroPointRepo/awesome-grok-bot

Useful because it tracks the very young Grok Bot plugin/skill/MCP ecosystem and distinguishes several extension mechanisms. It is unofficial. Every interesting entry must be checked against its own repository and, where relevant, xAI documentation.

### RongleCat/awesome-grok-bot

- https://github.com/RongleCat/awesome-grok-bot

Useful as a second independent discovery list and for community/failure-mode links. Never treat popularity/list inclusion as compatibility or security evidence.

### Cursor Community Forum

- https://forum.cursor.com/tag/grok-bot

Useful for real rollout bugs, auth/plugin failures, user workarounds, regressions and newly released controls. Forum statements require product-doc or reproducible confirmation before becoming policy.

## Research method

For every candidate capability or plugin:

1. Record discovery source.
2. Find primary product docs or repository.
3. Determine whether it is specifically Grok Bot, broader Grok/xAI, Cursor, or a third-party integration.
4. Record current version/commit/date where feasible.
5. Inspect license and installation/permission scope.
6. Classify security surface: browser, shared filesystem, terminal, external write, secret access, local-computer execution.
7. Ask whether it improves Miyamae information coverage, verification, community, trend understanding, publication reliability or operational cost.
8. Define a smallest safe experiment.
9. Keep it `watch` until the experiment succeeds twice on non-consequential inputs.
10. Only then promote it to a Bot skill/routine dependency.

## Current adoption decisions

| Capability/reference | State | Use |
|---|---|---|
| Grok persistent shared computer | ADOPT | hot operational workspace and shared authenticated browser |
| Multi-Bot parallel screens/handoff | ADOPT | specialist roster and group workflow |
| Background routines | ADOPT | radar, reserve, trend and later follow-up checks |
| Teach a task | TEST | X/Threads posting, trends, replies when rollout exposes control |
| Grok native X Search | TEST | potentially highest-value X discovery path; Bot availability not assumed |
| Grok native Web Search | TEST | discovery benchmark; official feeds remain deterministic lane |
| Custom MCP | DEFER | build only after typed cross-Bot local archive access has demonstrated need |
| insane-search concepts | ADOPT | free/public fetch escalation and browser fallback procedure |
| browser-use concepts | ADOPT | controlled authorized browser observation procedure |
| random community Grok skills | WATCH | inspect case-by-case; no blind installs |

## Anti-patterns

- installing every new plugin because it is popular;
- giving a plugin shared browser/terminal access without examining permissions;
- treating one community README as official Grok behavior;
- using a separate Bot as a security sandbox on the shared user computer;
- converting a fresh trick into a recurring routine before one-time testing;
- depending on paid API access while a reliable free official feed exists;
- silently replacing a primary source with AI search summaries.
