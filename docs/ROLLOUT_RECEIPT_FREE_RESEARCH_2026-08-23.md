---
{}
---

# Free Research and Korean-Only Rollout Receipt — 2026-08-23

> Source commit `9faa545b46f12511c89234fc1b9c64573ded7bb4` was reconciled to Grok Bot Desktop `0.24.0` using Codex App built-in Computer Use only.

# Free Research and Korean-Only Rollout Receipt — 2026-08-23

## Outcome

Source commit `9faa545b46f12511c89234fc1b9c64573ded7bb4` was reconciled to Grok Bot Desktop `0.24.0` using Codex App built-in Computer Use only.

- X and paid external APIs remain deferred.
- `insane-search` was not installed, executed, vendored, or configured as a private Grok Skill.
- Its pinned public-research procedure and each Bot's bounded source policy were rendered into the exact verified Bot Description.
- All natural-language Bot replies, questions, status updates, summaries, and explanations are constrained to Korean; code, commands, URLs, proper nouns, and necessary source quotations may remain verbatim.
- The active Daily AI Engineering Radar instruction now uses free public sources, excludes X, and carries the Korean-only rule.

## Verified runtime resources

The following existing runtime Bots were saved, closed, reopened, and matched exactly against `botctl export`:

- `x-signal-scout` / Open Signal Scout — name, title, 6,411-character Description, group, and Daily Routine
- `github-scout` — 4,678-character Description, group, and empty Routine list
- `release-scout` — 4,538-character Description, group, and empty Routine list
- `evidence-verifier` — 5,160-character Description, group, and empty Routine list
- `relevance-judge` — 626-character Description, group, and Weekly AI Engineering Review relationship
- `github-sot-writer` — 593-character Description, group, and empty Routine list
- `codex-sync-test` — 463-character Description, no group, and empty Routine list

`daily-ai-radar` was separately reopened and matched on:

- name: `Daily AI Engineering Radar`
- active: `on`
- instruction: exact `routine-export` value
- trigger: daily at 06:30 with repository timezone semantics `Asia/Tokyo`

All seven Bot plans and the Daily Routine plan returned `SYNCED` after their correlated audit, UI-observation, and runtime-snapshot chains were written.

## Behavior check and learned UI rule

After saving Open Signal Scout, one explicit Korean prompt asked it to confirm its role, language policy, and X status. It answered in Korean and confirmed that X stays deferred until human approval.

The automatic acknowledgement emitted immediately after the profile change used stale English/X context. Therefore:

1. never use an automatic profile-change acknowledgement as policy verification;
2. first close and reopen Bot settings and compare the exact Description;
3. then run a bounded post-save conversation check when behavior-level proof is required;
4. record both structural and behavioral evidence separately.

No Routine test run was triggered, so this rollout did not cause a radar execution or an external/canonical write.

## Validation

- `npm test` — 12/12 passed before runtime reconciliation
- `npm run validate` — passed before reconciliation
- GitHub PR #4 CI `validate` — passed
- independent static re-review — no blocking findings
- final repository validation and runtime plan checks are recorded in the evidence commit that contains this receipt
