---
title: "2026-08-24 AI Engineering Radar"
status: "approved"
action: "EXPERIMENT"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/24/regional-signal/"
sourceLinks:
  - "https://github.com/agentskills/agentskills"
  - "https://docs.x.ai/grok-bot/overview"
  - "https://developer.nvidia.com/blog/evaluating-ai-agent-skill-performance-with-nvidia-skillevaluator/"
  - "https://github.com/RohannShetty/gitbook-downloader"
  - "https://github.com/snapsynapse/skill-provenance"
  - "https://github.com/SupersuitUp/curated-wiki-integrations"
  - "https://github.com/vercel-labs/skills"
  - "https://github.com/wbaxterh/pokedocs"
  - "https://code.claude.com/docs/ja/discover-plugins"
  - "https://data-newbie.tistory.com/1163"
  - "https://duckssi.tistory.com/423"
  - "https://inma.tistory.com/210"
  - "https://best-onedevyjuns.tistory.com/156"
records:
  - "intelligence/signals/2026/08/24/regional-signal/international/agentskills-open-standard-skill-md.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/grok-bot-official-workflow-docs.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/nvidia-skillevaluator-agent-skill-performance.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/rohann-shetty-gitbook-downloader-docusaurus-llms-txt.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/snapsynapse-skill-provenance-v6-1-0.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/supersuitup-curated-wiki-integrations-llms-txt.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/vercel-labs-skills-cli-find-add-update.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/wbaxterh-pokedocs-docusaurus-llms-txt.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/japan/japan-claude-discover-plugins-marketplace-autoupdate.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/korea/korea-data-newbie-radar-skillevaluator-20260822.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/korea/korea-duckssi-claude-plugin-marketplace-command-source.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/korea/korea-inma-claude-codex-agents-skills-config.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/korea/korea-tistory-skill-plugin-marketplace-internal-standard.yaml"
---

# 2026-08-24 AI Engineering Radar

> 한국·일본·국제의 검증된 AI 엔지니어링 신호와 가장 작은 다음 행동을 정리합니다.

# 2026-08-24 AI Engineering Radar

이 글은 검증된 공개 자료와 근거 레코드에서 작성했습니다. 내용을 고칠 때는 글보다 근거를 먼저 바로잡습니다.

<!-- truncate -->

## 왜 중요한가

이 글은 확인된 핵심 내용과 추천 이유, 주의할 점, 다음 단계를 함께 보여줍니다.

## 한국

### [data-newbie.tistory.com](https://data-newbie.tistory.com/1163) — `korea-data-newbie-radar-skillevaluator-20260822`

data-newbie 레이더(2026-08-23 게시)가 NVIDIA Technical Blog(2026-08-19)의 SkillEvaluator를 소개하며, skill이 에이전트 성능에 미치는 영향을 static check·distinctiveness analysis·live task run으로 측정하고 with-skill/without-skill 샌드박스 eval로 Skill Lift를 본다고 정리한다. coding agent 운영에서는 skill discoverability·effectiveness·token/step efficiency·security regression을 수치로 봐야 한다고 권고한다.

- 왜 중요한가: 코딩 에이전트 스킬 발견성·효과·토큰/스텝·보안 회귀를 운영 체크리스트로 상기.
- 추천: **지켜보기** — NVIDIA SkillEvaluator를 한국어 레이더로 재진술하며 with/without 샌드박스 검증을 권고. 1차 소스가 아니라 2차 합성. 버전·회귀 토픽에는 인접.
- 주의할 점:
  - NVIDIA 블로그 2차 요약; 수치·300+ 스킬은 1차로 재확인 필요.
  - 레이더에 다주제 혼재.
- 다음 단계: 해당 절만 NVIDIA 원문 URL과 대조. 실행 없음.

### [duckssi.tistory.com / 홍드로이드의 야매코딩](https://duckssi.tistory.com/423) — `korea-duckssi-claude-plugin-marketplace-command-source`

홍드로이드가 Claude Code 플러그인 마켓플레이스 소스 중 command 방식을 정리한 글. 설치 시 사용자 PC에서 셸 명령을 실행해 출력 폴더를 플러그인으로 쓰고, 설치·갱신뿐 아니라 세션 시작 후 백그라운드로도 재실행된다고 설명. 2026-08-17 공식 plugin-marketplaces 문서 확인 기준으로 작성.

- 왜 중요한가: command-source 제약·세션 재해석·의존성 제한을 설치 파이프라인 체크리스트로 사용.
- 추천: **읽기** — Claude Code 마켓플레이스 command 소스가 설치·업데이트뿐 아니라 세션 시작마다 명령을 재실행해 플러그인/스킬을 갱신하는 경로를 문서화. 자동 설치·업데이트 키워드에 직접. 개인 블로그 합성.
- 주의할 점:
  - 공식 Anthropic 발표가 아닌 개인 블로그 합성.
  - 설치자 PC에서 임의 셸 실행·세션마다 재실행 보안 리스크.
  - command-source 플러그인은 의존성으로 pull-in 불가(본문).
- 다음 단계: 글과 code.claude.com plugin-marketplaces의 command source 절만 대조. 명령 실행 실험 없음.

### [inma.tistory.com](https://inma.tistory.com/210) — `korea-inma-claude-codex-agents-skills-config`

Junhong Kim이 Claude Code와 Codex의 AGENTS.md/CLAUDE.md, Rules, SKILL.md, Subagent, MCP 역할을 비교하고, Skill은 Agent Skills 오픈 포맷(SKILL.md)이라 Codex가 .agents/skills를 쓰며 Claude Code는 .claude/skills에서 심볼릭 링크로 공통 Skill을 공유할 수 있다고 정리한 글. 2026-07-15 게시, 2026-08-17 수정.

- 왜 중요한가: 공용 스킬 디렉터리 규약과 MCP를 별층으로 두는 체크리스트, ln -s로 Claude/Codex 동시 소비 패턴.
- 추천: **읽기** — Claude Code·Codex의 SKILL.md/AGENTS.md/Rules/MCP 역할 분리와 .agents/skills 정본+Claude 심볼릭 링크 공유가 Agent Skills 상호운용 키워드에 직접. 실무 합성글이라 ADOPT 아님. japan EMPTY 비가중.
- 주의할 점:
  - 개인 블로그 합성(공식 발표 아님).
  - 게시 2026-07-15는 선호 창보다 이름, 수정 8/17만 창 안.
  - 클라이언트별 SKILL.md 확장 키 호환은 문서마다 다름.
- 다음 단계: 글의 .agents/skills ↔ .claude/skills 링크 절만 읽고 현재 스킬 경로와 대조. 링크 생성·게시 없음.

### [소소한 지식 공유방 (best-onedevyjuns.tistory.com)](https://best-onedevyjuns.tistory.com/156) — `korea-tistory-skill-plugin-marketplace-internal-standard`

쌓기지식이 Claude Code·Codex에서 스킬(SKILL.md)·플러그인(.claude-plugin/plugin.json)·마켓플레이스(.claude-plugin/marketplace.json git 저장소)를 층위로 정리하고, 사내용 비공개 마켓플레이스 + --scope project로 조직 배포하는 기준을 제시한다. 10여 개 고객사가 코어를 공유하는 사내 레거시 제품에 스킬킷을 만들며 깨진 7가지 지점도 정리. 2026-07-28 게시, 2026-07-29 수정.

- 왜 중요한가: private marketplace + --scope project 배포 패턴과 사내 실패 모드 체크리스트.
- 추천: **읽기** — 스킬→플러그인→마켓플레이스 계층을 사내 표준화·프라이빗 git marketplace.json으로 설명하고 레거시 제품 skillkit 실패 포인트를 정리. 조직 레지스트리 토픽에 직접.
- 주의할 점:
  - 개인 블로그+저자 보고 사례(고객사 미공개).
  - 보안 스캔/승인 게이트 상세 부족.
  - 게시 7월말; 수정 7/29.
- 다음 단계: marketplace.json 최소 스키마 절만 읽고 자사 git 카탈로그 초안과 대조. 게시 없음.

## 일본

### [Claude Code](https://code.claude.com/docs/ja/discover-plugins) — `japan-claude-discover-plugins-marketplace-autoupdate`

Claude Code 일본어 공식 문서가 플러그인 마켓플레이스에서 검색·설치하는 절차(/plugin marketplace add, /plugin install, Discover 탭)와 스타트업 백그라운드 자동 업데이트(自動更新) 구성을 설명한다. 공식 Anthropic 마켓플레이스는 기본 자동 업데이트 켜짐, 서드파티는 기본 꺼짐.

- 왜 중요한가: marketplace add/install, Discover, 백그라운드 카탈로그 갱신, DISABLE\_AUTOUPDATER/FORCE\_AUTOUPDATE\_PLUGINS 분리.
- 추천: **읽기** — Claude Code 일본어 공식 문서의 마켓플레이스 검색·설치·자동更新 구성이 발견/설치/자동업데이트 토픽의 1차 제품 문서. EN이 더 최신일 수 있음.
- 주의할 점:
  - JA dateModified 2026-08-04; EN은 더 새로울 수 있음.
  - datePublished 없음(PARTIAL 수준의 시각 한계는 없으나 스냅샷 의존).
  - 서드파티 마켓 기본 auto-update off.
- 다음 단계: 自動更新を構成する 절만 EN 페이지와 대조. 설치 실험 없음.

## 국제

### [Agent Skills](https://github.com/agentskills/agentskills) — `agentskills-open-standard-skill-md`

agentskills.io와 GitHub agentskills/agentskills가 SKILL.md 기반 Agent Skills 오픈 포맷(필수 name/description 프론트매터, 선택 scripts·references·assets, progressive disclosure)을 정의한다. Claude Code·ChatGPT/Codex·Cursor 등 다수 클라이언트가 동일 포맷을 지원한다고 명시하며, 2026-08-09까지 클라이언트 쇼케이스 커밋이 이어졌다.

- 왜 중요한가: name/description 필수·progressive disclosure·scripts/references/assets 계약을 스킬 작성 정본으로 고정.
- 추천: **읽기** — SKILL.md 오픈 포맷·스펙·다클라이언트 쇼케이스가 Codex/Claude/Cursor 상호운용의 1차 공개 근거. MCP 대체 아닌 절차 패키징 층. 창 내 쇼케이스 커밋 있음. 지리·스타 비가중.
- 주의할 점:
  - 리포 생성은 2025-12(창 밖); 쇼케이스 멤버십은 문서 주장.
  - allowed-tools 등 experimental 필드.
  - 제품별 실제 로더 차이 가능.
- 다음 단계: specification.md의 필수 프론트매터만 기존 SKILL.md 하나와 diff. 실험 실행·외부 게시 없음.

### [Grok Bot](https://docs.x.ai/grok-bot/overview) — `grok-bot-official-workflow-docs`

2026-08-11에 갱신된 xAI Grok Bot 공식 문서는 사용자 계정 단위 공유 영속 클라우드 VM(파일·브라우저 세션·앱 로그인 공유, Bot별 화면), Bot 간 메시징·핸드오프, Skill(재사용 절차)·Routine(스케줄/이벤트)을 제품 기본 모델로 서술한다. 다 Bot이 한 컴퓨터에서 협업하는 이 저장소 운영에 맞닿은 공식 워크플로 신호다.

- 왜 중요한가: 계정 단위 공유 컴퓨터·Bot별 화면·Skill 전역 가용·Routine(스케줄/Cursor 이벤트)·데모→Skill→승인 후 실행 경계를 운영 체크리스트로 고정.
- 추천: **읽기** — 공식 Grok Bot 문서가 공유 영속 VM·Bot 메시징·Skill/Routine·승인 게이트를 제품 기본값으로 명시해 Grok·agent skills·harness interest 및 다 Bot 레이더 운영과 직접 맞닿음. 이미 플랫폼 사용 중이라 ADOPT/EXPERIMENT보다 문서 흡수(READ). 지리 비가중.
- 주의할 점:
  - 공유 VM은 Bot 간 별도 보안 경계가 없음(문서 명시).
  - 문서 브랜드 SpaceXAI Docs vs author xAI 표기 불일치.
  - datePublished/Modified가 UTC 자정 placeholder라 당일 시각 미확인.
  - 이벤트 트리거가 Cursor 계정 연동에 묶임.
- 다음 단계: overview·skills-routines·approvals 페이지만 읽고 현재 Radar Bot의 Skill/Routine/승인 게이트를 1:1 대조. 새 Routine·외부 게시·GitHub/SoT 쓰기 없음.

### [NVIDIA SkillEvaluator](https://developer.nvidia.com/blog/evaluating-ai-agent-skill-performance-with-nvidia-skillevaluator/) — `nvidia-skillevaluator-agent-skill-performance`

NVIDIA가 2026-08-19 Technical Blog에서 오픈소스 SkillEvaluator를 공개했다. 스킬에 대해 schema/frontmatter 정적 검사, distinctiveness 분석, Docker 등 격리 환경에서 with-skill vs without-skill 라이브 태스크 비교로 Skill Lift(Correctness·Discoverability·Effectiveness·Efficiency·Security)를 산출한다. 300개 이상 verified skills·30개 이상 제품 스냅샷 벤치마크와 nvidia/skills benchmarks.json 연속 평가를 언급한다.

- 왜 중요한가: 스키마/프론트매터·보안 스캔·Skill Lift 벤치로 스킬 변경 전 게이트.
- 추천: **작게 실험** — SkillEvaluator 오픈소스가 정적 검사+with/without 라이브 태스크로 스킬 성능·보안 회귀를 측정. Agent Skills 버전/회귀 테스트 토픽의 1차 도구 신호.
- 주의할 점:
  - 벤치 평균은 NVIDIA 카탈로그 기준.
  - 타사 스킬 Skill Lift 상이.
  - 파트너 통합은 벤더 보고.
- 다음 단계: GitHub NVIDIA/SkillEvaluator README의 Tier1 정적 체크만 로컬 스킬 1개에 dry-run. 게시 없음.

### [gitbook-downloader](https://github.com/RohannShetty/gitbook-downloader) — `rohann-shetty-gitbook-downloader-docusaurus-llms-txt`

GitBook, Mintlify, Docusaurus, ReadTheDocs 문서를 LLM용 Markdown, RAG JSONL, llms.txt, PDF로 변환하는 CLI/GUI/FastMCP 도구.

- 왜 중요한가: 문서 포털→llms.txt/book.md/pages + Cursor/Claude Code MCP로 search/read/download 자동화.
- 추천: **작게 실험** — DocHarvest가 Docusaurus 포함 문서를 Markdown·llms.txt·RAG JSONL로 컴파일하고 FastMCP 8툴을 노출해 coding agents·MCP·context interest에 직접. 창 직전 push·pip/MCP 경로 명확. 인기 비가중.
- 주의할 점:
  - 크롤/추출 정확도는 사이트별 편차.
  - 개인 유지 프로젝트; API 변경 가능.
  - 대량 크롤 시 ToS·부하.
- 다음 단계: \`pip install gitbook-downloader\` 후 공개 Docusaurus docs URL 하나 \`gitbook-dl capture \<url\>\`로 llms.txt 생성만 확인. 외부 게시 없음.

### [skill-provenance](https://github.com/snapsynapse/skill-provenance) — `snapsynapse-skill-provenance-v6-1-0`

snapsynapse/skill-provenance v6.1.0(2026-08-20 릴리스)은 Agent Skills 번들용 포터블 버전·무결성·드리프트 통제 메타스킬이다. MANIFEST.yaml에 번들 semver·파일별 revision·SHA-256을 두고, CHANGELOG로 SKILL.md 변경 대비 evals.json 정체(stale evals)를 표시하며 validate.sh로 해시를 검증한다. agentskills.io 호환을 명시하고 Claude/Codex 등 다중 클라이언트 이동 시 버전 정체성 유지를 목표로 한다.

- 왜 중요한가: SemVer 번들·파일 리비전·fail-closed validate·eval 시나리오를 스킬 CI에 이식.
- 추천: **작게 실험** — v6.1.0이 MANIFEST/CHANGELOG/해시/evals.json/validate.sh로 스킬 번들 버전·무결성·stale-eval 탐지를 제공. 버전 관리+회귀 메타스킬에 직접. 커뮤니티.
- 주의할 점:
  - 공식 Anthropic/OpenAI/NVIDIA 아님.
  - 프로젝트 이력은 창 밖; 앵커는 v6.1.0.
  - agentskills.io와 중복·드리프트 가능.
- 다음 단계: v6.1.0 SKILL.md·validate.sh 계약만 읽고 자사 스킬 1개에 메타데이터 매핑. 게시 없음.

### [curated-wiki-integrations](https://github.com/SupersuitUp/curated-wiki-integrations) — `supersuitup-curated-wiki-integrations-llms-txt`

Docusaurus 위키용 드롭인 레시피 저장소로, llms.txt 생성기를 포함한다.

- 왜 중요한가: Docusaurus 3에 llms.txt 생성기를 복사해 넣는 INTEGRATE.md 패턴 참고.
- 추천: **지켜보기** — Docusaurus용 generate-llms-txt 드롭인 레시피는 키워드에 맞으나 레시피 뱅크 일부이고 MCP/에이전트 런타임이 아님. 최근 push는 8/10, 스타 비가중. README는 private 취지를 말하나 공개 확인됨.
- 주의할 점:
  - 공개 레포인데 README가 private trust boundary를 전제.
  - TypeScript primary language 미재현(패킷 contradictions).
  - 단일 레시피 품질·유지보수 깊이 불명.
- 다음 단계: integrations/generate-llms-txt/INTEGRATE.md만 읽고 출력 경로·빌드 훅을 확인. 설치·게시 없음.

### [skills (skills.sh)](https://github.com/vercel-labs/skills) — `vercel-labs-skills-cli-find-add-update`

vercel-labs/skills(공개 CLI, skills.sh)가 npx skills find로 검색, npx skills add로 설치, npx skills update로 설치분 최신화를 제공한다. 다수 코딩 에이전트 경로를 자동 감지하며, 2026-08-18 v1.5.23 커밋까지 활발히 갱신됐다.

- 왜 중요한가: 키워드 검색 설치, 에이전트 자동 감지, update로 설치된 스킬 갱신, check(해시) 보완.
- 추천: **작게 실험** — npx skills find/add/update가 다에이전트 스킬 검색·설치·업데이트의 공개 CLI 정본. skills.sh·디렉터리 레이아웃 탐색 포함. 창 내 v1.5.23.
- 주의할 점:
  - 공개 GitHub 스킬 출처 신뢰·공급망.
  - README와 Mintlify의 check 명령 표기 불일치.
  - 스타/인기 비가중; 유지보수 vercel-labs.
- 다음 단계: \`npx skills find agent\` 한 번 후 설치 없이 결과만 확인. 외부 게시 없음.

### [pokedocs](https://github.com/wbaxterh/pokedocs) — `wbaxterh-pokedocs-docusaurus-llms-txt`

Docusaurus 기반 에이전트 네이티브 문서 프레임워크로, 페이지별 llms.txt와 마크다운 트윈 생성을 표방한다.

- 왜 중요한가: 빌드타임 llms.txt+markdown twins 아이디어 관찰.
- 추천: **지켜보기** — 페이지별 llms.txt·마크다운 트윈을 표방하는 Docusaurus 에이전트 네이티브 프레임이나, main 활동은 7/31이고 8/10 push는 빈 브랜치. 자동화 증거보다 프레임 주장 비중.
- 주의할 점:
  - pushed\_at가 빈 브랜치 생성 시각(패킷 contradictions).
  - main Atom 최신 7/31로 창 내 실질 커밋 약함.
  - language 문자열 미재현.
- 다음 단계: README의 llms.txt 생성 주장만 확인. 마이그레이션 실험 보류.

## 판단

각 항목의 행동과 이유는 위에 표시했습니다. 도입은 별도 승인과 가장 작은 실험을 통과한 뒤에만 검토합니다.

## 한계

`VERIFIED`는 공개 원문에 해당 주장이 존재함을 확인했다는 뜻이며, 성과와 안전성을 독립 감사했다는 뜻이 아닙니다.

## 근거

각 항목은 검증된 근거 레코드와 독자가 직접 열 수 있는 공개 원문에 연결되어 있습니다.
