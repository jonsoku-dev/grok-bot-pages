---
{}
---

# Codex App Handoff

> Turn this repository into a usable Git-backed Grok Bot control plane. Work through the repository using the `gh` CLI for GitHub operations. Keep GitHub as canonical desired state; do not make Grok UI state authoritative.

# Codex App Handoff

## Mission

Turn this repository into a usable Git-backed Grok Bot control plane. Work through the repository using the `gh` CLI for GitHub operations. Keep GitHub as canonical desired state; do not make Grok UI state authoritative.

## First commands

```bash
gh repo clone jonsoku-dev/grok-bot
cd grok-bot
gh repo view --json nameWithOwner,visibility,defaultBranchRef
```

Before making changes, inspect all existing files and `git log`.

## Required implementation order

### Phase 1 — Foundation

1. Formalize `agentops/v1alpha1` schemas for Bot, Group, Skill, Routine, Channel and RuntimeSnapshot.
2. Add all initial bot manifests listed below.
3. Add group definitions and routine manifests.
4. Add policy/config files for interests, publishing, personal/company boundaries and approvals.
5. Add deterministic validation.

Initial bots:

**AI Engineering Radar**
- x-signal-scout
- github-scout
- release-scout
- evidence-verifier
- relevance-judge
- github-sot-writer

**Architecture Council**
- assumption-challenger
- tradeoff-analyst
- operations-reviewer
- security-reviewer
- decision-synthesizer

**Knowledge Delivery**
- github-reader
- document-publisher
- slack-publisher
- gmail-publisher

**Control plane**
- bot-registry-manager

Keep bot responsibilities minimal. A reusable procedure belongs in a Skill, not a new Bot.

### Phase 2 — botctl

Build a TypeScript CLI under `tooling/botctl` with at least:

```bash
npm run botctl -- validate
npm run botctl -- list
npm run botctl -- show <bot>
npm run botctl -- export <bot>
npm run botctl -- plan [bot]
npm run botctl -- guided <bot>
npm run botctl -- snapshot <bot> --input <runtime-snapshot.yaml> --correlation-id <id>
npm run botctl -- verify <bot> [--input <runtime-snapshot.yaml>]
npm run botctl -- ui-observe --input <ui-observation.yaml>
npm run botctl -- ui-observe-summary
```

`export` should produce a human/computer-use friendly package containing the exact Grok UI values to enter plus group/routine actions.

`plan` must compare desired manifests with `runtime/grok/**` snapshots and classify each object as:

- SYNCED
- DRIFTED
- MISSING
- UNMANAGED

Never auto-delete. `deletionPolicy: retain` is the default.

### Phase 3 — CI

Add GitHub Actions to run with deterministic checks only:

- YAML/schema validation
- duplicate IDs
- dangling references
- group membership validity
- missing skills/routines
- invalid trigger configuration
- permission escalation policy
- personal/company boundary violations
- schedule collisions where detectable

Use `gh` to inspect workflow status and PR checks.

### Phase 4 — Computer-use adapter

Design provider abstraction first:

```ts
interface AgentRuntimeProvider {
  inspect(id: string): Promise<RuntimeBot | null>;
  create(desired: BotManifest): Promise<void>;
  update(desired: BotManifest): Promise<void>;
  verify(id: string): Promise<RuntimeBot>;
}
```

Implement a `GrokComputerUseProvider` only after manual `export` is stable.

Computer-use application rules:

1. `plan` before every mutation.
2. Require explicit approval for apply during initial rollout.
3. Create/update only; never delete automatically.
4. Re-read UI after save and verify exact values.
5. Persist observed state to `runtime/grok/` with source commit SHA and timestamp.
6. UI selectors and navigation knowledge must remain adapter-specific.
7. If the UI is ambiguous, stop instead of guessing.

If an official Grok configuration API becomes available, implement another provider rather than changing manifests.

## GitHub workflow

Use branches and PRs for meaningful control-plane changes:

```bash
git switch -c feat/control-plane-foundation
# edit/test
git add .
git commit -m "feat: build Grok control plane foundation"
git push -u origin HEAD
gh pr create --fill

gh pr checks --watch
```

Do not store tokens or secrets in the repository. Use GitHub Actions secrets or the approved runtime secret mechanism.

## SoT rules

- `bots/`, `groups/`, `skills/`, `routines/`, `config/`, `knowledge/`, and approved `reports/` are desired/canonical data.
- `runtime/` is observed state and never overrides desired state.
- Grok conversation memory is never canonical.
- Company data must be isolated from this personal repository unless explicitly public/sanitized.

## Definition of done for the next Codex session

Do not attempt full Grok UI automation immediately. The first milestone is complete when:

1. all initial manifests exist and validate;
2. `pnpm botctl validate` passes;
3. `pnpm botctl export x-signal-scout` emits an exact setup package;
4. `pnpm botctl plan` works against fixture/runtime snapshots;
5. CI passes on a PR;
6. README documents manual setup from exported configuration;
7. a follow-up issue exists for computer-use synchronization with explicit acceptance criteria.

After that, test computer-use synchronization on **one disposable/test bot first**, then expand to the roster.
