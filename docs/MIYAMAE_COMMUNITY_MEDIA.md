---
{}
---

# Miyamae Community Media

> 宮前区で起きている、住民の生活に関係する共有可能な情報を、良いこと・悪いこと・楽しいこと・悲しいことを恣意的に選別せず、検証可能な形で届ける。

# Miyamae Community Media

## Mission

宮前区で起きている、住民の生活に関係する共有可能な情報を、良いこと・悪いこと・楽しいこと・悲しいことを恣意的に選別せず、検証可能な形で届ける。

**Residents should not need to know where to look. The account should know where to look.**

This is not an official Kawasaki City or Miyamae Ward account. It is an independent resident-operated local information account assisted by automation/AI.

## Product thesis

Do not create a separate community product at first. The X/Threads account itself is the town square:

- publishing creates discovery;
- replies and mentions create submissions;
- polls/questions create conversation;
- corrections create accountability;
- recurring local contributors create community;
- useful archives create trust.

The system should minimize the founder's posting burden. Humans own policy, high-risk judgment, corrections, and exceptional cases. Automation owns discovery, deduplication, extraction, scheduling, drafting, and low-risk publishing when explicitly enabled.

## Coverage: "everything" means broad relevance, not surveillance

Track any publicly shareable information materially relevant to Miyamae residents:

- emergency/disaster/weather/earthquake/fire/public safety
- transport, roads, closures, construction, parking, buses and railway disruption
- ward/city administration, benefits, deadlines, elections and public meetings
- schools, childcare, parenting, libraries and youth activities
- health/public-health notices and facility changes
- elderly/disability/community support information
- events, festivals, concerts, sports, workshops and volunteer activity
- parks, nature, seasonal changes and local environment
- restaurant/shop openings, closures, relocations, sales and notable changes
- supermarkets, farmers, direct-sale stands, markets and food trucks
- housing/development/redevelopment and material neighborhood construction
- waste collection, utilities, outages and everyday-life notices
- lost/found or community requests only when safe and privacy-preserving
- local achievements, people, clubs and positive stories
- accidents/incidents and sad news when verified and genuinely locally relevant
- resident observations, questions, rumors requiring verification, and corrections
- useful nearby information outside the ward when it materially affects ward residents

Never interpret "everything" as permission to publish private addresses, doxxing, medical details, minors' identifying information, unverified accusations, graphic material, stalking-enabling location data, or rumor presented as fact.

## Editorial constitution

1. **Public interest over engagement.** Never suppress bad/sad news merely because it hurts the feed's mood.
2. **Evidence before assertion.** Separate confirmed fact, official claim, eyewitness report, inference, and rumor.
3. **No rumor laundering.** A resident post is a lead, not evidence by itself.
4. **Source visible.** Material factual posts should link or name the primary source whenever feasible.
5. **Time visible.** Breaking information must say when it was observed/updated.
6. **Corrections are first-class content.** Correct visibly; never silently rewrite history where a correction matters.
7. **Proportionality.** A minor local incident must not be sensationalized into fear.
8. **Privacy by default.** Protect victims, minors, private residents and vulnerable people.
9. **No automated blame.** Crime, misconduct, controversy, politics, death/injury, allegations and identifiable private persons require human review.
10. **No pay-to-hide.** Commercial relationships must never determine whether negative factual information is covered.
11. **Label ads/sponsorships.** Editorial and commercial content stay distinguishable.
12. **Independent identity.** Never imply affiliation with 宮前区役所, 川崎市, police, fire department or another authority.

## Geographic model

Primary scope: 神奈川県川崎市宮前区.

Maintain neighborhood/station tags including at minimum: 宮前平, 宮崎台, 鷺沼, 犬蔵, 土橋, 有馬, 東有馬, 野川, 西野川, 南野川, 梶ケ谷, 馬絹, 神木, 神木本町, 平, 初山, 菅生, 菅生ケ丘, 水沢, 潮見台, 五所塚, けやき平, 白幡台.

Adjacent-area stories may be published with an `OUTSIDE_WARD_RELEVANT` label when they affect Miyamae residents.

## Information states

Every candidate is one of:

- `LEAD` — discovered but not verified
- `VERIFYING` — evidence collection in progress
- `CONFIRMED` — sufficient evidence
- `OFFICIAL` — primary authority is the source
- `DISPUTED` — credible sources conflict
- `CORRECTED` — a published fact required correction
- `RETRACTED` — publication should no longer be relied upon
- `EXPIRED` — event/notice no longer current

Do not collapse these states into a single confidence number.

## Risk classes and publishing

### R0 — automatic candidate / eventually auto-publish
Official event announcements, facility hours/closures, public administrative notices, weather reminders, verified store openings, scheduled transport works, recurring summaries.

### R1 — automatic after corroboration
Commercial changes, construction, road conditions, non-sensitive resident tips, local observations. Prefer primary source or two independent credible sources.

### R2 — human review required
Accidents, fires with uncertain impact, public safety incidents, politically contentious local matters, disputes, complaints about businesses, potentially reputation-affecting claims.

### R3 — human-only / often do not publish
Deaths/injuries before authoritative confirmation, alleged crimes naming people, private-person accusations, minors, victim identities, precise vulnerable-person locations, graphic content, personal medical information.

Emergency information from an authoritative primary source may bypass normal batching, but must preserve attribution and timestamp.

## Source hierarchy

Prefer in this order when applicable:

1. primary public authority / operator / business / organizer
2. official public datasets and alerts
3. direct first-party statements
4. established local/news reporting
5. multiple independent resident observations
6. single resident/social post (lead only)

Initial source families to inventory:

- 川崎市 / 宮前区 official pages and press releases
- ward disaster/emergency information
- police/fire/public safety official information where publicly available
- Japan Meteorological Agency and disaster feeds
- railway/bus/operator service information
- road/traffic/public works notices
- schools, libraries, civic halls, sports/community facilities
- event organizers, neighborhood associations and civic groups
- businesses and shopping facilities
- public social accounts/RSS/feeds/search discovery
- resident mentions/replies/submissions

## Account behavior

The account should sound like a useful Miyamae resident, not a press-release bot.

- Japanese is the primary public language.
- concise, factual, neighborly, non-bureaucratic
- avoid AI filler and excessive hashtags
- distinguish urgency visually: `【速報】`, `【続報】`, `【注意】`, `【イベント】`, `【開店】`, `【閉店】`, `【行政】`, `【交通】`, `【募集】`, `【訂正】`
- ask questions naturally when local knowledge is useful
- thank useful contributors without exposing identities unnecessarily
- never manufacture personal experiences ("行ってきた", "見た") unless the human operator actually supplied them
- never fake consensus ("宮前区民みんなが...")

## Community loop

The community exists in the account rather than a separate forum initially.

1. Publish useful information consistently.
2. Invite replies: `この件、現地の状況をご存じの方いますか？`
3. Convert replies/mentions into leads.
4. Verify before amplifying.
5. Credit contributors when they consent / attribution is already intentionally public.
6. Ask low-friction local questions and polls.
7. Summarize community answers without pretending the sample represents all residents.
8. Follow up old stories: opening dates, construction completion, event results, corrections.
9. Recognize recurring helpful contributors organically; do not create an elite gatekeeping layer.

## Fresh + reserve + trend model

The account should never depend on one stream of breaking news.

### Fresh lane

Breaking/current local utility always wins: disaster/weather, transport, city/ward notices, events, openings/closures, construction and facility changes.

### Reserve lane

Maintain a verified, expiring reserve inventory so quiet days do not force low-value posting. Target roughly 80 READY items, warn below 30, and keep about three weeks of useful coverage. Every reserve item must retain source provenance, `verifiedAt`, `recheckAt`/`expiresAt`, seasonality and a revalidation rule.

Good reserve categories include parks, walks, libraries, public facilities, local history, disaster preparedness, recycling/waste, parenting resources, markets/farms, seasonal nature and transit tips.

Never reserve accidents, crime, death, emergency or controversy as filler.

### Trend lane

Observe current X/Threads/Google trend signals separately from factual verification. Trends can change timing, framing, questions or which verified reserve item is useful now; trends never count as evidence and never convert a LEAD into CONFIRMED.

Examples of natural joins:

- heat trend + verified local cooling/park/shade information
- school-holiday conversation + verified family events
- cherry-blossom trend + verified Miyamae park/seasonal information
- food trend + already verified local shops serving that item
- commute trend + useful local rail/bus information

Do not trend-jack tragedy, crime, personal controversy or unrelated celebrity news.

## Cadence

Event-driven:
- emergencies and high-utility changes: publish as soon as verification/risk policy allows
- meaningful openings/closures/transport/admin changes: publish when confirmed

Collection/drafting:
- every ~20 minutes: fresh Miyamae sweep
- minute 10/40 each hour: trend sweep
- 05:15 daily: reserve replenish/revalidation

Batch publication candidates:
- 07:00 `おはよう宮前区`: weather + transport + today's important notices/events
- 12:00 optional lunch/local-life slot when enough signal exists
- 18:00 `今日の宮前区`: notable developments + tomorrow reminders
- Friday evening: `今週末の宮前区`
- Sunday evening: week recap + upcoming deadlines

Do not post to satisfy a quota. Silence is better than low-value filler; reserve exists to increase useful optionality, not to mandate posting.

## Initial success metrics

Avoid optimizing only impressions. Track:

- verified useful items published
- median detection-to-publication latency by risk class
- correction/retraction rate
- primary-source coverage rate
- duplicate rate
- reserve READY inventory, stale rate and revalidation success
- trend joins that led to useful replies/saves vs forced joins skipped
- resident submissions received
- submissions that become verified posts
- meaningful reply conversations
- repeat contributors
- saves/bookmarks and link clicks where available
- unanswered resident questions

## Current public signal

As of 2026-08-27, Miyamae Ward itself is recruiting `みやまえPRサポーター` to encourage residents to publish local attractions through SNS, and the ward continuously publishes disaster, parenting, event and community information. This validates that there is substantial source material, but this project is deliberately broader than PR: it covers useful negative, neutral, positive, serious and playful information under the same evidence policy.

## Non-goals for v1

- standalone community app/forum
- anonymous accusation board
- citizen surveillance
- automated crime blotter without editorial review
- engagement bait
- scraping sources in violation of terms/access controls
- pretending AI output is eyewitness reporting
- monetization before trust

## Rollout

### Phase 0 — SoT and dry run
Build source registry, taxonomy, prompts, safety policy, candidate schema, sample posts and dry-run reports. No autonomous external write.

### Phase 1 — assisted account
System discovers/drafts; operator approves sensitive/new classes. Start conversations manually/assisted.

### Phase 2 — trusted automation
Allow R0 and selected R1 classes to auto-publish after measured precision is high. R2/R3 remain gated.

### Phase 3 — community flywheel
Mentions/replies become structured leads, follow-up threads become routine, recurring local contributors emerge naturally.

### Phase 4 — optional archive/map
Only after the social account demonstrates demand, consider a searchable website/map/archive. The social account remains the primary community surface.

See also [`MIYAMAE_COLLECTION_ARCHITECTURE.md`](MIYAMAE_COLLECTION_ARCHITECTURE.md) for the free-first collection, reserve inventory and trend-bridge implementation architecture.
