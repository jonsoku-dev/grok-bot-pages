---
{}
---

# AX Regional Split Live Validation Receipt — 2026-08-23

> The single three-region AX scout was split into Korea, Japan, and International Scouts. All three run independently, publish one bounded regional `ax-case/v1` packet to the `AX Intelligence` group, and hand verification to the same independent Evidence Verifier. The group has exactly four members: three Scouts plus Evidence Verifier.

# AX Regional Split Live Validation Receipt — 2026-08-23

## Outcome

The single three-region AX scout was split into Korea, Japan, and International Scouts. All three run independently, publish one bounded regional `ax-case/v1` packet to the `AX Intelligence` group, and hand verification to the same independent Evidence Verifier. The group has exactly four members: three Scouts plus Evidence Verifier.

The live preview produced one meaningful case per region and all three reached `VERIFIED` without a canonical or external write:

- **Korea:** Shinhan Securities used a Gemini Enterprise agent platform and an internal hybrid orchestrator to extract roughly 50 fields from OTC derivatives contracts. The reported closed-beta workflow changed from three or four people spending about two hours per contract to about five minutes. Evidence Verifier cross-checked Yonhap, ZDNet Korea, and Digital Times and retained the warning that the reduction is self-reported and unaudited.
- **Japan:** Mitsubishi UFJ Bank described using generated flowcharts to standardize overseas-office work. Evidence Verifier confirmed the 2026-08-21 ITmedia reconstruction of the bank's AWS Summit Japan presentation. The reported 90% reduction remains a projected `見込み`, not an audited outcome, and the primary link is a media reconstruction rather than a bank report.
- **International:** Nordre Follo municipality in Norway uses a Copilot Studio agent to summarize and classify public-hearing submissions. Evidence Verifier cross-checked Technology Record and Atea, confirmed the human review boundary, and retained the absence of audited time-saving or error-rate figures.

X and paid APIs were not used. No SoT, GitHub knowledge file, Drive document, Gmail message, Slack message, or other external destination was written.

## Test-fix-test loop

The first single Scout produced useful data but its combined three-region handoff was truncated twice. Evidence Verifier had to request resends and could not reliably see all long parts. The durable fix is structural: one Bot, one region, one bounded candidate packet. Candidate-level `region i/n` splitting remains the fallback when even one regional packet is too long.

The shared Group is the progress and handoff surface, but pasted plain-text Bot names did not reliably wake every member. Deterministic execution therefore wakes each regional Scout directly and requires the packet and Verifier response to return to `AX Intelligence`. Evidence Verifier receives an explicit pointer when a group packet is present but not visible in its current context.

Automatic review classified one internal group preview as external posting. Only that one explicitly requested run was allowed; no persistent allow rule was created.

## Desktop and connector lessons

- GitHub was already connected with all exposed tools enabled. Bot Registry Manager nevertheless interpreted a private-repository public 404 as an authentication failure and started local `gh` device login. The flow was cancelled, and the Bot successfully read `jonsoku-dev/grok-bot` after being told to use the connected GitHub plugin read-only. Repository Bots now prohibit public API fallback, local `gh`, terminal, device login, and OAuth reauthorization.
- A newly created Japan routine was initially attached to the previously focused International Scout even though its creation form looked correct. Re-selecting both owner Bots exposed the error. The wrong routine was removed and recreated under Japan.
- The Daily Slack preview routine contained two identical 08:00 triggers. Reopening the editor exposed the duplicate; one trigger was removed before verification.
- New weekly routines initially announce Monday 08:00. These acknowledgements can be stale after the editor is corrected. The authoritative evidence is the reopened routine editor and the owner Bot's routine list; all three AX routines were verified at Sunday 07:00 Asia/Tokyo.

## Reusable creation rule

For future regional research Bots, use this loop:

```text
create/update profile
-> re-open exact Name, Title, Description
-> add to the shared Group one member at a time
-> create one owner-specific routine
-> re-select the owner Bot and verify the routine list
-> re-open the routine and count exact triggers
-> run one bounded real-data preview
-> verify in the shared Group
-> snapshot only after the full visible reread
```
