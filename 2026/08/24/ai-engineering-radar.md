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
  - "https://github.com/RohannShetty/gitbook-downloader"
  - "https://github.com/SupersuitUp/curated-wiki-integrations"
  - "https://github.com/wbaxterh/pokedocs"
  - "https://inma.tistory.com/210"
records:
  - "intelligence/signals/2026/08/24/regional-signal/international/agentskills-open-standard-skill-md.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/grok-bot-official-workflow-docs.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/rohann-shetty-gitbook-downloader-docusaurus-llms-txt.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/supersuitup-curated-wiki-integrations-llms-txt.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/international/wbaxterh-pokedocs-docusaurus-llms-txt.yaml"
  - "intelligence/signals/2026/08/24/regional-signal/korea/korea-inma-claude-codex-agents-skills-config.yaml"
---

# 2026-08-24 AI Engineering Radar

> 한국·일본·국제의 검증된 AI 엔지니어링 신호와 가장 작은 다음 행동을 정리합니다.

# 2026-08-24 AI Engineering Radar

이 글은 검증된 공개 자료와 근거 레코드에서 작성했습니다. 내용을 고칠 때는 글보다 근거를 먼저 바로잡습니다.

<!-- truncate -->

## 왜 중요한가

이 글은 확인된 핵심 내용과 추천 이유, 주의할 점, 다음 단계를 함께 보여줍니다.

## 한국

### [inma.tistory.com](https://inma.tistory.com/210) — `korea-inma-claude-codex-agents-skills-config`

Junhong Kim이 Claude Code와 Codex의 AGENTS.md/CLAUDE.md, Rules, SKILL.md, Subagent, MCP 역할을 비교하고, Skill은 Agent Skills 오픈 포맷(SKILL.md)이라 Codex가 .agents/skills를 쓰며 Claude Code는 .claude/skills에서 심볼릭 링크로 공통 Skill을 공유할 수 있다고 정리한 글. 2026-07-15 게시, 2026-08-17 수정.

- 왜 중요한가: 공용 스킬 디렉터리 규약과 MCP를 별층으로 두는 체크리스트, ln -s로 Claude/Codex 동시 소비 패턴.
- 추천: **읽기** — Claude Code·Codex의 SKILL.md/AGENTS.md/Rules/MCP 역할 분리와 .agents/skills 정본+Claude 심볼릭 링크 공유가 Agent Skills 상호운용 키워드에 직접. 실무 합성글이라 ADOPT 아님. japan EMPTY 비가중.
- 주의할 점:
  - 개인 블로그 합성(공식 발표 아님).
  - 게시 2026-07-15는 선호 창보다 이름, 수정 8/17만 창 안.
  - 클라이언트별 SKILL.md 확장 키 호환은 문서마다 다름.
- 다음 단계: 글의 .agents/skills ↔ .claude/skills 링크 절만 읽고 현재 스킬 경로와 대조. 링크 생성·게시 없음.

## 일본

EMPTY — 이 권역에서 기준을 충족한 검증 레코드가 없습니다.

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

### [gitbook-downloader](https://github.com/RohannShetty/gitbook-downloader) — `rohann-shetty-gitbook-downloader-docusaurus-llms-txt`

GitBook, Mintlify, Docusaurus, ReadTheDocs 문서를 LLM용 Markdown, RAG JSONL, llms.txt, PDF로 변환하는 CLI/GUI/FastMCP 도구.

- 왜 중요한가: 문서 포털→llms.txt/book.md/pages + Cursor/Claude Code MCP로 search/read/download 자동화.
- 추천: **작게 실험** — DocHarvest가 Docusaurus 포함 문서를 Markdown·llms.txt·RAG JSONL로 컴파일하고 FastMCP 8툴을 노출해 coding agents·MCP·context interest에 직접. 창 직전 push·pip/MCP 경로 명확. 인기 비가중.
- 주의할 점:
  - 크롤/추출 정확도는 사이트별 편차.
  - 개인 유지 프로젝트; API 변경 가능.
  - 대량 크롤 시 ToS·부하.
- 다음 단계: \`pip install gitbook-downloader\` 후 공개 Docusaurus docs URL 하나 \`gitbook-dl capture \<url\>\`로 llms.txt 생성만 확인. 외부 게시 없음.

### [curated-wiki-integrations](https://github.com/SupersuitUp/curated-wiki-integrations) — `supersuitup-curated-wiki-integrations-llms-txt`

Docusaurus 위키용 드롭인 레시피 저장소로, llms.txt 생성기를 포함한다.

- 왜 중요한가: Docusaurus 3에 llms.txt 생성기를 복사해 넣는 INTEGRATE.md 패턴 참고.
- 추천: **지켜보기** — Docusaurus용 generate-llms-txt 드롭인 레시피는 키워드에 맞으나 레시피 뱅크 일부이고 MCP/에이전트 런타임이 아님. 최근 push는 8/10, 스타 비가중. README는 private 취지를 말하나 공개 확인됨.
- 주의할 점:
  - 공개 레포인데 README가 private trust boundary를 전제.
  - TypeScript primary language 미재현(패킷 contradictions).
  - 단일 레시피 품질·유지보수 깊이 불명.
- 다음 단계: integrations/generate-llms-txt/INTEGRATE.md만 읽고 출력 경로·빌드 훅을 확인. 설치·게시 없음.

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
