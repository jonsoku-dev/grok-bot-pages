---
{}
---

# Miyamae Editorial & Community Playbook

> Before publishing, answer:

# Miyamae Editorial & Community Playbook

## Core test

Before publishing, answer:

1. Is this materially relevant to a Miyamae resident?
2. What exactly do we know, and what do we not know?
3. What is the strongest available source?
4. Could publication harm a private person or distort an unresolved event?
5. Does urgency justify publishing now rather than verifying further?
6. What would we need to correct if the source changes?

## Candidate record

Each story candidate should preserve:

```yaml
id: stable-id
detected_at: ISO-8601
observed_at: ISO-8601
geography: [宮前区, neighborhood]
topics: []
state: LEAD|VERIFYING|CONFIRMED|OFFICIAL|DISPUTED|CORRECTED|RETRACTED|EXPIRED
risk: R0|R1|R2|R3
headline_fact: ""
known: []
unknown: []
sources:
  - url: ""
    source_type: primary|first_party|media|resident|social
    observed_at: ISO-8601
publish_mode: immediate|batch|hold
follow_up_at: null
correction_of: null
```

## Writing templates

### Breaking / official

`【速報】宮前区：{fact}`

State what happened, where, effective time, resident action if any, and source. Do not add drama.

### Follow-up

`【続報】{previous story}`

Explicitly say what changed since the previous post.

### Correction

`【訂正】{incorrect point}`

Say what was wrong, what is correct, why the correction is being made, and link back when possible. Do not hide the original mistake.

### Event

`【イベント】{name}`

Prioritize date/time, place, cost/registration, who it is useful for, cancellation conditions and official source.

### Opening / closure

`【開店】` / `【閉店】`

Use first-party confirmation when possible. Do not treat construction appearance or a resident rumor as confirmation.

### Unverified community lead

Normally do not create a standalone assertion. Ask carefully:

`鷺沼周辺の○○について情報提供をいただいています。公式情報を確認中です。一次情報をご存じの方がいれば、リンク等を教えてください。`

Use this only when asking itself has public value and does not unfairly damage someone.

## Tone

Good:
- `今日、宮前区で知っておきたいことをまとめます。`
- `現時点で公式発表は確認できていません。分かり次第更新します。`
- `現地をご存じの方、公開可能な一次情報があれば教えてください。`

Bad:
- `ヤバすぎる！`
- `宮前区民ブチギレ`
- `絶対○○らしい`
- `AIによると...`
- fake eyewitness language

## Community prompts

Community formation should emerge from useful prompts, not forced engagement bait.

Recurring formats:

- `宮前区民に聞きたい` — one concrete local question
- `教えて宮前区` — request first-hand local knowledge
- `今週末なにする？` — events + resident additions
- `この店どう？` — only neutral experience solicitation, never pile-ons
- `昔の宮前区` — history/memory/photo prompts with rights/privacy caution
- `宮前区の好きな場所` — parks, views, shops, walks
- `困ってます / 知ってる人いますか` — practical non-sensitive questions

Do not ask followers to identify suspected people, vehicles, homes, children, victims or alleged offenders.

## Moderation

Delete/ignore/do not amplify:
- doxxing and personal data
- threats/harassment
- discriminatory attacks
- unverified accusations against identifiable people
- victim/minor identification
- spam/scams
- graphic content

Criticism of public policy, local services and businesses is not removed merely because it is negative. Preserve factual criticism while preventing harassment and unverified allegations.

## Politics and elections

Local politics is within scope because residents have a right to know. Coverage must be informational rather than campaign advocacy:

- deadlines, polling, candidate/public-meeting information and official results are valid;
- summarize competing positions accurately when covering disputes;
- distinguish official records from campaign claims;
- no automated endorsement;
- high-impact allegations require human review and strong sourcing.

## Crime, accidents, death and grief

These stories may matter locally, but they are where an automated account can do the most damage.

- prioritize safety instructions and verified public facts;
- do not identify victims/private persons unless clearly justified and already authoritatively public;
- avoid speculation about cause, blame or motive;
- avoid graphic details not necessary for resident safety;
- R2/R3 human review remains mandatory;
- grief is not engagement content.

## Commercial fairness

Businesses can be praised, criticized, reported opened or closed, and discussed. Apply the same verification rules regardless of whether the owner follows the account, advertises, complains, or offers benefits.

## Publishing matrix

| Story | Default | Requirement |
|---|---|---|
| Official ward event | R0 batch | official source |
| Official emergency warning | R0 immediate | primary authority + timestamp |
| Railway/operator disruption | R0/R1 immediate | operator source |
| Store opening | R1 | first-party or strong corroboration |
| Store closure | R1/R2 | first-party/credible evidence; reputational care |
| Resident road observation | R1 | corroborate if presented as fact |
| Accident/fire | R2 | human review unless pure authoritative safety relay |
| Complaint about business | R2 | evidence, right-sized wording, human review |
| Political controversy | R2 | human review + multi-source context |
| Named alleged offender | R3 | human-only, normally avoid |
| Minor/victim/private medical detail | R3 | do not publish absent exceptional public-interest justification |

## Founder workload target

The founder should not become a full-time editor. Target steady state:

- R0: no review after trust threshold is met
- R1: exception queue only
- R2: concise review card with evidence and recommended wording
- R3: rare escalation, default hold
- one weekly editorial review of errors, blind spots and source gaps

The system should learn operationally from corrections and source failures, but never learn that high engagement is evidence of truth.
