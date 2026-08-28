---
{}
---

# Local Grok Desktop Automation Checklist

> Use this checklist during Codex App or Grok Desktop reconciliation. GitHub Actions and required status checks are not part of this procedure.

# Local Grok Desktop Automation Checklist

Use this checklist during Codex App or Grok Desktop reconciliation. GitHub Actions and required status checks are not part of this procedure.

## Repository and validation

- [ ] Repository is exactly `jonsoku-dev/grok-bot` and the intended commit SHA is recorded.
- [ ] Working tree or connector target state is understood before changes.
- [ ] Dependencies are reproducible; run `npm ci` on a fresh checkout.
- [ ] The correct validation profile is selected from `docs/LOCAL_VALIDATION.md`.
- [ ] Run `npm run verify:runtime` for Bot, Routine, policy, schema, skill, agent-eval, or Miyamae runtime changes.
- [ ] Run `npm run verify:local` for complete repository validation.
- [ ] On a bootstrapped Grok VM, run `npm run verify:vm` when live runtime behavior is in scope.
- [ ] Record the exact command, exit status, environment, timestamp, and Git commit SHA.
- [ ] Any check that could not execute is marked `UNVERIFIED`; it is not inferred as passed.
- [ ] Do not create, re-enable, retry, or poll a GitHub Actions validation workflow.
- [ ] `npm run botctl -- list` shows the expected roster.
- [ ] `npm run botctl -- plan` or the scoped plan contains no unapproved delete/disable action.

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

## Local executor

- [ ] `npm run local:executor:dry-run` produces a schema-valid receipt with no external writes.
- [ ] `tooling/install-local-publication-fallback.sh` has been reviewed before installation; do not install it from a Bot.
- [ ] The launchd jobs use existing local Git credentials only and never print them.
- [ ] Every npm/test/build child runs with `env -i`, an isolated temporary `HOME`, and no inherited SSH or GitHub credentials.
- [ ] A PR validation receipt is committed in canonical `main` history and binds the exact unmerged PR head SHA; it does not claim impossible ancestry from that PR head.
- [ ] A publication receipt commit descends from its `main` publication-input subject; it is never compared for equality with its own post-receipt main HEAD.
- [ ] The 5-minute PR validator skips heads already merged or covered by a successful exact-subject receipt and never merges a PR itself.
- [ ] A Git pull-ref scan failure is an error receipt, never an empty-result receipt; closed-unmerged refs may be revalidated but are never merged by the local host.
- [ ] The publisher writes a stale-recoverable pending marker, waits up to 30 minutes for an active validator, and validator children yield before starting another head.

## Completion evidence

Before reporting a reconciliation complete, preserve:

- the exact source commit SHA;
- the selected local/VM validation result;
- the approved plan and plan hash;
- exact post-save UI re-read evidence;
- runtime snapshots for all managed entities;
- correlated audit and UI-observation records;
- a final `SYNCED` plan;
- explicit degraded or `UNVERIFIED` items, if any.
