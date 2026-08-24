---
{}
---

# Manual Delivery Live Validation Receipt — 2026-08-23

> Two approved current Git SoT reports were validated as `canonical-content/v1` packets at commit `c2d46a4f6d0df0a3deb3c8c49ea53a6aa22f3531` and manually delivered through the connected personal accounts.

# Manual Delivery Live Validation Receipt — 2026-08-23

## Outcome

Two approved current Git SoT reports were validated as `canonical-content/v1` packets at commit `c2d46a4f6d0df0a3deb3c8c49ea53a6aa22f3531` and manually delivered through the connected personal accounts.

- Slack: `reports/daily/latest.md`, SHA-256 `b682301a6b6b304d139b9d7a7b22f56c08e3a3d1d9da5c215775a4de77367a4b`.
- Gmail: `reports/weekly/latest.md`, SHA-256 `cd72800ccc275894d8de2724fd034f79b8bdb88faf89aa49fafd501f73d917a6`.

GitHub Reader re-read the exact commit through the connected GitHub plugin, confirmed `status: approved`, exact content hashes, current HEAD, and the required `title`, `action`, `evidence`, and `sourceLinks` frontmatter. It then sent the daily packet to Slack Publisher and the weekly packet to Gmail Publisher.

Slack Publisher created a Korean preview and sent it once to the connected user's self-DM after explicit approval. Gmail Publisher created a Korean draft and sent that exact draft once from the connected account to itself after explicit approval.

No shared Slack channel, Slack thread, additional Gmail recipient, Drive destination, company account, or third-party destination was used. Personal email addresses, Slack user IDs, channel IDs, message IDs, and workspace identifiers are intentionally omitted from repository evidence.

## SoT links

- [Knowledge index](../knowledge)
- [Approved daily report](../reports/daily/latest)
- [Approved weekly report](../reports/weekly/latest)
- [AX regional source receipt](ROLLOUT_RECEIPT_AX_REGIONAL_2026-08-23.md)

## Safety behavior

Both publishers first stopped at preview/draft because the default policy denies automatic sending. Actual send happened only after the user explicitly requested the manual delivery test and the destination was narrowed to the connected account's self target. The automatic routines remain preview/draft-only.
