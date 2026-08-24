---
{}
---

# Obsidian and Drive Workflow

> Use this repository directly as a plain-Markdown vault. Begin at
[`knowledge/index.md`](../knowledge), keep canonical notes in Git, and
use ordinary Markdown links. Do not commit `.obsidian/`, workspace state,
plugin state, or device-specific settings.

# Obsidian and Drive Workflow

## Obsidian-compatible vault

Use this repository directly as a plain-Markdown vault. Begin at
[`knowledge/index.md`](../knowledge), keep canonical notes in Git, and
use ordinary Markdown links. Do not commit `.obsidian/`, workspace state,
plugin state, or device-specific settings.

## Delivery flow

```text
approved current Git SoT
  -> GitHub Reader canonical-content/v1
  -> Korean Slack preview or Gmail draft
  -> explicit human approval
  -> separately authorized send
```

Routines stop at preview/draft. They never send. The reader rejects stale,
unapproved, pathless, hashless, or conversation-only input.

## Drive share layer

Drive is an approved share layer, not the canonical source. Prepare the local
[`drive-export/v1`](../knowledge/drive-export/v1) package from the
approved canonical packet. This repository contains no Drive API integration,
upload, share, or external-write command.

## Company use

Use the [company template](../templates/company) only in a
company-controlled environment. Keep company SoT, accounts, destinations,
internal data, and identifiers out of this personal repository.
