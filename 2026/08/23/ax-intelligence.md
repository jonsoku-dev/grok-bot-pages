---
title: "2026-08-23 AX Intelligence"
status: "approved"
action: "READ"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/23/ax-case/international/nordre-follo-hearing-agent.yaml"
  - "intelligence/signals/2026/08/23/ax-case/japan/mufg-ai-flowchart.yaml"
  - "intelligence/signals/2026/08/23/ax-case/korea/shinhan-securities-contract-agent.yaml"
sourceLinks:
  - "https://www.technologyrecord.com/article/nordre-follo-municipality-modernises-public-hearing-workflows-with-microsoft-copilot-studio"
  - "https://www.itmedia.co.jp/enterprise/articles/2608/21/news019.html"
  - "https://www.yna.co.kr/view/AKR20260818061300017"
records:
  - "intelligence/signals/2026/08/23/ax-case/international/nordre-follo-hearing-agent.yaml"
  - "intelligence/signals/2026/08/23/ax-case/japan/mufg-ai-flowchart.yaml"
  - "intelligence/signals/2026/08/23/ax-case/korea/shinhan-securities-contract-agent.yaml"
---

# 2026-08-23 AX Intelligence

> 한국·일본·국제의 검증된 AX 사례를 업무 전후, 사람 책임과 한계로 비교합니다.

# 2026-08-23 AX Intelligence

이 글은 검증된 공개 자료와 근거 레코드에서 작성했습니다. 내용을 고칠 때는 글보다 근거를 먼저 바로잡습니다.

<!-- truncate -->

## 왜 중요한가

이 글은 확인된 핵심 내용과 추천 이유, 주의할 점, 다음 단계를 함께 보여줍니다.

## 한국

### [신한투자증권](https://www.yna.co.kr/view/AKR20260818061300017) — `shinhan-securities-contract-agent`

- 이전 흐름: 담당자 3~4명이 이메일로 받은 약 50쪽의 비정형 장외파생상품 계약서를 읽고 약 50개 항목을 사내 시스템에 직접 입력했다.
- 바뀐 흐름: Gemini Enterprise 기반 에이전트와 내부 오케스트레이터가 계약서를 분석하고 업무 시스템 입력까지 이어 주며, 담당자는 결과를 확인한다.
- 사람의 책임: 담당자가 추출·입력 결과를 최종 확인하며 금융 규제와 내부 통제 책임은 조직에 남는다.
- 거버넌스·평가: 공개 보도는 금융권 망분리와 보안 규제 대응 장치를 적용했다고 설명하지만 통제 항목과 감사 결과는 공개하지 않았다. 장외파생상품 계약서 처리 클로즈드 베타에서 기존 수작업과 에이전트 적용 후 소요 시간을 비교했다.
- 공개 수치:
  - 처리 시간이 건당 약 2시간에서 약 5분으로 줄었다는 회사 측 클로즈드 베타 결과가 보도됐다.
  - 입력 대상은 약 50쪽 계약서의 약 50개 항목이며 기존에는 담당자 3~4명이 처리했다.
- 한계:
  - 수치는 회사와 공급자 측 발표를 인용한 보도이며 독립 감사나 표본 수가 공개되지 않았다.
  - 추출 정확도, 예외율, 재작업률과 잘못된 입력의 영향은 공개되지 않았다.
  - 클로즈드 베타 결과를 전체 계약 유형과 실제 운영 규모로 일반화할 수 없다.
- 재사용할 패턴: 문서 접수, 구조화 추출, 내부 시스템 입력 제안, 사람의 최종 확인을 분리하고 시간뿐 아니라 정확도·예외·재작업을 함께 측정한다.

## 일본

### [미쓰비시UFJ은행](https://www.itmedia.co.jp/enterprise/articles/2608/21/news019.html) — `mufg-ai-flowchart`

- 이전 흐름: 지식 보유자가 본부 약 600쪽과 각 해외 거점의 수백~수천 쪽 절차서를 읽어 흐름도를 만들고, 거점 간 차이를 비교하고, 관계자 협의를 거쳐 절차를 수정했다.
- 바뀐 흐름: 생성형 AI가 절차를 흐름도로 만들고 차이를 표시하며 자연어 수정과 다국어 협의를 지원한다. 오ント롤로지와 약 2만 개의 트리플로 구성한 지식 그래프가 표현 차이를 정규화한다.
- 사람의 책임: 지식 보유자가 트리플과 흐름도를 검토·수정하고 최종 절차를 확인하며 관계자 협의는 계속 사람이 수행한다.
- 거버넌스·평가: 생성형 AI 단독 프로토타입에서 오해·환각·출력 편차가 발생한 뒤, 도메인 오ント롤로지와 지식 그래프 및 사람 검토를 추가했다. AWS Summit Japan 2026 발표에서 흐름도 작성·비교·수정의 기존 추정 공수와 AI 흐름도 도입 후 예상 공수를 비교했다.
- 공개 수치:
  - 흐름도 작성·비교·수정 공수가 사례당 11인일에서 1인일로 줄어 90% 감소할 것으로 예상했다.
  - 작성은 10인일에서 0.5인일, 비교와 수정은 각각 0.5인일에서 0.25인일로 예상했다.
  - 관계자 협의에 필요한 1~2인월은 줄지 않는다고 밝혔다.
- 한계:
  - 90%는 확정 운영 실적이 아니라 발표 시점의 예상치다.
  - 초기 생성형 AI 단독 방식은 부정확하고 지나치게 단순하거나 화려한 흐름도를 만들고 담당 인원을 잘못 이해했다.
  - ITmedia가 기업 발표를 재구성한 2차 기사이며 기사 일부는 회원 전용이다.
- 재사용할 패턴: 자유 생성만 맡기지 말고 도메인 개념과 관계를 구조화한 지식 그래프, 사람의 교정, 변경 가능한 시각화, 협의 단계의 명시적 분리를 결합한다.

## 국제

### [Nordre Follo municipality](https://www.technologyrecord.com/article/nordre-follo-municipality-modernises-public-hearing-workflows-with-microsoft-copilot-studio) — `nordre-follo-hearing-agent`

- 이전 흐름: 담당자가 PDF 의견서를 SharePoint로 옮긴 뒤 각 문서를 읽고 핵심 주제를 추출해 요약하고, 여러 요약을 의사결정용 Word 문서로 합쳤다.
- 바뀐 흐름: 구조화 웹 폼으로 받은 의견을 기록 관리 시스템에 PDF로 보존한 뒤 SharePoint 라이브러리에 올리면 Copilot Studio 에이전트가 주제·이의·규제 우려를 요약하고 항목별 분류와 편집 가능한 Word 표 및 통합 보고서를 만든다.
- 사람의 책임: 모든 요약을 담당자가 수동 검토하고 편집하며 최종 공공 의사결정과 공개 책임은 지방정부에 남는다.
- 거버넌스·평가: 개발 환경에서 8개 공청회 주기로 파일럿하고 정확도를 검증한 뒤 2025년 11월 운영으로 옮겼으며 원본 PDF는 기록 관리 시스템에 보존한다. 8개 공청회 파일럿에서 정확도를 확인했다고 설명하지만 평가 표본, 기준, 오차 유형과 합격 임계값은 공개하지 않았다.
- 공개 수치:
  - 근린 공청회는 40~50건, 지방정부 전체 계획은 150건 이상 의견을 받을 수 있다고 설명한다.
  - 의견서 한 건은 첨부를 제외하고도 6쪽 이상일 수 있다.
  - 감사된 처리 시간, 정확도, 오류율, 재작업률 수치는 공개되지 않았다.
- 한계:
  - 주요 공개 자료는 구현 파트너와 Microsoft 생태계 매체의 사례 소개로 독립 감사 자료가 아니다.
  - 수동 검토가 필요하며 잘못된 감성·이해관계자·규제 우려 분류가 공공 의사결정에 영향을 줄 수 있다.
  - 정확도 검증 방법과 개인정보·보존·이의제기 절차의 세부 사항이 공개되지 않았다.
- 재사용할 패턴: 원본 기록을 보존한 채 AI가 초안 요약과 분류만 만들고, 사람이 모든 항목을 검토하며 평가 기준과 오류 정정 경로를 별도로 운영한다.

## 판단

각 항목의 행동과 이유는 위에 표시했습니다. 도입은 별도 승인과 가장 작은 실험을 통과한 뒤에만 검토합니다.

## 한계

`VERIFIED`는 공개 원문에 해당 주장이 존재함을 확인했다는 뜻이며, 성과와 안전성을 독립 감사했다는 뜻이 아닙니다.

## 근거

각 항목은 검증된 근거 레코드와 독자가 직접 열 수 있는 공개 원문에 연결되어 있습니다.
