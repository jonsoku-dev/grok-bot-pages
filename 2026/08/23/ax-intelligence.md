---
title: "AI가 업무를 바꾼 세 장면과 아직 답하지 못한 질문"
status: "approved"
action: "READ"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/23/ax-case/"
sourceLinks:
  - "https://www.yna.co.kr/view/AKR20260818061300017"
  - "https://www.fnnews.com/news/202608181028437199"
  - "https://www.itmedia.co.jp/enterprise/articles/2608/21/news019.html"
  - "https://www.technologyrecord.com/article/nordre-follo-municipality-modernises-public-hearing-workflows-with-microsoft-copilot-studio"
  - "https://www.atea.no/kundereferanser/norde-follo-kommune-1/?pid=3b1733d9-adef-4b74-8b69-2cedb52ea3ec"
records:
  - "intelligence/signals/2026/08/23/ax-case/korea/shinhan-securities-contract-agent.yaml"
  - "intelligence/signals/2026/08/23/ax-case/japan/mufg-ai-flowchart.yaml"
  - "intelligence/signals/2026/08/23/ax-case/international/nordre-follo-hearing-agent.yaml"
---

# AI가 업무를 바꾼 세 장면과 아직 답하지 못한 질문

> 신한투자증권, 미쓰비시UFJ은행, Nordre Follo 사례에서 바뀐 업무 흐름과 사람이 계속 맡는 책임을 비교합니다.

# AI가 업무를 바꾼 세 장면과 아직 답하지 못한 질문

세 사례의 공통점은 “AI를 썼다”가 아닙니다. 사람이 하던 긴 문서 읽기와 구조화 초안을 에이전트가 맡고, 원본 보존·검토·최종 판단은 사람에게 남겼습니다. 반대로 세 사례 모두 공개 수치만으로 정확도와 총비용을 판단하기는 어렵습니다.

아래 세 YAML 레코드가 사실의 SoT이고, 본문은 업무 흐름과 판단을 비교한 해설입니다.

<!-- truncate -->

## 왜 중요한가

AX 사례는 도구 이름보다 “업무가 전후로 어떻게 달라졌는가”가 핵심입니다. 세 사례를 같은 틀로 보면 자동화가 잘 맞는 구간과 사람이 빠지면 안 되는 구간이 분명해집니다.

## 한국: 계약서 읽기와 입력을 하나의 흐름으로

### 신한투자증권 — `shinhan-securities-contract-agent`

[연합뉴스 보도](https://www.yna.co.kr/view/AKR20260818061300017)에 따르면 기존에는 담당자 3~4명이 이메일로 받은 약 50쪽의 장외파생상품 계약서를 읽고 약 50개 항목을 사내 시스템에 직접 입력했습니다. Gemini Enterprise 기반 에이전트와 내부 오케스트레이터를 적용한 뒤에는 계약서 분석에서 입력까지 이어지고, 담당자가 결과를 확인합니다.

- 보고된 변화: 클로즈드 베타에서 건당 약 2시간이 약 5분으로 줄었다고 회사 측은 설명했습니다.
- 사람의 책임: 추출과 입력 결과를 최종 확인하고 금융 규제와 내부 통제를 책임집니다.
- 판단: 문서 접수 → 구조화 추출 → 시스템 입력 제안 → 사람 확인이라는 패턴은 재사용할 만합니다.
- 한계: 표본 수, 추출 정확도, 예외율, 재작업률과 잘못된 입력의 영향이 공개되지 않았습니다. 수치는 회사·공급자 발표이며 독립 감사 결과가 아닙니다.

## 일본: 자유 생성의 실패를 도메인 구조로 줄이기

### 미쓰비시UFJ은행 — `mufg-ai-flowchart`

[ITmedia가 AWS Summit Japan 발표를 재구성한 기사](https://www.itmedia.co.jp/enterprise/articles/2608/21/news019.html)에 따르면, 기존에는 지식 보유자가 본부 약 600쪽과 각 해외 거점의 수백~수천 쪽 절차서를 읽어 흐름도를 만들고 차이를 비교했습니다. AI 흐름도는 작성·비교·자연어 수정을 돕고, 약 2만 개 트리플로 만든 오ント롤로지와 지식 그래프가 표현 차이를 정규화합니다.

- 보고된 변화: 흐름도 작성·비교·수정 공수가 사례당 11인일에서 1인일로 줄어들 것으로 예상했습니다.
- 사람의 책임: 트리플과 흐름도를 검토·수정하고, 관계자 협의와 최종 절차 결정을 맡습니다.
- 실패에서 얻은 것: 생성형 AI만 사용한 초기 프로토타입은 흐름을 잘못 이해하고 지나치게 단순하거나 화려한 결과를 만들었습니다. 도메인 구조와 사람의 교정을 추가한 뒤 방향이 바뀌었습니다.
- 한계: 90%는 운영 확정 실적이 아니라 예상치입니다. 관계자 협의에 필요한 1~2인월은 줄지 않으며, 기사는 기업 발표에 기반한 2차 자료입니다.

## 국제: 공공 의견을 요약하되 원본과 검토를 남기기

### Nordre Follo 지방정부 — `nordre-follo-hearing-agent`

[Technology Record 사례](https://www.technologyrecord.com/article/nordre-follo-municipality-modernises-public-hearing-workflows-with-microsoft-copilot-studio)와 [Atea의 구현 사례](https://www.atea.no/kundereferanser/norde-follo-kommune-1/?pid=3b1733d9-adef-4b74-8b69-2cedb52ea3ec)는 노르웨이 Nordre Follo의 공청회 흐름을 설명합니다. 과거에는 담당자가 PDF 의견서를 옮겨 읽고 주제를 추출해 Word 보고서로 합쳤습니다. 지금은 원본 PDF를 기록 관리 시스템에 보존한 뒤 Copilot Studio 에이전트가 요약·분류·표 초안을 만들고 담당자가 모두 검토합니다.

- 운영 근거: 개발 환경에서 8개 공청회 주기로 파일럿하고 정확도를 확인한 뒤 2025년 11월 운영으로 옮겼다고 설명합니다.
- 사람의 책임: 모든 요약을 수동 검토하고 편집하며 공공 의사결정과 공개 책임을 집니다.
- 판단: 원본 기록 보존 → AI 초안 → 전수 검토라는 경계는 공공 문서뿐 아니라 기업 규정·고객 의견에도 적용할 수 있습니다.
- 한계: 평가 표본과 합격 기준, 개인정보·이의제기 절차, 감사된 시간 절감·정확도·오류율은 공개되지 않았습니다. 두 자료 모두 구현 생태계와 이해관계가 있습니다.

## 판단

세 사례에서 가져올 설계 원칙은 네 가지입니다.

1. AI가 원문을 덮어쓰지 않고 원본과 초안을 분리합니다.
2. 자유 생성이 흔들리면 더 큰 모델보다 도메인 스키마·오ント롤로지·지식 그래프를 먼저 검토합니다.
3. 시간 절감만 보지 않고 정확도, 예외, 재작업, 사람 검토 시간과 실패 비용을 함께 측정합니다.
4. 사람의 최종 책임을 문구로만 남기지 말고 실제 승인 단계와 감사 기록으로 구현합니다.

## 한계

- 세 사례 모두 독립 감사 보고서가 아니라 기업·구현 파트너·산업 매체의 공개 자료에 의존합니다.
- `VERIFIED`는 업무 흐름과 공개 주장을 출처에서 확인했다는 뜻입니다. 주장한 성과가 일반적으로 재현된다는 뜻은 아닙니다.
- 한국 수치는 클로즈드 베타, 일본 수치는 예상, 국제 사례는 정량 성과 미공개입니다. 같은 막대그래프로 비교할 수 없습니다.
- 실제 도입 판단에는 데이터 분류, 오류 정정, 책임 소재, 총비용과 운영 중단 절차가 더 필요합니다.

## 근거

각 사례의 이전·이후 워크플로, 사람 책임, 거버넌스, 평가, 수치, 한계와 검증 URL은 frontmatter의 `records` 세 파일에 보존했습니다.
