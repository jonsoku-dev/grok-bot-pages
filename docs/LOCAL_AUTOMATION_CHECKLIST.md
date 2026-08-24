---
{}
---

# Local Grok Desktop Automation Checklist

> Use this checklist during the Codex App rollout.

# Local Grok Desktop Automation Checklist

Use this checklist during the Codex App rollout.

## Repository
- [x] `gh auth status` succeeds.
- [x] Repository is `jonsoku-dev/grok-bot` and private.
- [x] Working tree state is understood before changes.
- [x] `npm install` succeeds.
- [x] `npm run validate` passes.
- [x] `npm run botctl -- list` shows the expected roster.

## Local Grok Bot app
- [x] Application bundle/name is observed, not assumed.
- [x] User is signed in.
- [x] Local Computer Execution permission is adequate for the requested task.
- [x] Current app version is recorded.
- [x] Non-mutating UI observation is complete.
- [x] `runtime/ui-contract/grok-desktop.yaml` exists and contains observed labels only.

## Disposable test Bot
- [x] Test Bot manifest exists.
- [x] Plan is `MISSING` before creation.
- [x] Human approves creation.
- [x] Apply request/approval is audited.
- [x] Computer Use creates the Bot.
- [x] Bot profile is reopened after Save.
- [x] Name/Title/Description match exactly.
- [x] Runtime snapshot is written.
- [x] Apply/verify/snapshot events are audited.
- [x] Subsequent plan is `SYNCED`.

## Drift update test
- [x] Manifest is intentionally changed.
- [x] Plan becomes `DRIFTED`.
- [x] Exact field-level change is shown before mutation.
- [x] Human approves update.
- [x] Only planned managed fields are changed.
- [x] Runtime is reopened and verified.
- [x] Snapshot/audit are updated.
- [x] Plan returns `SYNCED`.

## Production rollout
- [x] `x-signal-scout` reconciles successfully.
- [x] Group synchronization is tested separately.
- [x] Routine synchronization is tested separately.
- [x] No deletion automation exists.
- [x] Ambiguity causes safe stop.
- [x] Auth/2FA/CAPTCHA always uses human takeover.
