---
{}
---

# Grok Desktop Rollout Receipt — 2026-08-23

> The desktop-automation milestone in `docs/CODEX_GROK_DESKTOP_AUTOMATION.md` was completed against Grok Bot Desktop `0.24.0` on macOS using Codex App built-in Computer Use only.

# Grok Desktop Rollout Receipt — 2026-08-23

## Outcome

The desktop-automation milestone in `docs/CODEX_GROK_DESKTOP_AUTOMATION.md` was completed against Grok Bot Desktop `0.24.0` on macOS using Codex App built-in Computer Use only.

Verified lifecycle:

- `codex-sync-test`: `MISSING -> create -> reopen/exact verify -> SYNCED`
- `codex-sync-test`: deliberate Title drift -> `DRIFTED -> approved one-field update -> reopen/exact verify -> SYNCED`
- `x-signal-scout`: profile, Group membership, and Routine ownership reconciled -> `SYNCED`

## Runtime rollout

Created and reopened with exact Name, Title, and Description:

- X Signal Scout
- GitHub Scout
- Release Scout
- Evidence Verifier
- Relevance Judge
- GitHub SoT Writer

Created and verified `AI Engineering Radar` with exactly those six members. Its Description is the canonical Group purpose.

Created and verified:

- `Daily AI Engineering Radar`: active, daily at 06:30, global timezone `Asia/Tokyo`
- `Weekly AI Engineering Review`: active, Sunday at 18:00, global timezone `Asia/Tokyo`; prepares a review candidate and stops for explicit approval before the canonical write

Both routines use canonical UI instructions stored in their manifests. Test Run was never clicked.

## Evidence

- Bot snapshots: `runtime/grok/bots/`
- Append-only reconciliation events: `audit/events/2026/08/2026-08-23.jsonl`
- Observed UI contract: `runtime/ui-contract/grok-desktop.yaml`
- Sanitized interaction learning log: `runtime/ui-observations/2026-08-23.jsonl`
- Stable learned patterns require successful observations from at least two distinct correlation IDs.
- Relationship snapshots were reissued after field-specific Group/Routine verification; the earlier insufficient snapshot attestations remain in append-only audit history and are linked by corrective `drift.detected` events.

No automatic deletion path exists. No Orca CLI path was used. No password, OTP, token, raw screenshot, screen dump, account inventory, or Plugin inventory was stored.

## External gates and remaining scope

The Daily Routine's immediate first run stopped because the X account/credit setup is unavailable. No account setup, connector installation, credit purchase, or external publish was attempted. The configured Routine remains active and should be re-run only after the user completes the X-side setup.

Architecture Council, Knowledge Delivery, and control-plane-only Bots remain desired manifests but were not deployed in this milestone. The repository-wide plan therefore intentionally continues to report those resources as `MISSING`; the verified AI Engineering Radar slice and disposable test are `SYNCED`.
