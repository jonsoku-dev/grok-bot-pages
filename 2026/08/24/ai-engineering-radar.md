---
title: "2026-08-24 AI Engineering Radar"
status: "approved"
action: "EXPERIMENT"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/24/regional-signal/"
sourceLinks:
  - "https://docs.x.ai/grok-bot/overview"
records:
  - "intelligence/signals/2026/08/24/regional-signal/international/grok-bot-official-workflow-docs.yaml"
---

# 2026-08-24 AI Engineering Radar

> 한국·일본·국제의 검증된 AI 엔지니어링 신호와 가장 작은 다음 행동을 정리합니다.

# 2026-08-24 AI Engineering Radar

이 초안은 검증된 항목별 SoT 레코드에서 생성했습니다. 사실을 수정하려면 글이 아니라 원본 레코드와 검증 근거를 먼저 고쳐야 합니다.

<!-- truncate -->

## 왜 중요한가

이 보고서는 이름을 나열하지 않고 관측 사실, 판단, 한계와 다음 행동을 함께 남깁니다.

## 한국

EMPTY — 이 권역에서 기준을 충족한 검증 레코드가 없습니다.

## 일본

EMPTY — 이 권역에서 기준을 충족한 검증 레코드가 없습니다.

## 국제

### [Grok Bot](https://docs.x.ai/grok-bot/overview) — `grok-bot-official-workflow-docs`

2026-08-11에 갱신된 xAI Grok Bot 공식 문서는 사용자 계정 단위 공유 영속 클라우드 VM(파일·브라우저 세션·앱 로그인 공유, Bot별 화면), Bot 간 메시징·핸드오프, Skill(재사용 절차)·Routine(스케줄/이벤트)을 제품 기본 모델로 서술한다. 다 Bot이 한 컴퓨터에서 협업하는 이 저장소 운영에 맞닿은 공식 워크플로 신호다.

- 관측:
  - https://docs.x.ai/grok-bot/overview HTML/JSON-LD: datePublished=2026-08-11T00:00:00Z, dateModified=2026-08-11T00:00:00Z; UI 'Last updated: August 11, 2026' (re-fetched 2026-08-24 for measurement regional-pipeline-20260824-grokbot-docs-v2).
  - https://docs.x.ai/grok-bot/skills-routines-and-automations HTML/JSON-LD: datePublished=2026-08-11T00:00:00Z, dateModified=2026-08-11T00:00:00Z; UI 'Last updated: August 11, 2026'.
  - Overview: each Bot runs on a persistent cloud VM with browser, filesystem, terminal; connectors/MCP when available; computer use for apps without clean API.
  - Overview 'Bots share one computer': all Bots share one user-scoped persistent cloud computer (files, browser sessions, app logins); isolated to account not individual Bot; each Bot has its own screen; parallel use without separate security boundaries.
  - Overview: Bots message each other, share context in threads/group chats, pass ownership; can learn workflows from live demonstration and persist as routine.
  - Skills/routines: skill = reusable instructions; routine = schedule or supported event trigger; skills available across Bots; Settings→Plugins; / for skills, @ for Bots/groups/routines/connectors.
  - Teach a task: up to ten minutes visible computer interaction, no mic audio; draft skill; secure handoff for credentials; test before scheduling.
  - Routines: owning Bot, schedule/timezone, inputs, expected result, approval boundary, missing-source policy; background while laptop closed; Cursor account event integrations separate from Slack/GitHub plugins.
  - Limits: up to 50 routines per Bot; 20 most recent run records kept; delete immediate no undo.
  - Trust design: preparation before execution; approval for send/purchase/delete/publish/production changes.
- 판단: `READ` — 공식 Grok Bot 문서가 공유 영속 VM·Bot 메시징·Skill/Routine·승인 게이트를 제품 기본값으로 명시해 Grok·agent skills·harness interest 및 다 Bot 레이더 운영과 직접 맞닿음. 이미 플랫폼 사용 중이라 ADOPT/EXPERIMENT보다 문서 흡수(READ). 지리 비가중.
- 한계:
  - datePublished/dateModified are calendar midnight UTC (2026-08-11T00:00:00Z); sub-day timestamp not provided.
  - originalTitle uses overview H1 'Grok Bot'; companion page title is 'Skills and routines'.
  - measurementId: regional-pipeline-20260824-grokbot-docs-v2
  - expectedCanonicalPath: intelligence/signals/2026/08/24/regional-signal/international/grok-bot-official-workflow-docs.yaml
  - X/paid APIs unused; no GitHub write in discovery.
  - 공유 VM은 Bot 간 별도 보안 경계가 없음(문서 명시).
  - 문서 브랜드 SpaceXAI Docs vs author xAI 표기 불일치.
  - datePublished/Modified가 UTC 자정 placeholder라 당일 시각 미확인.
  - 이벤트 트리거가 Cursor 계정 연동에 묶임.
- 다음 행동: overview·skills-routines·approvals 페이지만 읽고 현재 Radar Bot의 Skill/Routine/승인 게이트를 1:1 대조. 새 Routine·외부 게시·GitHub/SoT 쓰기 없음.

## 판단

각 항목의 행동과 이유는 위에 표시했습니다. 도입은 별도 승인과 가장 작은 실험을 통과한 뒤에만 검토합니다.

## 한계

`VERIFIED`는 공개 원문에 해당 주장이 존재함을 확인했다는 뜻이며, 성과와 안전성을 독립 감사했다는 뜻이 아닙니다.

## 근거

frontmatter의 `records`가 항목별 사실 SoT이며 `sourceLinks`는 독자가 직접 열 수 있는 공개 원문입니다.
