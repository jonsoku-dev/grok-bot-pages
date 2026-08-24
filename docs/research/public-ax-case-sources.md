---
{}
---

# Public AX Watch case sources

> Research date: 2026-08-23. This note defines a free, public-source discovery lane for concrete enterprise or public-service AI transformation cases. It does not assert that any individual case is verified: AX Case Scout must emit `evidenceStatus: UNVERIFIED`, preserve the primary URL, and leave independent verification to a later Evidence Verifier handoff.

# Public AX Watch case sources

Research date: 2026-08-23. This note defines a free, public-source discovery lane for concrete enterprise or public-service AI transformation cases. It does not assert that any individual case is verified: AX Case Scout must emit `evidenceStatus: UNVERIFIED`, preserve the primary URL, and leave independent verification to a later Evidence Verifier handoff.

## What qualifies as a case

The minimum evidence is a named organization or public body, a public primary URL, and a changed workflow that can be described as before/after. The packet must also say what humans still do and capture at least one governance control, evaluation method, metric, failure, or limitation. A casebook may be self-reported and still be useful discovery, but it remains `UNVERIFIED` until the verifier checks the source and contradictions.

Reject a CEO vision, future roadmap, generic “AI-powered” claim, unnamed customer, unsupported metric, or vendor-only success story with no implementer-owned source. Do not infer Korea/Japan/international from language alone. Sanitize personal, confidential, customer-identifying, and security-sensitive details.

## Regional public source types

### Korea (`korea` / 한국)

- [NIA: AI Government Service Casebook (2026)](https://nia.or.kr/site/nia_kor/ex/bbs/View.do?bcIdx=29161&cbIdx=37989&parentSeq=29161) is an official Ministry of the Interior and Safety/NIA publication. The listing says it selected 16 public AI service cases across six fields and includes implementation trials, technical specifications, and field difficulties. It is a strong source for public-service workflow, governance, evaluation, and limitations; it is not automatically an enterprise-private case.
- [NIA: Public-sector AI adoption/use casebook and data-analysis guide (2025)](https://nia.or.kr/site/nia_kor/ex/bbs/View.do?bcIdx=28925&cbIdx=27974&parentSeq=28925) is an official casebook intended to support public institutions’ AI adoption and data-driven administration. Use the case documents for concrete workflows, not the announcement headline alone.
- [NIA: Public AI service demonstration casebook and overseas inventory](https://www.nia.or.kr/site/nia_kor/ex/bbs/View.do?bcIdx=27985&cbIdx=99953) identifies a public AI demonstration collection and states that it contains 110 cases. Treat the inventory as discovery; retain only entries with enough primary detail to fill every AX packet field.

### Japan (`japan` / 日本)

- [METI DX Selection](https://www.meti.go.jp/policy/it_policy/investment/dx-selection/dx-selection.html) publishes selected-company reports for 2022–2026. Selection is useful discovery for named organizations and implementation context, but the scout must extract the actual workflow, human responsibility, measures, and limitations from the linked report.
- [METI DX Selection 2025 report](https://www.meti.go.jp/meti_lib/report/2024FY/000292.pdf) contains concrete company initiatives, including AI analysis of production data, generated advice/work instructions, traceability, and technical-transfer efforts. Keep the report’s original Japanese title and distinguish reported outcomes from independently verified metrics.
- [METI case-study teaching materials for digital talent](https://www.meti.go.jp/press/2024/04/20240423002/20240423002.html) describes data-backed case-study materials based on actual company AI implementation and data-driven transformation. Use the attached public materials when they expose the before/after workflow and evaluation context; reject purely educational or aspirational descriptions.

### International (`international` / 海外)

- [GOV.UK: UK bank AI compliance case study](https://www.gov.uk/government/case-studies/how-a-uk-based-bank-used-ai-to-increase-operational-efficiency) is an official Government Digital Service/Office for AI case study. It identifies the prior sampling-heavy compliance workflow, the AI extraction workflow, human review context, and reported impacts such as 100% case coverage and an 80% reduction in process duration. Treat the outcomes as reported case evidence until independently verified.
- [GOV.UK: supporting case studies for AI upskilling](https://www.gov.uk/government/publications/skills-for-ai-what-works-for-ai-upskilling-in-the-uk/supporting-case-studies-for-ai-upskilling-in-the-uk) documents named organizations, capability-building workflows, governance-linked training, and reported impact. The page explicitly says cases were validated with participating organizations but outcomes were not independently audited; preserve that limitation in `failuresLimitations` and keep `UNVERIFIED`.
- [Canada ATSSC AI Transformation Strategy](https://www.canada.ca/en/administrative-tribunals-support-service/reports/ai-at-atssc.html) is a public institutional strategy describing AI use, governance, human-centric principles, pilots, and measurement intent. It is eligible for a case only where the implementation is concrete; strategy-only passages must be rejected as vision.

## Free discovery adapters

The repository’s [public source policy](../../config/sources.yaml) already marks GitHub public activity/releases, official RSS/Atom, Hacker News, Bluesky public AppView, arXiv Atom, and Mastodon public API/RSS as public, paid-API-free, read-only sources. Use them to find candidate URLs, then verify against the named organization’s or public body’s primary document. X, paid APIs, private feeds, and whole-network Bluesky Jetstream remain excluded.

- **Deterministic:** official RSS/Atom, GitHub public endpoints, Hacker News API, Bluesky public AppView, arXiv Atom, and a configured Mastodon instance/API.
- **Browser fallback:** opening a linked public casebook/report when the structured adapter cannot expose its content. Stop at login, paywall, CAPTCHA, or ambiguous access; return partial results.
- **Agentic work:** classify the changed workflow, separate reported facts from interpretation, reject weak cases, preserve original metadata, and package `ax-case/v1`. It must not upgrade evidence status, recommend adoption, or write canonical knowledge.

## `ax-case/v1` contract

Every candidate is grouped into exactly `korea`, `japan`, or `international` and contains, in this order:

```text
company, region, originalLanguage, originalTitle, primaryUrl,
previousWorkflow, aiEnabledWorkflow, humanResponsibility, governance,
evaluation, metrics, failuresLimitations, reusablePattern, evidenceStatus
```

`evidenceStatus` is always `UNVERIFIED` at discovery. Preserve all fields and the primary URL for an optional Evidence Verifier handoff. If an exact adapter for this packet is unavailable, retain the packet unchanged and flag the handoff as pending; do not add Evidence Verifier to the AX discovery group merely to imply verification.

## Residual uncertainties

- Official casebooks and company-reported outcomes are primary sources for what was claimed or implemented, not independent audits; the packet must retain source warnings.
- Government collections may emphasize public-sector service delivery rather than private enterprise operating models; classify the organization accurately and reject strategy-only entries.
- RSS/API discovery is free but not exhaustive. A missing feed or unavailable page produces `partial_and_flag`, not a reason to lower the acceptance bar.
