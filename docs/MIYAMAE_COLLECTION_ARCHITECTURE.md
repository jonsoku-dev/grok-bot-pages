---
{}
---

# Miyamae Collection Architecture

> Build a low-cost, high-coverage local-information system for 神奈川県川崎市宮前区 that can keep publishing useful information without requiring the human operator to search for or write posts manually.

# Miyamae Collection Architecture

## Objective

Build a low-cost, high-coverage local-information system for 神奈川県川崎市宮前区 that can keep publishing useful information without requiring the human operator to search for or write posts manually.

The account is both a media surface and the community surface. Discovery and discussion happen in X/Threads; GitHub remains the configuration/SoT for policies, schemas and operational knowledge.

## Collection layers

### Layer A — deterministic/public feeds

Preferred because they are cheap, stable and high-trust:

- 川崎市 / 宮前区 RSS
- 川崎市 event open API
- 川崎市 open data/catalog files
- 神奈川県 RSS/emergency feeds
- JMA public disaster/weather pages/XML
- transport/operator status pages and feeds

### Layer B — public web discovery

Use local keyword searches for openings, closures, construction, events, facilities and first-party business announcements. Fetch the first-party source whenever possible instead of repeating search-result snippets.

### Layer C — resilient browser research

When a public page is JavaScript-rendered or ordinary fetch fails, use the authorized Chrome/browser runtime following `skills/resilient-public-web-research/SKILL.md`. Browser access is a fallback, not the default crawler.

### Layer D — social/trend discovery

X/Threads posts and trends produce leads, questions and format signals. They are not factual evidence. Google Trends provides an additional free Japan-wide signal.

### Layer E — resident sensor network

Replies, mentions and quoted posts become structured `LEAD` records. The verifier searches independent evidence before promotion. This lets the account gradually become a community without a separate forum.

## Fresh lane vs reserve lane

Two inventories run in parallel.

### Fresh lane

Designed for immediate utility:

- disaster/weather
- rail/bus disruption
- road/utility changes
- ward/city notices
- confirmed openings/closures
- events/deadlines
- construction and facility changes

Breaking verified utility always outranks scheduled content.

### Reserve lane

A continuously maintained inventory of low-risk, useful, still-valid information:

- parks and walks
- libraries and facilities
- local history
- disaster-preparedness knowledge
- recycling/waste tips
- parenting resources
- markets/farms/direct-sale stands
- seasonal nature
- transit tips
- evergreen local services

Reserve target: 80 READY items; warn below 30; roughly 21 days of coverage. Each item has `verifiedAt`, `recheckAt`, `expiresAt`, seasonality and a source fingerprint. The reserve curator expires or refreshes stale records before they can be drafted.

Reserve is not filler at any cost. Emergency, accident, crime, death and controversy are forbidden reserve categories.

## Trend lane

Trend collection runs independently from story verification.

Sources:

- X Explore/Trending through an authorized account/browser
- X local keyword search
- Threads public/search surfaces available to the authorized browser
- Google Trends Japan
- this account's own recent interaction patterns

A trend may influence publication timing, headline framing, question/poll format, which READY reserve item is useful now, and follow-up timing. A trend may never corroborate a factual claim, turn a LEAD into CONFIRMED, justify unrelated trend-jacking, or weaken privacy/risk rules.

## Scheduling model

- every 5 min class: emergency/operator sources where practical
- every 10–20 min: ward/city RSS, transport, fresh local sweep
- every 20 min: consolidated Miyamae radar routine
- minute 10/40 each hour: trend radar
- 05:15 daily: reserve replenish/revalidation
- morning/evening/weekend digests are later publication-layer routines using already verified inventory

Do not force a post on every run.

## Free-first research findings

As researched on 2026-08-27:

- Kawasaki publishes an official RSS directory including ward, city bus, waterworks and education feeds.
- Kawasaki's official event app exposes a documented Web API with pagination and reusable event data under CC BY 2.1 Japan.
- Kawasaki maintains open-data initiatives including shelters and other civic datasets.
- Kawasaki offers a registered disaster/weather mail service covering emergency information, earthquakes, warnings, forecasts and disaster-radio content; use only when the runtime has an intentionally authorized mailbox, otherwise consume equivalent public sources.
- Kanagawa publishes a general RSS feed and emergency information surface.
- JMA provides machine-readable disaster/weather information and public warning pages.
- X officially exposes location-aware Trending/Explore surfaces in signed-in x.com; use the account's authorized browser rather than a paid API in v1.
- Google Trends publicly exposes Japan 'Trending now' and is useful as a non-social cross-check for current interest.
- `fivetaku/insane-search` demonstrates a useful public-content escalation architecture: machine-readable/public endpoints first, cheap variants next, then rendered browser, and stop at authentication/paywall boundaries. This repository adopts the architecture concept, not a promise that every site can or should be bypassed.

## Community flywheel

```text
public sources ─┐
operator pages ─┼─> discover -> verify -> post -> replies/mentions
web/browser ────┤                              │
trends ─────────┘                              v
                                           new LEAD
                                              │
                                              └-> verify -> follow-up
```

Community strength should be measured by useful submissions, repeated contributors, corrections, answered questions and resident-to-resident help—not follower count alone.

## Operational boundaries

- public information does not automatically mean appropriate publication
- cache and rate-limit instead of repeatedly hammering sites
- respect access restrictions and terms
- never store credentials/session cookies in Git
- no CAPTCHA/login/paywall circumvention
- private-person allegations remain R3/human-only
- trend and resident content are discovery signals until independently verified
- corrections and source changes must propagate to reserve/follow-up records

## Next implementation gates

1. Validate the new bot/group/routine manifests in CI.
2. Add deterministic adapters for Kawasaki RSS + event API before browser automation.
3. Add a raw candidate cache and content-hash deduplication.
4. Add local-story validation and fixture corpus.
5. Execute dry runs without external publication and measure source coverage/precision.
6. Configure Grok browser routines for X/Threads trend observation.
7. Only after evaluation, permit selected R0 publication; R2/R3 remain human-gated.
