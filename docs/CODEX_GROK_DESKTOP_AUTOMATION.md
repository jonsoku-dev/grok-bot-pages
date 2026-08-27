---
{}
---

# Codex App → Grok Bot Desktop Automation

> This document is the implementation handoff for Codex App. The goal is to use **Codex Computer Use on the local Mac** to read the canonical desired state from this repository and create/update Grok Bots in the locally installed Grok Bot desktop app.

# Codex App → Grok Bot Desktop Automation

## Purpose

This document is the implementation handoff for Codex App. The goal is to use **Codex Computer Use on the local Mac** to read the canonical desired state from this repository and create/update Grok Bots in the locally installed Grok Bot desktop app.

Canonical access page: https://x.ai/bot

The repository is authoritative. The Grok Bot desktop app is runtime state only.

## Current product facts to assume

As of 2026-08-23, official Grok Bot documentation states:

- Grok Bot has a macOS/Windows desktop app.
- Bots can use apps and websites through computer use.
- Local-computer execution is a separate permission controlled in `Settings → General → Agent → Execution on Local Computer`.
- Bots can have profiles, group chats, skills, and routines.
- The product may change UI layout over time, so automation must not depend on fragile screen coordinates.

This repository does **not** assume an official Bot configuration API exists. UI automation is an adapter and must be replaceable.

---

# Non-negotiable invariants

1. **GitHub is desired state. Grok is runtime state.**
2. Never infer desired values from existing Grok UI state.
3. Never change a Grok Bot without a generated plan.
4. Never auto-delete a Grok Bot.
5. Apply only fields represented in the manifest/export contract.
6. After every UI mutation, reopen/re-read the Bot and verify exact values.
7. If the UI is ambiguous, missing, renamed, blocked by auth, or confidence is low, stop and record failure. Never guess.
8. Every plan/apply/verify/snapshot operation must produce an audit event.
9. Do not log passwords, one-time codes, access tokens, cookies, or sensitive screen contents.
10. Start with one disposable/test Bot before touching the production roster.

---

# Local prerequisites Codex must check

From the repository root:

```bash
gh auth status
gh repo view jonsoku-dev/grok-bot --json nameWithOwner,visibility,defaultBranchRef
git status --short
git log --oneline -10
node --version
npm --version
```

Then verify the Grok Bot desktop application exists locally. On macOS, use safe inspection commands such as:

```bash
mdfind 'kMDItemKind == Application' | grep -i 'Grok Bot' || true
ls /Applications | grep -i 'Grok' || true
```

Do not assume the application bundle name until observed.

If local computer control requires a setting change, ask the user to explicitly allow it. Do not weaken local-computer execution policy silently.

---

# Repository commands

Install and validate:

```bash
npm install
npm run validate
npm run botctl -- list
npm run botctl -- export x-signal-scout
npm run botctl -- plan x-signal-scout
```

The `export` output is the exact handoff package for the Grok UI. It includes:

- canonical Bot ID
- Name
- Title
- Description
- Group membership
- desired summary SHA-256
- control-plane metadata not necessarily entered into the UI

Do not parse human prose from README when the manifest/export gives a canonical field.

---

# Phase 0 — Observe the UI, do not mutate

Before implementing automation, Codex must inspect the installed Grok Bot desktop app manually through Computer Use and create an **observed UI contract**.

Open the application and determine, without making changes:

1. how the Bot list/sidebar is opened;
2. how an existing Bot profile is opened;
3. how a new Bot is created;
4. visible labels for Name, Title, Description, Avatar, or other profile fields;
5. how Save/Done is represented;
6. how Group Chat creation/member editing works;
7. how Routine creation/editing works;
8. whether any fields have character limits or validation;
9. whether profile editing occurs in a modal, page, side panel, context menu, or conversation details screen;
10. what stable accessibility labels/text are exposed to Computer Use.

Record observations under:

```text
runtime/ui-contract/grok-desktop.yaml
```

Suggested structure:

```yaml
observedAt: 2026-08-23T00:00:00+09:00
app:
  platform: macos
  name: Grok Bot
  version: observed-version
navigation:
  createBot:
    stableText: "..."
  editProfile:
    stableText: "..."
fields:
  name:
    label: "..."
  title:
    label: "..."
  description:
    label: "..."
actions:
  save:
    label: "..."
confidence: high
```

Do not invent any of these values. They must be observations from the local app.

Commit the observed contract separately before implementing mutation logic.

---

# Phase 1 — Dry-run test Bot

Create a disposable manifest first, for example:

```text
an untracked temporary test manifest
```

Use a clearly disposable name such as `Codex Sync Test`. Its purpose is only to validate automation.

Required dry-run workflow:

```text
manifest
  ↓
botctl validate
  ↓
botctl export <temporary-test-bot>
  ↓
botctl plan <temporary-test-bot>
  ↓
MISSING
  ↓
explicit human approval
  ↓
Computer Use create
  ↓
reopen Bot profile
  ↓
exact verify
  ↓
runtime snapshot
  ↓
botctl plan
  ↓
SYNCED
```

Do not automate the real roster until this completes successfully at least twice, including one update/drift scenario.

---

# Computer Use behavior contract

## Navigation strategy

Preferred selection order:

1. semantic/accessibility label;
2. visible text;
3. nearby stable text plus relative location;
4. visual icon plus verified surrounding context;
5. absolute coordinate only as a last-resort temporary fallback.

Never build the primary implementation around hard-coded screen coordinates.

After every navigation step, confirm expected state before proceeding.

Example logic:

```text
open Grok Bot
→ confirm expected app title/sidebar
→ search/select Bot by exact Name
→ confirm selected Bot identity
→ open profile/details
→ confirm expected field labels
→ only then type values
```

## Text entry

For each managed field:

1. focus the exact field;
2. select all existing content;
3. replace with canonical value from `botctl export`;
4. read back the field if Computer Use supports it;
5. do not normalize punctuation or whitespace unless the UI itself forces it.

Description must be treated as opaque canonical text. Codex must not “improve” or rewrite it during apply.

## Save

Before Save:

- confirm Name matches expected Bot;
- confirm this is not a different existing Bot with a similar name;
- confirm all planned changes only.

After Save:

- wait for visible success/state transition;
- close/reopen profile;
- inspect exact field values again.

Do not mark apply successful merely because a Save button was clicked.

---

# Create algorithm

For a Bot classified `MISSING`:

1. generate and persist `plan.generate` audit event;
2. print/show exact change plan to the user;
3. require explicit approval;
4. persist `apply.approve` audit event;
5. open Grok Bot desktop app;
6. navigate to Create Bot;
7. populate only mapped fields;
8. save;
9. locate the new Bot by exact desired Name;
10. reopen its profile;
11. read Name/Title/Description;
12. verify exact equality to desired state;
13. write runtime snapshot;
14. append `apply.execute`, `verify.execute`, and `snapshot.write` audit events;
15. run `botctl plan <id>` and require `SYNCED`.

If exact verification fails, classify as `DRIFTED`, log failure, and stop. Do not repeatedly overwrite the UI in a loop.

---

# Update algorithm

For `DRIFTED`:

1. identify exact field-level differences before launching the app;
2. present the planned fields only;
3. require approval;
4. locate the Bot by exact runtime identity/name;
5. open profile;
6. verify this is the intended Bot;
7. mutate only changed managed fields;
8. save;
9. reopen and verify all managed fields;
10. snapshot and audit;
11. require subsequent plan = `SYNCED`.

If an unmanaged field exists in Grok UI, leave it unchanged unless this repository explicitly adopts it into the manifest contract.

---

# Existing duplicate-name handling

If Grok contains multiple Bots whose visible name matches the desired Name:

- DO NOT choose one arbitrarily;
- classify the operation as ambiguous;
- emit failed `apply.execute` or policy event;
- require human resolution.

Long term, store a stable runtime identifier in runtime snapshots if the Grok UI exposes one.

---

# Runtime snapshot contract

After successful verification, create:

```text
runtime/grok/bots/<bot-id>.yaml
```

Required shape:

```yaml
apiVersion: agentops/v1alpha1
kind: RuntimeSnapshot
metadata:
  id: x-signal-scout
  correlationId: reconcile-20260823-x-signal-scout-a81f
spec:
  observedAt: 2026-08-23T12:00:00+09:00
  sourceCommit: <git-sha>
  desiredVersion: 0.1.0
  desiredSummaryHash: <sha256-from-botctl-export>
  observed:
    id: x-signal-scout
    name: X Signal Scout
    title: Emerging AI Engineering Signal Scout
    description: <exact-re-read-description>
    groups:
      - ai-engineering-radar
    routines:
      - daily-ai-radar
    managed:
      provider: grok
      mode: managed
      autoApply: false
      deletionPolicy: retain
    approval:
      externalWrite: deny
      sotWrite: review
  verification:
    status: verified
    method: codex-app-built-in-computer-use
    appVersion: <observed-version>
    auditEventId: <verify.execute-event-uuid>
```

`botctl snapshot` accepts this document only when the source commit resolves in the repository, the desired hash and exact observed fields still match, and the same correlation ID has an ordered plan/request/human-approval/apply/verify audit chain plus a successful UI verification observation. Avoid storing sensitive screenshots or unrelated app data.

---

# Computer Use learning loop

Every reusable UI interaction should follow:

```text
observe -> append sanitized UI observation -> summarize repeated evidence -> promote or stale the UI contract -> reuse on the next run
```

Store only bounded interaction facts through `botctl ui-observe`: app version, locale, surface, action, targeting strategy, accessibility role/label, outcome, contract status, and safe counts/hashes. Never store raw screenshots, screen dumps, prompts, account/plugin inventories, coordinates, or credentials.

One successful correlation is only `candidate`. `botctl ui-observe-summary` recommends `stable` only after the same pattern succeeds under at least two distinct correlation IDs. A failure or UI change should be logged as `failure`/`ambiguous` and the observed contract should be marked `stale` until it is re-observed.

---

# Group synchronization

Group manifests live in `groups/*.yaml`.

Treat Group synchronization as a separate resource reconciliation, not an incidental side effect of Bot creation.

For each Group:

1. validate every member ID exists as desired Bot;
2. confirm every required Bot is already runtime `SYNCED`;
3. generate group plan;
4. create Group if missing or update membership if drifted;
5. never remove a member automatically if the UI state is ambiguous;
6. verify final exact membership;
7. snapshot/audit.

Because Grok group UI may evolve, observe and document the current local Group creation flow before implementing mutation.

---

# Routine synchronization

Routine manifests live in `routines/*.yaml`.

Do not immediately automate all schedules. First confirm the current Grok UI supports the desired routine concepts and how timezone/schedule are represented.

For scheduled routines verify explicitly:

- owner Bot;
- schedule/time;
- timezone;
- enabled/paused state;
- input/instruction text;
- approval behavior if surfaced.

Never silently convert a cron value into a different timezone. Repository schedule semantics are Asia/Tokyo unless manifest says otherwise.

---

# Approval model

During initial rollout:

```text
validate: automatic
plan: automatic
create/update UI mutation: explicit user approval
verify: automatic
snapshot: automatic after verified apply
delete: prohibited
publish: separate policy, review by default
```

No blanket “approve all future Grok mutations” during the stabilization phase.

---

# Audit integration

Before each state-changing step use:

```bash
npm run botctl -- audit \
  --action apply.request \
  --kind bot \
  --id x-signal-scout \
  --correlation-id reconcile-20260823-x-signal-scout-a81f \
  --source-commit "$(git rev-parse HEAD)" \
  --result planned \
  --actor-type codex \
  --actor-id codex-app \
  --changes '{"status":"MISSING","fields":["name","title","description"],"desiredSummaryHash":"<sha256>"}'
```

After approval:

```bash
npm run botctl -- audit \
  --action apply.approve \
  --kind bot \
  --id x-signal-scout \
  --correlation-id reconcile-20260823-x-signal-scout-a81f \
  --source-commit "$(git rev-parse HEAD)" \
  --result success \
  --actor-type human \
  --actor-id jonsoku-dev \
  --approval '{"required":true,"approvedBy":"jonsoku-dev","approvedAt":"<RFC3339>","reference":"chat-request-2026-08-23"}'
```

After successful UI mutation, append `apply.execute` and `verify.execute` with the same correlation ID and approval object. Append a sanitized `action: verify`, `outcome: success` UI observation, then run:

```bash
npm run botctl -- snapshot x-signal-scout \
  --input runtime-input.yaml \
  --correlation-id reconcile-20260823-x-signal-scout-a81f
```

The snapshot command validates the evidence chain and writes its own `snapshot.write` event.

UI-tracked Routines use a separate desired/runtime contract so an updated instruction cannot be hidden behind a Bot snapshot:

```bash
npm run botctl -- routine-export daily-ai-radar
npm run botctl -- routine-plan daily-ai-radar
npm run botctl -- routine-verify daily-ai-radar --input routine-runtime-input.yaml
npm run botctl -- routine-snapshot daily-ai-radar \
  --input routine-runtime-input.yaml \
  --correlation-id reconcile-20260823-daily-ai-radar-a81f
```

The Routine observation must re-read `name`, `instruction`, `active`, and `trigger`. Repository Skill procedures remain rendered into the exact Bot Description until the Grok private-Skill creation, assignment, and re-read path is observed; never self-attest a Skill ID in a runtime snapshot.

Every reconciliation run should have one `correlationId` linking plan/apply/verify/snapshot events.

---

# Recommended Codex implementation structure

```text
tooling/
└── botctl/
    └── src/
        ├── commands/
        │   ├── validate.ts
        │   ├── export.ts
        │   ├── plan.ts
        │   ├── apply.ts
        │   ├── verify.ts
        │   ├── snapshot.ts
        │   └── audit.ts
        ├── providers/
        │   ├── types.ts
        │   └── grok-computer-use.ts
        ├── runtime/
        │   ├── snapshot.ts
        │   └── diff.ts
        └── manifests/
            ├── loader.ts
            └── normalize.ts
```

Provider contract:

```ts
interface AgentRuntimeProvider {
  inspect(id: string): Promise<RuntimeBot | null>;
  create(desired: BotDesiredState): Promise<RuntimeBot>;
  update(current: RuntimeBot, desired: BotDesiredState, plan: ChangePlan): Promise<RuntimeBot>;
  verify(id: string, desired: BotDesiredState): Promise<VerificationResult>;
}
```

Computer Use belongs strictly behind `GrokComputerUseProvider`.

Do not scatter UI-driving logic through manifest or business-logic modules.

---

# Important limitation: Codex Computer Use API surface

Do not invent a private/undocumented automation interface for the Grok desktop app. Use the Computer Use capabilities actually exposed by the Codex App session.

If Codex can visually operate the desktop but cannot expose a programmatic reusable driver API, implement `botctl apply` as a **guided reconciliation command** that generates:

- exact target Bot;
- exact current/desired diff;
- exact fields to enter;
- audit correlation ID;
- verification checklist;

and let the Codex Computer Use agent execute those steps interactively.

This is preferable to fake determinism.

---

# Failure modes and required response

## Authentication / login required

Stop and ask the user to take over for authentication. Never request that a password or OTP be placed in repository files or chat logs.

## CAPTCHA / passkey / 2FA

Human takeover only.

## App updated and UI changed

Do not patch selectors blindly. Re-run Phase 0 observation and update `runtime/ui-contract/grok-desktop.yaml`.

## Bot not found

If desired state says runtime should exist but the Bot cannot be found, classify `MISSING`; do not recreate until the user sees the plan because deletion/rename may have occurred externally.

## Description truncated by UI limit

Fail verification and record the observed limit. Do not silently truncate canonical instructions. Decide at schema/design level how to split profile description vs Skills.

## Group limit / Bot limit reached

Stop and report capacity conflict. Do not remove other Bots/groups automatically.

## App crashes or Save uncertainty

Reopen app and inspect runtime before retrying. Never assume transaction success.

---

# Security

The Grok Bot docs state local-computer execution is separately permissioned and that Bots share a user-scoped cloud computer. Treat those as distinct trust zones.

For this workflow:

- Codex may control the local Grok Bot desktop application only for declared synchronization tasks.
- Do not place GitHub credentials into Grok descriptions.
- Do not let Grok Bot memory become an authentication or configuration store.
- Do not use separate Bots as security boundaries.
- Company Bot configuration should eventually use a company-controlled repository/environment rather than mixing confidential configuration into this personal repo.

---

# Definition of done for desktop automation milestone

The milestone is complete only when all are true:

1. `npm run validate` passes.
2. current Grok desktop UI contract is documented from actual observation.
3. `botctl export` supports inline and file descriptions.
4. disposable test Bot can be created from manifest via Codex Computer Use.
5. fields are reopened and verified exactly after save.
6. runtime snapshot is written.
7. audit events are written for plan/approval/apply/verify/snapshot.
8. `botctl plan test-bot` returns `SYNCED` after apply.
9. a deliberate manifest update returns `DRIFTED`, is approved/applied, and returns `SYNCED` again.
10. ambiguous UI state causes a safe stop rather than guessing.
11. no automatic deletion path exists.
12. one real non-destructive Bot (start with `x-signal-scout`) is successfully reconciled after the test Bot proves stable.

---

# Exact prompt to give Codex App

Use the following instruction in Codex App:

```text
Open the local repository jonsoku-dev/grok-bot and read README.md, docs/ARCHITECTURE.md, docs/CODEX_HANDOFF.md, and docs/CODEX_GROK_DESKTOP_AUTOMATION.md before making changes.

GitHub is the canonical desired state. The locally installed Grok Bot desktop app is runtime state only.

Use gh CLI for GitHub operations. Use Codex Computer Use to inspect and operate the locally installed Grok Bot desktop app. Do not assume the current UI layout: first perform the non-mutating UI observation phase and record an observed UI contract under runtime/ui-contract/grok-desktop.yaml.

Then implement the control-plane foundation and reconciliation flow. Start with one disposable test Bot. Required lifecycle is validate → export → plan → explicit approval → Computer Use apply → reopen and exact verify → runtime snapshot → audit → plan must become SYNCED.

Never auto-delete. Never guess when UI state is ambiguous. Never rewrite canonical Bot descriptions during apply. Never store credentials, OTPs, cookies, or secrets. Authentication/2FA/CAPTCHA must use human takeover.

All Computer Use implementation must remain behind a GrokComputerUseProvider-style adapter so an official API can replace it later. Add deterministic tests wherever possible. Use meaningful commits and PRs. Run validation after each logical phase.

Do not touch the full Bot roster until the disposable test Bot has successfully completed both create and drift-update reconciliation flows.
```
