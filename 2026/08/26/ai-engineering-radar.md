---
title: "2026-08-26 AI Engineering Radar"
status: "approved"
action: "EXPERIMENT"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/26/regional-signal/"
sourceLinks:
  - "https://arxiv.org/abs/2608.22533"
  - "https://arxiv.org/abs/2608.22167"
  - "https://arxiv.org/abs/2608.23552"
  - "https://github.blog/changelog/2026-08-25-github-copilot-app-customize-tab-is-generally-available"
  - "https://github.com/github/copilot-cli/releases/tag/v1.0.81-10"
  - "https://githubnext.com/posts/knowledge-compressor/"
  - "https://openai.com/products/release-notes#CL-20260824-CODE-430"
  - "https://github.com/xhluca/session-migrate/releases/tag/v0.8.0"
  - "https://zenn.dev/demia/articles/6c1291f0dae964"
  - "https://developers.gmo.jp/technology/85730/"
  - "https://developers.gmo.jp/technology/84294/"
  - "https://zenn.dev/hissy/articles/concretecms-mcp-security"
  - "https://zenn.dev/acntechjp/articles/2ed34149089122"
  - "https://zenn.dev/fairydevices/articles/0723b8b06c1957"
  - "https://techblog.zozo.com/entry/cc-plugin-marketplace"
  - "https://techblog.zozo.com/entry/loop-engineering-prompt-tuning"
  - "https://github.com/NomaDamas/github-issue-solver/commit/ef9b85499ed4c68e111439d91c1651dd95ab9f32"
  - "https://github.com/NomaDamas/jikji/commit/12227080b7d736200aa28fd42ed4d3ab51d2b511"
records:
  - "intelligence/signals/2026/08/26/regional-signal/international/arxiv-contramem-2608-22533.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/arxiv-mcp-universe-rl-2608-22167.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/arxiv-prime-agent-2608-23552.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/github-copilot-app-customize-tab-2026-08-25.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/github-copilot-cli-v1-0-81-10.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/github-next-knowledge-compressor-2026-08-24.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/openai-codex-mcp-server-deprecated-2026-08-24.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/international/xhluca-session-migrate-v0-8-0.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/demia-agent-ui-component-library.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/gmo-conoha-vps-mcp-harness-safety.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/gmo-conoha-vps-mcp-hermes-openclaw-nanoclaw.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/hissy-concretecms-mcp-token-security.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/zenn-acntechjp-knowledge-gap-radar-routing.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/zenn-fairydevices-claude-memory-gc-skills.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/zozo-claude-code-plugin-marketplace.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/japan/zozo-loop-engineering-prompt-tuning.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/korea/github-nomadamas-github-issue-solver-jikji-markr-ef9b854.yaml"
  - "intelligence/signals/2026/08/26/regional-signal/korea/github-nomadamas-jikji-folder-index-1222708.yaml"
---

# 2026-08-26 AI Engineering Radar

> 한국·일본·국제의 검증된 AI 엔지니어링 신호와 가장 작은 다음 행동을 정리합니다.

# 2026-08-26 AI Engineering Radar

이 글은 검증된 공개 자료와 근거 레코드에서 작성했습니다. 내용을 고칠 때는 글보다 근거를 먼저 바로잡습니다.

<!-- truncate -->

## 왜 중요한가

이 글은 확인된 핵심 내용과 추천 이유, 주의할 점, 다음 단계를 함께 보여줍니다.

## 한국

### [NomaDamas/github-issue-solver](https://github.com/NomaDamas/github-issue-solver/commit/ef9b85499ed4c68e111439d91c1651dd95ab9f32) — `github-nomadamas-github-issue-solver-jikji-markr-ef9b854`

NomaDamas/github-issue-solver 커밋 ef9b854(2026-08-24T22:50:29Z)가 셀프호스트 GitHub 이슈 자동화 콘솔(Markr)에 Jikji를 붙였다(+87/−0). 이어서 문서 기록과 Jikji 프록시 강화 커밋이 같은 창 안에 있다.

- 왜 중요한가: 이슈 폴링 하네스가 에이전트 배정 전에 Jikji 발견을 콘솔에서 쓰는 경로. 로컬 검색을 이슈→PR 루프에 넣는 배치 예.
- 추천: **읽기** — 셀프호스트 이슈 솔버(Markr)가 gjc/omx/claude를 배정·PR·검증·오토머지하는 하네스에 Jikji를 콘솔·프록시로 붙인 신규 커밋. 코딩 에이전트 하네스·로컬 파일 발견 연동에 맞음. 어제 jikji GUI EXPERIMENT·오늘 folder-index READ와 다른 리포. 태그 없고 같은 창에 프록시·포털 인증 수정이 이어짐. 오토머지 서비스 기동은 EXPERIMENT/ADOPT 아님. 지리 비가중. relatedCategories는 \[\] 유지.
- 주의할 점:
  - README가 검증 후 오토머지를 명시. 실험 기동 시 머지 사고 가능.
  - 창 안 후속 커밋이 Jikji 프록시와 Markr 포털 인증을 고치고 있어 연동이 아직 굳지 않음.
  - 릴리스 태그 없음. +87 콘솔 연동만으로는 일반 설치 경로가 없음.
  - evidence가 덮어쓴 discovered 파일 뒤 재구성됨(패킷 sourceWarning).
- 다음 단계: README의 에이전트 배정·Jikji 콘솔 문장과 ef9b854 패치만 읽기. 솔버 기동·오토머지·외부 게시·SoT 쓰기 없음. folder-index 재판정 없음.

### [NomaDamas/jikji](https://github.com/NomaDamas/jikji/commit/12227080b7d736200aa28fd42ed4d3ab51d2b511) — `github-nomadamas-jikji-folder-index-1222708`

NomaDamas/jikji 커밋 1222708(2026-08-25T11:13:51Z)이 폴더 단위 GUI 인덱스 제어를 추가했다(+218/−27). /api/reindex-folder·/api/remove-folder·/api/deep-index-target와 source\_preserved \`source\_preserved=true\`인 인덱스 제거, 경로 이탈 403 테스트를 넣었다.

- 왜 중요한가: 원본 파일은 두고 중앙 인덱스 행만 접두사로 지우는 계약과, \`path=../\` 403을 에이전트 인덱스 GUI의 최소 경계로 고정.
- 추천: **읽기** — 어제 native GUI EXPERIMENT(5cfabea) 다음 커밋. 폴더 단위 reindex/remove/deep-index API와 source\_preserved·경로 이탈 403 테스트가 로컬 인덱스 위생·sandbox 경계에 맞음. sourceWarning대로 reindex-folder는 아직 루트 전체 prepare라 하위트리 재인덱스로 읽으면 안 됨. 태그 없는 커밋. 재EXPERIMENT/ADOPT 아님. 지리 비가중. relatedCategories는 \[\] 유지.
- 주의할 점:
  - reindex-folder가 폴더가 아니라 루트 전체 prepare를 호출함.
  - 창 안 릴리스 태그 없음.
  - mutation API 3종이 GUI/HTTP 공격면을 넓힘.
  - 어제 5cfabea EXPERIMENT와 같은 프로젝트 후속이라 중복 실험 가능.
- 다음 단계: 패치의 source\_preserved와 \`/api/remove-folder?path=../root1\` 403 테스트만 읽고 인덱스 삭제 경계를 대조. \`jikji find\` 재실험·외부 게시·SoT 쓰기 없음.

## 일본

### [DeMiA UI (@demia/react)](https://zenn.dev/demia/articles/6c1291f0dae964) — `demia-agent-ui-component-library`

주식회사 DeMiA가 코딩 에이전트용 UI 라이브러리 DeMiA UI를 공개했다. className/style를 받지 않는 시맨틱 props, npx @demia/react add-skill로 node\_modules 문서 경로만 Skill에 심고, 27컴포넌트에 VRT·oxlint 규칙으로 에이전트가 디자인을 깨지 못하게 한다.

- 왜 중요한가: 닫힌 prop 표면 + 패키지 동봉 Do/Don't 문서 + oxlint/VRT로 에이전트가 디자인 시스템을 다시 열지 못하게 하는 계약.
- 추천: **읽기** — 에이전트용 UI 라이브러리. semantic props만 받고 className/style 거절, Skill은 node\_modules 문서 경로만 심어 버전 고정. Agent Skills 소비 계약에 인접. 디자인 시스템 교체 근거 아님. a11y는 기계 보장 전. 코어 하네스/MCP보다 주변. 설치 EXPERIMENT 안 올림.
- 주의할 점:
  - 27컴포넌트. 접근성은 구현 가능하나 기계 보장 전이라고 적음.
  - 내부 시스템·목업 사용. 외부 품질 측정 없음.
  - 시맨틱 props가 표현력을 닫아 에이전트가 우회 인라인 스타일을 찾을 수 있음. lint가 그 구멍을 막는지 미재현.
- 다음 단계: className 거절과 Skill→dist/docs 경로 고정만 읽고 에이전트용 라이브러리 문서 전략과 대조. npx add-skill·외부 게시 없음.

### [ConoHa VPS MCP](https://developers.gmo.jp/technology/85730/) — `gmo-conoha-vps-mcp-harness-safety`

GMO인터넷이 7월 7일 낸 ConoHa VPS MCP 원격판을 Claude Code 하네스로 만든 과정을 공개했다. 규칙으로 AI가 못 벗어나게 하고, Codex·Takumi·SOC 펜테스트로 리뷰하며, 삭제는 확인·자격증명은 AI에 안 남긴다.

- 왜 중요한가: 에이전트 대면 컨트롤 플레인에서 삭제와 자격 보관을 다른 등급으로 두는 체크리스트. Skills를 MCP 절차서로 짝지어 냄.
- 추천: **읽기** — 원격 ConoHa VPS MCP를 Claude Code 하네스로 만든 인터뷰. 규칙→레일→자유 개발, Claude+Codex 교차 리뷰(자기검토 금지), Takumi, SOC 펜테스트. MCP·harness·Codex·sandboxing에 맞음. 삭제는 확인, 자격증명은 AI 쪽에 안 남김. 제품은 2026-07-07 출시(창 밖). 이 신호는 8/25 회고. VPS 기동 EXPERIMENT 아님. 벤더 '국내 최초' 비가중.
- 주의할 점:
  - 요청량·국내 최초는 벤더 서술. 미검증.
  - 리뷰 주기 2–3일·치명 이슈 소멸 1개월은 인터뷰 수치.
  - IaC vs MCP 구분은 저자 의견. 대형 인프라에 MCP를 쓰면 안 된다고 단정할 근거는 이 글뿐.
- 다음 단계: 레일 우선·교차 리뷰·삭제 확인·자격 AI 비보관 네 줄만 현재 MCP 권한과 대조. ConoHa 연동·외부 게시 없음.

### [ConoHa VPS MCP](https://developers.gmo.jp/technology/84294/) — `gmo-conoha-vps-mcp-hermes-openclaw-nanoclaw`

GMO인터넷 바바가 ConoHa VPS 원격 MCP(api.conoha.jp/vps/mcp, OAuth 2.1)로 Claude Code Opus 4.8에서 Hermes·OpenClaw·NanoClaw VPS를 만들었다. 같은 프롬프트인데 Hermes는 용어 확인, NanoClaw는 웹검색부터 했다.

- 왜 중요한가: 제품명만 주고 절차를 안 주면 같은 모델도 그라운딩 경로가 갈림. OpenClaw=호스트 광역/유출, NanoClaw=컨테이너 격리, Hermes=3층 메모리라는 저자 구분.
- 추천: **읽기** — 같은 벤더의 클라이언트 실측. Claude Code Opus 4.8이 원격 MCP로 Hermes/OpenClaw/NanoClaw VPS를 만들 때 첫 수가 다름(용어 확인 / 스타트업 스크립트 / 웹검색). Claude Code·MCP에 맞음. 자매 글 85730(하네스 안전)과 다른 아티팩트. 생성 VPS는 과금. 기동 실험 아님. 모델명 비가중.
- 주의할 점:
  - 벤더 워크스루. 스펙 숫자는 스크린샷 미재독.
  - OpenClaw를 켜면 호스트 자격 유출 위험을 저자가 명시.
  - 본문 오타 'Hermes Agentt'.
  - 원격 MCP 출시는 창 전(2026-07-07).
- 다음 단계: 세 프롬프트의 첫 수와 OAuth 2.1(클라이언트에 API 키 안 씀)만 읽기. VPS 생성·외부 게시 없음.

### [Concrete CMS MCP Server](https://zenn.dev/hissy/articles/concretecms-mcp-security) — `hissy-concretecms-mcp-token-security`

도쿄 마카루디지털 히시카와가 Concrete CMS MCP 토큰을 사이트 해시 디렉터리와 0600 파일로 나눈다. stdio는 암호화 키 권고, HTTP는 AES-256-GCM과 MCP\_API\_KEY 필수. 키체인 저장은 아직 없다. 같은 사용자 OAuth 중복 시작은 409.

- 왜 중요한가: stdio는 첫 툴 호출 때 OAuth, HTTP는 암호화 키·API 키 필수. 토큰을 채팅/스크린샷에 붙이지 말라는 운영 규칙.
- 추천: **읽기** — Concrete CMS MCP가 토큰을 사이트 해시 디렉터리·0600으로 나누고, HTTP는 AES-256-GCM+MCP\_API\_KEY 없으면 실패 닫힘. 같은 사용자 OAuth 중복은 409. MCP 로컬 보안 운영에 맞음. 권한은 승인한 CMS 사용자와 동일. 키체인 미구현. CMS 기동 EXPERIMENT 아님. 시리즈 4편.
- 주의할 점:
  - OS 키체인 미구현. 공유 머신에서 TOKEN\_ENCRYPTION\_KEY 누락 시 stdio는 경고만.
  - 권한=CMS 사용자. 넓게 승인한 토큰이 디스크에 남음.
  - 콜백·health는 공개(PKCE). 기본 레이트리밋 10/min/IP.
- 다음 단계: stdio vs HTTP 실패 닫힘과 409 락만 읽고 현재 MCP 토큰 보관과 대조. CMS 연동·외부 게시 없음.

### [Knowledge Gap Radar / Graph RAG](https://zenn.dev/acntechjp/articles/2ed34149089122) — `zenn-acntechjp-knowledge-gap-radar-routing`

액센추어 재팬 사노가 Graph RAG 구멍을 파이썬으로 찾고 Gemini 3.5 Flash-Lite와 Claude Sonnet 5에 같은 목록을 돌렸다. 우선순위가 이미 갈리면 Gemini, 다른 gap\_type 동점은 사람이 resolve\_ties를 켠 때만 Claude.

- 왜 중요한가: 비싼 모델을 기본 라우트로 두지 않는 규칙: 동점 없음/동종 동점→Gemini, 이종 동점→사람 게이트 후 Claude.
- 추천: **읽기** — 그래프 구멍은 파이썬이 찾고, 기본 리뷰는 Gemini, 이종 gap\_type 동점만 사람이 resolve\_ties를 켤 때 Claude. model routing에 맞음. 학습 분류기가 아니라 측정된 에스컬레이션. Graph RAG PoC이지 코딩 에이전트 하네스 아님. 비용 기준이 서로 달라 요금 비교 금지. 유명 컨설팅 브랜드 비가중.
- 주의할 점:
  - 시간·비용은 1회 측정이고 Gemini 문자 추정 vs Claude Code CLI 자가보고라 비교 불가.
  - 액센추어 재팬 유저 유저(有志) 개인 견해. 공식 제품 문서 아님.
  - YAML 자동 기입 없음. 구멍을 후보로만 둠.
- 다음 단계: 최종 라우터 세 갈래와 '목록에 없는 노드 금지'만 현재 모델 라우팅과 대조. Gemini/Claude 일괄 재실행·외부 게시 없음.

### [tatsuya6502/cc-skills (memory-gc)](https://zenn.dev/fairydevices/articles/0723b8b06c1957) — `zenn-fairydevices-claude-memory-gc-skills`

도쿄 Fairy Devices 고노가 Claude Code MEMORY가 썩는 문제에 대해 memory-gc·promote-knowledge 스킬을 1개월 운용했다. SessionStart lint와 주 1회 사람 승인 트리아지로 색인을 줄였고, SkillSpector 6/100 뒤 샌드박스 안내를 hardened 했다.

- 왜 중요한가: 세션마다 4–5k 토큰이던 인덱스(110파일/18.7KB)를 lint 문제만 주입하고, 팀 공유 사실은 CLAUDE.md로 promote. 완료 마커의 절반 미만만 아카이브 가능했다는 운용 수치.
- 추천: **작게 실험** — Claude Code MEMORY를 예산 인덱스로 보고 SessionStart lint와 주 1회 사람 승인 GC로 나눈 1개월 운용. Claude Code·Agent Skills·context engineering에 직접 맞음. 변이는 사람 게이트, 아카이브는 mv. 공개 MIT 플러그인(tatsuya6502/cc-skills). 회사 리포·GH 태그 아니라 ADOPT 아님. SkillSpector 6/100. 지리 비가중. relatedCategories는 \[\] 유지.
- 주의할 점:
  - 플러그인은 개인 리포. Fairy Devices 공식 패키지가 아님.
  - GH 릴리스 태그 없음. v1.0.0/1.0.1은 changelog·커밋.
  - 오분류 ARCHIVE/DELETE 제안이 사람 승인 전에도 목록에 올라옴.
  - 운용 수치(110→70 live)는 1프로젝트 1개월.
- 다음 단계: 폐기 가능한 Claude Code 프로젝트에 memory-gc만 설치해 SessionStart lint 한 줄과 제안 테이블이 변이 없이 끝나는지 확인. 일괄 승인·외부 게시·SoT 쓰기 없음.

### [ZOZO Claude Code plugin marketplace](https://techblog.zozo.com/entry/cc-plugin-marketplace) — `zozo-claude-code-plugin-marketplace`

ZOZO가 2025-07부터 수백 명 Claude Code 제도를 열고, 팀마다 쌓인 Skill·Agent를 하나의 플러그인 마켓플레이스로 모았다. marketplace.json을 plugin.json에서 자동 생성하고, 정적 검증·의도 역검색·@claude 영향 체크로 공동 운영 5문제를 막는다.

- 왜 중요한가: Skill/Agent/Hook/MCP를 한 플러그인으로 묶고, 머지를 릴리스로 쓰는 공동 운영 체크리스트. 누락 등록·구조 오류 전팀 전파를 생성+검증으로 막음.
- 추천: **읽기** — 다팀 Claude Code 플러그인 마켓의 카탈로그 계약: marketplace.json 자동 생성, 버전=git SHA, 팀 디렉터리 소유권, 정적 검증·의도 역검색·@claude 영향 체크. Claude Code·Agent Skills 조직 레지스트리에 직접 맞음. 내부 카탈로그라 설치 EXPERIMENT/ADOPT 아님. 수백 명 제도는 규모 서술이지 품질 가중 아님. relatedCategories는 \[\] 유지.
- 주의할 점:
  - 효과(가시성·재사용·온보딩)는 저자 주장. 재사용률 미측정.
  - 내부 /cc-plugin-marketplace. 이 글만으로 재현 설치 불가.
  - SHA=버전은 머지마다 전 플러그인 소비자가 갱신 대상이 될 수 있음.
- 다음 단계: marketplace.json 생성·SHA 버전·소유 디렉터리 세 줄만 현재 스킬 배치와 대조. 마켓 구축·외부 게시 없음.

### [ZOZO WEAR /tune prompt-tuning skill](https://techblog.zozo.com/entry/loop-engineering-prompt-tuning) — `zozo-loop-engineering-prompt-tuning`

ZOZO WEAR 데이터사이언스부가 사람 손의 VLM 프롬프트 튜닝 루프를 Claude Code /tune 스킬의 analyzer·planner·improver·retrospector 서브에이전트로 옮겼다. T1에서 F1이 인력과 동등 이상(train +0.024, test +0.017, N=1), 공수는 약 3.5주에서 약 1주.

- 왜 중요한가: 스킬을 더 좋은 프롬프트가 아니라 정책 파일(optimization-policy.md)과 lessons.md를 가진 루프 오케스트레이터로 쓰는 패턴.
- 추천: **읽기** — 사람 실패분석→개서→재평가 루프를 /tune 스킬이 analyzer·planner·improver·retrospector에 1:1로 옮김. SKILL.md는 스케줄러(115줄). Agent Skills·evaluation·Claude Code 서브에이전트에 맞음. T1 F1은 N=1. 공수 3.5주→1주는 저자 보고. VLM 튜닝 재실행 EXPERIMENT 아님. 수치 과대평가 금지.
- 주의할 점:
  - T1 F1 +0.024/+0.017은 N=1.
  - T1–T3 전이는 같은 팀 스키마. 일반 최적화기 아님.
  - 에이전트 설계는 사람이 이미 푼 루프를 이식하는 데서 시작한다고 저자가 적음. 루프가 없으면 스킬만으로 안 됨.
- 다음 단계: SKILL.md 오케스트레이터 vs 정책 파일 vs lessons.md 역할만 읽고 현재 스킬 구조를 대조. VLM 재튜닝·외부 게시 없음.

## 국제

### [CONTRAMEM](https://arxiv.org/abs/2608.22533) — `arxiv-contramem-2608-22533`

CONTRAMEM은 학습 없이 같은 작업의 성공·실패 궤적을 대조해 Function Card·Skill Card 절차 기억을 만드는 프레임워크. GAIA2/ARE 컴퓨터 사용 과제에서 세 소스 모델 성공률을 26.2%에서 55.3%로 올렸고, 같은 뱅크가 Qwen3.7 Plus로 이전된다고 적는다.

- 왜 중요한가: append-only 기억 대신 대조로 절차 카드를 압축. 이질 멀티모델 궤적이 자기 롤아웃보다 낫다는 가설.
- 추천: **읽기** — 학습 없이 같은 작업의 성공·실패 궤적을 대조해 Function Card·Skill Card를 만드는 프레임워크. Agent Skills·computer use·context에 인접. 26.2%→55.3%와 Qwen 전이는 논문 보고. 모델명 비가중. 공개 설치 경로가 이 패킷에 없어 EXPERIMENT 아님.
- 주의할 점:
  - 성공률 배증은 GAIA2/ARE·AppWorld 저자 보고. 미재현.
  - 잘못된 실패 궤적을 카드로 증류하면 절차 기억이 오염됨.
  - 모델 마케팅명을 품질 가중으로 쓰면 안 됨.
- 다음 단계: Function Card vs Skill Card와 대조 증류 문장만 읽고 현재 스킬/메모리 축적 방식과 대조. 궤적 수집·외부 게시 없음.

### [MCP-Universe RL](https://arxiv.org/abs/2608.22167) — `arxiv-mcp-universe-rl-2608-22167`

MCP-Universe RL이 MCP 서버를 환경 인터페이스로 쓰는 오픈소스 RL 프레임워크를 제시. 컨테이너로 MCP 환경을 격리·재사용하고, 툴 대기 중 GPU를 겹쳐 굴리며 veRL·slime 백엔드로 gpt-oss-20b를 소프트웨어 엔지니어링·딥리서치·일반 툴사용에서 학습했다고 적는다.

- 왜 중요한가: 이미 MCP인 툴을 RL 전용 어댑터 없이 학습에 붙이는 패턴. 환경 프로비저닝과 stalled-tool overlap을 분리.
- 추천: **읽기** — MCP 서버를 RL 환경 인터페이스로 쓰고 컨테이너로 격리·재사용, 툴 대기 중 GPU 롤아웃을 겹침. MCP·sandboxing·evaluation에 인접. 보상 이득은 gpt-oss-20b 저자 보고. 새 MCP 스펙 아님. 학습 프레임이라 코딩 에이전트 운영 기본값 교체 아님. relatedCategories는 \[\] 유지.
- 주의할 점:
  - task reward 향상은 미재현.
  - 소속은 공개 저자 기록(Salesforce)이지 페이지 스크레이프가 아님.
  - 컨테이너 MCP 환경이 툴 권한·비밀을 학습 롤아웃에 노출할 수 있음.
- 다음 단계: 환경 오케스트레이션 vs 롤아웃 overlap 두 층만 읽고 현재 MCP 샌드박스와 대조. gpt-oss 학습·외부 게시 없음.

### [PrimeIntellect-ai/prime-agent](https://arxiv.org/abs/2608.23552) — `arxiv-prime-agent-2608-23552`

Prime Intellect가 장기 호라이즌 평가·코딩 에이전트용 오픈소스 하네스 Prime Agent를 논문으로 공개. 지속 IPython REPL(RLM), 히스토리·메모리·스킬을 보존하는 Continual Harness, 재귀 서브에이전트를 두고 ARC-AGI-3 RHAE Best@1을 30%에서 95.5%로 올렸다고 적는다.

- 왜 중요한가: 전략은 모델에 두고 실행·복구·검증·자원 회계를 하네스가 표준화하는 설계. Agents View로 데몬 세션을 사람이 봄.
- 추천: **읽기** — 장기 호라이즌 평가·코딩용 오픈소스 하네스. 지속 IPython REPL, 히스토리·메모리·스킬을 보존하는 Continual Harness, 재귀 서브에이전트. agent harness·Skills·evaluation에 맞음. ARC-AGI-3 30%→95.5%는 논문 보고. 공개 태그 v0.8.0은 창 밖이라 이 신호의 선박으로 쓰지 않음. 클론 EXPERIMENT/ADOPT 아님.
- 주의할 점:
  - 벤치 이득은 미재현 논문 수치.
  - stable v0.8.0은 창 전(2026-08-21). 창 안은 beta뿐.
  - 자기개선(self-improving) 서술을 RSI로 읽으면 안전 제한이 글에 없음.
- 다음 단계: 초록의 Continual Harness·Agents View 문장만 현재 하네스와 대조. 리포 클론·벤치 재실행·외부 게시 없음.

### [GitHub Copilot app](https://github.blog/changelog/2026-08-25-github-copilot-app-customize-tab-is-generally-available) — `github-copilot-app-customize-tab-2026-08-25`

GitHub이 2026-08-25에 Copilot 앱 Customize 탭 일반 제공을 공지. MCP 서버·플러그인·스킬·캔버스를 한 곳에서 탐색·설치하고, Featured와 유형별 섹션으로 맞춤을 고른다고 적는다.

- 왜 중요한가: Copilot 앱에서 MCP/Skills를 Featured·유형별로 고르는 UI가 공개 카탈로그 관측점이 됨.
- 추천: **지켜보기** — Copilot 앱 Customize 탭 GA. MCP·플러그인·스킬·캔버스를 한 설치 허브로 묶는 가용 공지. MCP·Agent Skills 표면에 인접하나 품질·도입 측정 없음. Codex/Claude Code/Grok 교체 근거 아님. 같은 날 CLI 대시보드와는 별 표면. 브랜드·트렌딩 복제 비가중. relatedCategories는 \[\] 유지.
- 주의할 점:
  - Featured/trending·Azure DevOps 캔버스 예시는 벤더 카피이며 이 패스에서 미실행.
  - Atom updated와 RSS pubDate가 수분 차이.
  - 가용 공지를 스킬/MCP 품질 신호로 읽으면 과대평가.
- 다음 단계: Changelog 문장만 읽고 MCP/Skills가 앱 맞춤 유형으로 올라왔는지 확인. 앱 설치·외부 게시 없음.

### [github/copilot-cli](https://github.com/github/copilot-cli/releases/tag/v1.0.81-10) — `github-copilot-cli-v1-0-81-10`

Copilot CLI 1.0.81-10이 /plugin·/mcp·/skills 플러그인 대시보드를 전원에게 열고 /plugins를 제거. Auto mode가 대화 중 모델 선택을 바꾸고, --no-sandbox가 엔터프라이즈 정책 미확인으로 무시될 때 안내 문구를 고친다고 적는다.

- 왜 중요한가: 세션 안에서 모델이 바뀌는 Auto mode와 /plugin 업데이트 배지를 CLI 라우팅·스킬 운영 체크리스트에 넣음.
- 추천: **읽기** — Copilot CLI가 /plugin·/mcp·/skills 대시보드를 열고 Auto mode가 대화 중 모델 선택을 바꾼다고 명시. 모델 라우팅·MCP·Skills 표면에 맞음. --no-sandbox 안내가 정책 미확인을 정정. 1.0.81-N 트레인이고 hooks/LSP 토글은 일시 제거. 앱 Customize 탭과 별개. 기본 스택 교체 아님.
- 주의할 점:
  - prerelease 스타일 1.0.81-N. Auto mode 라우팅은 미재실행.
  - 훅·LSP enable/disable이 제거된 /plugins에만 있어 일시 불가.
  - 엔터프라이즈 정책 미확인 시 --no-sandbox가 무시됨. 문구만 고친 것.
- 다음 단계: 노트에서 /plugin /mcp /skills 이동과 Auto mode·sandbox 안내만 읽기. CLI 업그레이드·외부 게시 없음.

### [GitHub Next / Knowledge Compressor](https://githubnext.com/posts/knowledge-compressor/) — `github-next-knowledge-compressor-2026-08-24`

GitHub Next가 2026-08-24에 Knowledge Compressor 프로토타입을 공개. 기술 문서 토큰을 반복 압축해도 모델이 지식을 쓸 수 있는지 시험하며, 전형적 기술 문서는 토큰을 절반으로 줄여도 유용성이 크게 떨어지지 않았다고 적는다.

- 왜 중요한가: 전형적 기술 문서가 절반 토큰에서도 모델에 쓰일 수 있다는 가설을 컨텍스트 예산 논의에 넣음.
- 추천: **읽기** — GitHub Next가 기술 문서를 반복 압축해 에이전트 컨텍스트 예산을 줄이는 프로토타입을 공개. context engineering에 맞음. 절반 토큰·996→480은 저자 보고이고 코딩 에이전트 벤치는 없음. HN 점수 비가중. 설치 대상 아님.
- 주의할 점:
  - 유용성 유지·996→480은 프로토타입 저자 보고. 코딩 작업 성공률과 무관.
  - datetime 12:00:00Z는 noon 기본값일 수 있음.
  - 과압축이 절차·경고를 지울 수 있음.
- 다음 단계: 본문 가설과 996→480 예시만 읽기. 문서 압축 파이프·외부 게시 없음.

### [OpenAI Codex](https://openai.com/products/release-notes#CL-20260824-CODE-430) — `openai-codex-mcp-server-deprecated-2026-08-24`

OpenAI가 2026-08-24 릴리스 노트에서 Codex의 \`codex mcp-server\` 명령을 폐기한다고 공지. 대체는 Codex app server이며, Claude Code에서 Codex를 쓰려면 Codex plugin for Claude Code를 쓰라고 적는다.

- 왜 중요한가: Codex를 MCP 서버 CLI가 아니라 app server/Claude Code 플러그인으로 붙이는 방향이 고정됨. 기존 mcp-server 설정을 폐기 대상으로 표시.
- 추천: **읽기** — 공식 Codex가 \`codex mcp-server\`를 폐기하고 Codex app server로 대체. Claude Code에서는 Codex plugin을 쓰라고 적음. Codex·MCP·Claude Code 상호운용에 직접 맞음. 마이그레이션 매트릭스·호환 측정은 없음. 대체 경로 미실행이라 EXPERIMENT/ADOPT 아님. 이 핸드오프에 korea/japan 대응 없음.
- 주의할 점:
  - RSS 시각이 자정이라 당일 시각 미확인.
  - app server와 Claude Code 플러그인 동작은 이 패스에서 미실행.
  - 폐기만 있고 호환 매트릭스가 없음.
- 다음 단계: 릴리스 노트와 learn.chatgpt changelog 문장만 현재 Codex MCP 설정과 대조. 이전 실행·외부 게시 없음.

### [xhluca/session-migrate](https://github.com/xhluca/session-migrate/releases/tag/v0.8.0) — `xhluca-session-migrate-v0-8-0`

session-migrate 0.8.0이 Muse Code 0.2.1·Qwen Code 0.22.1·Kimi Code 0.38.0를 양방향 1급 포맷으로 추가. 11개 네이티브 포맷, 121개 경로, 세 하네스의 OpenRouter continuation gate, 자격증명 비이관을 명시한다. Cursor는 experimental·text-only로 남긴다.

- 왜 중요한가: Claude/Codex 말고 Muse/Qwen/Kimi 세션을 같은 CLI로 옮기는 경로가 생김. OpenRouter continuation gate를 세 하네스에 명시.
- 추천: **읽기** — 어제 v0.7.1 READ(제목 전송) 다음 태그. Muse·Qwen·Kimi를 양방향 1급으로 넣고 11 포맷·121 경로를 주장. 하네스 상호운용은 맞으나 경로 수·코퍼스는 프로젝트 보고. 자격증명 비이관·Cursor experimental 유지. 중복 IGNORE 아님. 실세션 이주는 올리지 않음. 스타 비가중.
- 주의할 점:
  - 121 경로·558+33 코퍼스는 미재실행 프로젝트 수치.
  - Cursor는 experimental·text-only. 자격증명은 의도적으로 미이관.
  - 실세션 이주는 프롬프트가 다른 하네스 로그로 새어 나갈 수 있음.
- 다음 단계: v0.8.0 노트의 신규 3포맷·자격증명 비이관만 읽고 v0.7.1과 델타 확인. 실세션 이주·외부 게시 없음.

## 판단

각 항목의 행동과 이유는 위에 표시했습니다. 도입은 별도 승인과 가장 작은 실험을 통과한 뒤에만 검토합니다.

## 한계

`VERIFIED`는 공개 원문에 해당 주장이 존재함을 확인했다는 뜻이며, 성과와 안전성을 독립 감사했다는 뜻이 아닙니다.

## 근거

각 항목은 검증된 근거 레코드와 독자가 직접 열 수 있는 공개 원문에 연결되어 있습니다.
