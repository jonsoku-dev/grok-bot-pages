---
title: "지금 읽을 결과"
status: "approved"
action: "EXPERIMENT"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/23/"
sourceLinks:
  - "https://toss.tech/article/tech_talk_talk_2"
  - "https://github.com/NomaDamas/jikji"
  - "https://github.com/NomaDamas/k-skill"
  - "https://zenn.dev/staddress/articles/b601f14a21c5c5"
  - "https://github.com/askdkc/pgroonga-mcp"
  - "https://github.com/Lyellr88/marm-memory"
  - "https://github.com/Mesutcydev/beet-code"
  - "https://github.com/supernovae-st/nika"
  - "https://www.yna.co.kr/view/AKR20260818061300017"
  - "https://www.itmedia.co.jp/enterprise/articles/2608/21/news019.html"
  - "https://www.technologyrecord.com/article/nordre-follo-municipality-modernises-public-hearing-workflows-with-microsoft-copilot-studio"
records:
  - "intelligence/signals/2026/08/23/regional-signal/korea/toss-llm-serving.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/korea/nomadamas-jikji.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/korea/nomadamas-k-skill.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/japan/staddress-mcp.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/japan/pgroonga-mcp.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/international/marm-memory.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/international/beet-code.yaml"
  - "intelligence/signals/2026/08/23/regional-signal/international/nika.yaml"
  - "intelligence/signals/2026/08/23/ax-case/korea/shinhan-securities-contract-agent.yaml"
  - "intelligence/signals/2026/08/23/ax-case/japan/mufg-ai-flowchart.yaml"
  - "intelligence/signals/2026/08/23/ax-case/international/nordre-follo-hearing-agent.yaml"
---

# 지금 읽을 결과

> 공개 원문에 묶인 인텔리전스 레코드 11건을 두 편의 글로 정리했습니다. AI 엔지니어링 후보 8건과 실제 업무 변화 사례 3건입니다.

# 지금 읽을 결과

공개 원문에 묶인 인텔리전스 레코드 11건을 두 편의 글로 정리했습니다. AI 엔지니어링 후보 8건과 실제 업무 변화 사례 3건입니다.

## 실제로 얻은 인텔리전스

### [지금 시험해볼 AI 엔지니어링 도구 8가지](../blog/2026/08/23/ai-engineering-radar)

- 한국: [토스증권 LLM 서빙 회고](https://toss.tech/article/tech_talk_talk_2)는 운영 장애를 읽을 자료, [Jikji](https://github.com/NomaDamas/jikji)는 문서 탐색 실험, [k-skill](https://github.com/NomaDamas/k-skill)은 필요한 스킬만 선별 검토할 후보입니다.
- 일본: [Staddress MCP](https://zenn.dev/staddress/articles/b601f14a21c5c5)와 [PGroonga MCP](https://github.com/askdkc/pgroonga-mcp)는 일본 주소·검색 요구가 생겼을 때 검토합니다. 개인정보와 데이터베이스 권한 경계를 먼저 확인해야 합니다.
- 국제: [MARM](https://github.com/Lyellr88/marm-memory), [Beet Code](https://github.com/Mesutcydev/beet-code), [Nika](https://github.com/supernovae-st/nika)는 각각 기억, 로컬 모델, 반복 워크플로의 작은 비교 실험 후보입니다.

### [AI가 업무를 바꾼 세 장면과 아직 답하지 못한 질문](../blog/2026/08/23/ax-intelligence)

- 한국 사례는 계약서 분석과 입력 초안을 에이전트가 맡고 담당자가 결과를 확인합니다. 공개된 시간 단축 수치는 클로즈드 베타 자체 보고입니다.
- 일본 사례는 자유 생성의 실패를 오ント롤로지, 지식 그래프와 사람 교정으로 줄였습니다. 90% 절감은 확정 실적이 아니라 예상치입니다.
- 국제 사례는 공청회 PDF 원본을 보존하고 AI가 요약·분류 초안을 만든 뒤 담당자가 전수 검토합니다. 감사된 시간·정확도 수치는 공개되지 않았습니다.

## 다음 행동

1. `Jikji`를 비민감 문서에서 기존 검색과 비교합니다.
2. `Nika`로 외부 쓰기가 없는 반복 요약 한 건만 재현합니다.
3. `MARM`과 기존 메모리의 동일 질의 정확도·중복률을 비교합니다.

어느 후보도 즉시 도입으로 승격하지 않았습니다.

## 근거와 한계

- 항목별 사실 SoT는 [`intelligence/signals/2026/08/23/`](https://github.com/jonsoku-dev/grok-bot/tree/main/intelligence/signals/2026/08/23)에 있습니다.
- `VERIFIED`는 공개 출처에 해당 사실·주장이 존재함을 확인했다는 뜻이며 독립 감사나 재현 성공을 뜻하지 않습니다.
- GitHub 프로젝트의 기능·보안·성능 설명은 대부분 제작자 주장입니다. 설치 전에 현재 커밋, 라이선스, 권한과 의존성을 다시 확인해야 합니다.
- 일본은 기준을 충족한 항목이 두 건뿐입니다. 숫자를 맞추기 위해 약한 후보를 추가하지 않았습니다.
