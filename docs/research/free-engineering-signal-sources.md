---
{}
---

# Free AI/software-engineering signal sources

> Research date: 2026-08-23. Scope: public, no-paid-API inputs that can replace X as the discovery layer for `X Signal Scout`. “Free” here means no paid vendor quota; network, storage, and any local model/browser execution still have an operational cost.

# Free AI/software-engineering signal sources

Research date: 2026-08-23. Scope: public, no-paid-API inputs that can replace X as the discovery layer for `X Signal Scout`. “Free” here means no paid vendor quota; network, storage, and any local model/browser execution still have an operational cost.

## Recommendation

Use a portfolio rather than a one-for-one social-network replacement, ranked for this repository’s AI-engineering radar:

1. **GitHub public activity and releases** — strongest deterministic evidence of shipped software, repositories, and maintainer activity.
2. **Hacker News** — deterministic, unauthenticated discussion and link signal with unusually simple official access.
3. **Publisher-owned RSS/Atom** — highest precision for official changelogs, release blogs, and project announcements; breadth depends on the configured feed list.
4. **Bluesky public AppView** — useful broad conversation discovery without login; treat it as a lead source, not evidence by itself.
5. **arXiv API/RSS** — authoritative research leads and metadata, but slower and subject to a strict request cadence.
6. **Mastodon public API/RSS** — potentially valuable maintainer/community discussion, but instance fragmentation makes coverage and availability uneven.

This keeps deterministic collection separate from the existing agentic scout, verifier, and judge stages. Browser/agentic work is a review fallback for a linked page or a source that has no usable feed/API; it should not be the normal collector.

## Source matrix

| Rank | Source and primary endpoint | Access classification | Adapter | Signal and caveats |
| --- | --- | --- | --- | --- |
| 1 | [GitHub REST activity/events](https://docs.github.com/en/rest/activity/events), [releases](https://docs.github.com/en/rest/releases/releases) | Public data can be fetched without authentication. Unauthenticated REST quota is **60 requests/hour per originating IP**; authenticated public-data requests are a free-quota path at 5,000/hour, but require a token and must not be introduced implicitly. | **Deterministic HTTP**; use ETags/cursors and a small allow-list of repos/orgs. | Excellent for release, push, issue/PR, and maintainer activity. GitHub explicitly says Events API is not real-time and may lag 30 seconds to 6 hours. Do not treat an event timestamp as a complete or instant stream. |
| 1b | [GitHub Changelog](https://github.blog/changelog/) RSS link | Unauthenticated publisher-owned RSS/Atom feed; no numeric feed quota is published on the page. | **Deterministic RSS/Atom**; browser only for a page that cannot expose a feed. | High-precision official product/platform changes. Keep feed URL in configuration and persist `ETag`/`Last-Modified`; feed availability and retention are publisher-controlled. GitHub’s REST `/feeds` endpoint is not a replacement for a public unauthenticated global firehose: its documented feed resources include authenticated timelines. |
| 2 | [Official Hacker News API](https://github.com/HackerNews/API), `https://hacker-news.firebaseio.com/v0/` | Public, read-only, no authentication. The official API repository currently states **“There is currently no rate limit.”** | **Deterministic HTTP/Firebase**; poll `newstories`, `topstories`, `beststories`, `askstories`, `showstories`, and `jobstories`, then fetch selected items. | Strong engineering discussion and links. There is no freshness/SLA guarantee; comment trees require multiple item requests, so cap depth/volume and back off politely even though no numeric limit is published. |
| 3 | Official project feeds (for example [GitHub Changelog RSS](https://github.blog/changelog/) and [arXiv RSS](https://info.arxiv.org/help/rss.html)) | Usually unauthenticated and free; each publisher controls cadence, retention, and limits. This is **RSS/Atom**, not a universal API contract. | **Deterministic RSS/Atom** parser. **Browser/agentic** only as an explicit fallback for a page whose publisher offers no feed. | Best precision-to-cost ratio for known projects and vendors. A feed list is required; discovery is narrow by design. Validate XML, canonical URL, publication time, and stable entry ID; never infer a rate limit that the publisher does not document. |
| 4 | [Bluesky public AppView](https://docs.bsky.app/docs/api/app-bsky-feed-get-author-feed), [public API directory](https://github.com/bluesky-social/bsky-docs/blob/main/docs/advanced-guides/api-directory.mdx) | Many read endpoints are public and do not require authentication. Current official API docs do not publish one stable numeric quota for all public endpoints; observe response status/headers and handle `429` with backoff. | **Deterministic HTTP/XRPC** for selected actors/feeds/search. The atproto firehose is deterministic WebSocket, but whole-network ingestion is a separate operational project. | Good discovery breadth, weaker provenance than a release or paper. AppView is eventually consistent. [Jetstream](https://github.com/bluesky-social/jetstream) is open-source full-network archive/streaming software, but self-hosting adds compute, bandwidth, storage, monitoring, and replay costs; do not assume a free hosted Jetstream service. |
| 5 | [arXiv API basics](https://info.arxiv.org/help/api/basics.html), [API terms](https://info.arxiv.org/help/api/tou.html), [RSS](https://info.arxiv.org/help/rss.html) | Public API/RSS with no paid key. arXiv’s terms require **no more than one request every three seconds and one connection at a time** across all machines under the operator’s control. | **Deterministic HTTP/Atom/RSS**; query `cs.AI`, `cs.SE`, `cs.LG`, and configured terms. | High-value research leads and descriptive metadata. Metadata may be stored/shared under CC0, but papers/PDFs are copyright-controlled and must not be redistributed without permission. arXiv asks products to acknowledge its data usage and says commercial projects should review its API/brand guidance. |
| 6 | [Mastodon public-data guide](https://docs.joinmastodon.org/client/public/), [timelines API](https://docs.joinmastodon.org/methods/timelines/), [syndication feeds](https://docs.joinmastodon.org/user/network/), [rate limits](https://docs.joinmastodon.org/api/rate-limits/) | Public API access is instance-configurable; some servers disable public timelines. Default documented limits are **300 calls/5 minutes per account and 300 calls/5 minutes per IP**. Account and tag pages expose RSS feeds, subject to the instance’s policy. | **Deterministic per-instance HTTP/RSS** once an instance/feed list is configured. Browser/agentic only for human review of a linked post or discovering an instance; do not scrape the federation globally. | Useful for selected maintainers/tags, but coverage, moderation, federation delay, and availability vary by instance. Store instance URL and access mode per adapter; treat a disabled public endpoint as a partial-source result, not as a retry storm. |

## Privacy, cost, and evidence rules

- Collect only public URLs, IDs, timestamps, author/actor handles, titles, excerpts, and source metadata needed for deduplication and verification. Do not collect private timelines, access tokens, or login cookies.
- Keep source content as a candidate signal, not a fact. The existing Evidence Verifier must independently open the primary source and classify the claim before `GitHub SoT Writer` persists it.
- Cache and deduplicate by `(source, canonical_id)`; honor `ETag`/`Last-Modified` where available; serialize requests per source; use bounded retries with `Retry-After`/reset headers when supplied.
- “Free API” excludes downstream costs: an always-on Bluesky firehose/Jetstream, feed archive, browser session, or local/hosted model all consume compute, bandwidth, storage, and maintenance. Start with scheduled pulls over a small allow-list; add streaming only after measured signal value justifies operations.
- Do not add Reddit to the portfolio: this review found no primary current terms/quota statement sufficient to certify the proposed automated free use.

## Regional coverage model

Every radar run uses three independent origin lanes: `korea` (한국), `japan` (일본), and `international` (해외). Origin is classified from the project, author, organization, or official-announcement context—not from platform or publication language. An English announcement from a Japanese project remains `japan`; a multinational or globally distributed community belongs to `international`.

Each discovery lane combines its Korean, Japanese, or English query seeds with the same canonical AI-engineering interest profile. Discovery emits `EMPTY_DISCOVERY` when a lane has no eligible candidate. After independent verification, Daily and Weekly reports retain all three sections and use `EMPTY` when a category has no verified signal. Neither stage forces equal quotas or admits weaker evidence merely to fill a category.

Preserve the original title and language alongside a Korean explanation, plus `primaryCategory`, supported `relatedCategories`, and an explicit `originBasis`, so the user can compare Korean, Japanese, and international evidence without losing source context.

## Observed handoff failure and remedy

A Daily Radar trial produced technically meaningful candidates but failed writer data quality because a summary-only stage handoff omitted category/provenance fields, original title/language and Korean explanation, source identity, author/project/time, verification evidence, and the observed-fact versus interpretation boundary. The remedy is `regional-signal/v1`: every scout sends a full packet array per category; verifier and judge append their own fields without dropping prior fields; the writer rejects incomplete packets with `DATA_QUALITY_FAIL` and must not create a PR or canonical write without both full-packet data quality and explicit human approval.

## Minimal manifest/routine impact

No runtime or manifest change is part of this note. For the next bounded implementation slice:

1. Preserve `x-signal-scout`’s ID and group/routine ownership during migration so existing Grok runtime relationships do not drift unexpectedly; change its display title/description only in a separately reviewed desired-state slice.
2. Replace the broad `sources: [x, web]` intent with explicit adapter entries (GitHub events/releases, HN API, configured RSS/Atom, Bluesky AppView, arXiv, and selected Mastodon instances), each carrying `authMode`, `transport`, `cursor`, `lookback`, `ratePolicy`, and `failureMode: partial_and_flag`.
3. Keep the daily routine’s 72-hour lookback, primary-link requirement, verifier/judge ordering, approval gate, and “partial on source failure” behavior. The scout may run deterministic adapters first, then use agentic reasoning only to cluster/describe candidates; it must not make adoption decisions.
4. Mark X as optional/degraded until the runtime is deliberately reconciled. The absence of X credentials should no longer prevent the free-source portfolio from producing a partial radar.

## Residual uncertainties

- GitHub event freshness, public feed URLs, and retention are service behavior rather than an end-to-end delivery guarantee; monitor observed lag and keep a last-seen cursor.
- Bluesky’s public AppView quota is endpoint/provider policy, not a single documented number. Re-check response headers and official docs before increasing poll frequency.
- Mastodon is a network of independently configured servers; an instance allow-list, terms review, and health/freshness telemetry are required for predictable coverage.
- arXiv’s API terms are explicit about request cadence and content rights, but not a promise of low-latency announcements. Use it as a research lane, not the only radar lane.

## Primary sources consulted

- [GitHub REST rate limits](https://docs.github.com/en/rest/using-the-rest-api/rate-limits-for-the-rest-api), [GitHub Events API](https://docs.github.com/en/rest/activity/events), [GitHub feeds API](https://docs.github.com/en/rest/activity/feeds)
- [Hacker News official API repository](https://github.com/HackerNews/API)
- [Bluesky public endpoint documentation](https://docs.bsky.app/docs/api/app-bsky-feed-get-author-feed), [Bluesky API directory](https://github.com/bluesky-social/bsky-docs/blob/main/docs/advanced-guides/api-directory.mdx), [atproto sync spec](https://atproto.com/specs/sync), [Jetstream source repository](https://github.com/bluesky-social/jetstream)
- [Mastodon public data](https://docs.joinmastodon.org/client/public/), [Mastodon syndication feeds](https://docs.joinmastodon.org/user/network/), [Mastodon rate limits](https://docs.joinmastodon.org/api/rate-limits/)
- [arXiv API basics](https://info.arxiv.org/help/api/basics.html), [arXiv API terms](https://info.arxiv.org/help/api/tou.html), [arXiv RSS](https://info.arxiv.org/help/rss.html)
