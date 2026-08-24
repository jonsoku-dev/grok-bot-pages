---
title: "2026-08-25 AI Engineering Radar"
status: "approved"
action: "EXPERIMENT"
artifactRole: "reader_facing_derivative"
publicationChannel: "document"
evidence:
  - "intelligence/signals/2026/08/25/regional-signal/"
sourceLinks:
  - "https://github.com/Lyellr88/marm-memory/releases/tag/v2.44.0"
  - "https://github.com/microsoft/agent-lightning/releases/tag/v1.0.1"
  - "https://openai.com/index/gpt-5-6-in-kiro"
  - "https://github.com/xhluca/session-migrate/releases/tag/v0.7.1"
  - "https://yegge.ai/essays/fences-not-sandboxes/"
  - "https://developers.cyberagent.co.jp/blog/archives/65362/"
  - "https://github.com/Nagi-Inaba/pmgs-reference/releases/tag/v0.5.0"
  - "https://github.com/shuji-bonji/pdf-reader-mcp/releases/tag/v0.12.0"
  - "https://github.com/takushio2525/tako/releases/tag/v0.7.8"
  - "https://zenn.dev/clopy/articles/codex-ignore-flags-user-skill-boundary"
  - "https://zenn.dev/estie/articles/06fc8455ae24cb"
  - "https://zenn.dev/marvelousu/articles/windows-mcp-vs-computer-use"
  - "https://zenn.dev/pepabo/articles/even-terminal-lolipop-ztl"
  - "https://zenn.dev/uehaj/articles/claude-code-supervisor-agent-view"
  - "https://github.com/NomaDamas/jikji/commit/5cfabeafaee2bbb32e10eb571bcc21e132a2cbdc"
records:
  - "intelligence/signals/2026/08/25/regional-signal/international/lyellr88-marm-memory-v2-44-0.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/international/microsoft-agent-lightning-v1-0-1.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/international/openai-gpt-5-6-in-kiro-2026-08-24.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/international/xhluca-session-migrate-v0-7-1.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/international/yegge-fences-not-sandboxes-2026-08-24.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/cyberagent-aja-pam-ai-agent-guardrails.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/github-nagi-inaba-pmgs-reference-v0-5-0.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/github-shuji-bonji-pdf-reader-mcp-v0-12-0.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/github-takushio2525-tako-v0-7-8.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/zenn-clopy-codex-ignore-user-skills.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/zenn-estie-claude-code-cockpit.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/zenn-marvelousu-windows-mcp-vs-computer-use.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/zenn-pepabo-even-g2-ztl-codex-claude.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/japan/zenn-uehaj-claude-code-supervisor-agent-view.yaml"
  - "intelligence/signals/2026/08/25/regional-signal/korea/github-nomadamas-jikji-native-gui-5cfabea.yaml"
---

# 2026-08-25 AI Engineering Radar

> 한국·일본·국제의 검증된 AI 엔지니어링 신호와 가장 작은 다음 행동을 정리합니다.

# 2026-08-25 AI Engineering Radar

이 글은 검증된 공개 자료와 근거 레코드에서 작성했습니다. 내용을 고칠 때는 글보다 근거를 먼저 바로잡습니다.

<!-- truncate -->

## 왜 중요한가

이 글은 확인된 핵심 내용과 추천 이유, 주의할 점, 다음 단계를 함께 보여줍니다.

## 한국

### [NomaDamas/jikji](https://github.com/NomaDamas/jikji/commit/5cfabeafaee2bbb32e10eb571bcc21e132a2cbdc) — `github-nomadamas-jikji-native-gui-5cfabea`

NomaDamas/jikji 커밋 5cfabea(2026-08-24T20:34:44Z)가 네이티브 Rust 관리 GUI를 추가했고(+1229/−35), 같은 날 fe2a545가 코딩 파일 본문 기본 인덱싱을 넣었다.

- 왜 중요한가: 에이전트가 ls/find/grep 크롤을 반복하지 않고 후보 slate를 한 번에 받는 로컬 검색 하네스. 본문 기본 인덱싱으로 파일명만이 아닌 코드 내용 질의 가능. GUI는 인덱스/라우트 점검용.
- 추천: **작게 실험** — 로컬 파일 발견·멀티쿼리 멀티라우트 slate(\`jikji find\`)와 SKILL.md가 context engineering·Agent Skills·agent harness에 직접 맞닿음. 창 변경은 네이티브 Rust 관리 GUI(+1229/−35)와 같은 날 코딩 파일 본문 기본 인덱싱(fe2a545). 이전 jikji@a824fb2 EXPERIMENT가 skip된 뒤의 후속 커밋이라 재판정은 유지하되, 태그 없는 커밋이라 ADOPT는 아님. 이 패킷은 korea 1/1이고 japan/international 대응 후보는 없음. 지리·인기 비가중.
- 주의할 점:
  - 창 안 릴리스 태그 없음. 커밋 단위라 CLI/GUI API가 바로 바뀔 수 있음.
  - 관리 GUI·HTTP 경로가 CLI 단독보다 공격면을 넓힘.
  - 코딩 파일 본문 기본 인덱싱이 시크릿·대용량·생성물을 포함할 수 있음.
  - 이전 a824fb2 EXPERIMENT가 skip된 같은 프로젝트 후속이라 중복 실험 가능.
- 다음 단계: 한 로컬 레포에서 \`jikji find ROOT "query" --json\` 1회와 skills/jikji/SKILL.md만 대조. GUI는 로컬 루트 관리 화면만 확인. 외부 게시·SoT 쓰기·채택 권고 없음.

## 일본

### [AJA DSP / Google Cloud PAM](https://developers.cyberagent.co.jp/blog/archives/65362/) — `cyberagent-aja-pam-ai-agent-guardrails`

사이버에이전트 계열 AJA DSP가 AI 에이전트에 클라우드 조작을 맡기면서 상시 Editor/Admin을 Google Cloud PAM JIT 승격으로 바꿨다. 조사는 Viewer로, 변경은 entitlement·승인·최대 24시간 만료로 나눈다.

- 왜 중요한가: 조사와 변경을 entitlement로 분리하는 체크리스트. Slack 승인·Terraform 관리·최대 TTL을 에이전트 클라우드 권한의 기본 형태로 고정.
- 추천: **읽기** — 프로덕션 DSP가 에이전트 클라우드 조작을 프롬프트가 아니라 Viewer 조사 / PAM JIT 변경(승인·24h)으로 나눈 사례. sandboxing·coding-agents interest와 맞닿고, 같은 창의 Yegge 펜스 에세이보다 재현 가능한 IAM 경계다. 인프라 전환이라 EXPERIMENT/ADOPT 아님. 지리·브랜드 비가중.
- 주의할 점:
  - 에이전트가 사람 자격증명을 물려받는 전제가 남아 있음.
  - PAM 승인 우회·만료 전 남용은 이 글만으로 검증되지 않음.
  - AJA SSP의 AWS TEAM 이전은 별 트랙이라 동일 패턴으로 단정하면 안 됨.
- 다음 단계: 본문의 investigate=Viewer / mutate=entitlement 표만 현재 클라우드 IAM과 대조. PAM 적용·외부 게시 없음.

### [Nagi-Inaba/pmgs-reference](https://github.com/Nagi-Inaba/pmgs-reference/releases/tag/v0.5.0) — `github-nagi-inaba-pmgs-reference-v0-5-0`

Nagi-Inaba의 PMGS Reference v0.5.0이 창 안에서 나왔다. 특허청 PMGS를 로컬 SQLite로 만들고 Codex/Claude Code용 읽기 전용 MCP·스킬을 붙이며, doctor가 모든 MCP 툴을 돌리고 3OS sdist 검증 뒤에 PyPI에 올렸다.

- 왜 중요한가: 공식 코퍼스를 버전된 로컬 DB+읽기 전용 MCP로 닫고, 검색 결과를 지시가 아닌 증거로 취급하는 계약 템플릿.
- 추천: **읽기** — 특허청 PMGS를 로컬 SQLite로 만들고 Codex/Claude용 읽기 전용 MCP·공통 스킬·doctor(전 툴 실호출)를 붙인 v0.5.0. 가치는 JPO 도메인이 아니라 evidence\_not\_instruction·not\_found 추측 금지·릴리스 전 doctor 게이트. 이전 information-accessibility-skill WATCH와 다른 리포. Claude live MCP=not\_observed, 소스 ZIP 미업로드. 3GB DB를 이유로 품질을 내리지 않되 ADOPT/EXPERIMENT는 도메인 의존이 커서 보류.
- 주의할 점:
  - Claude live MCP=not\_observed. Codex live만 verified.
  - 사용자 보유 JPO 패키지가 없으면 재현 불가. 소스 ZIP/SQLite는 업로드하지 않음.
  - author GitHub location 공백.
  - 이전 Nagi-Inaba 스킬 WATCH와 저자는 같으나 리포·계약이 다름.
- 다음 단계: README의 AI contract YAML과 doctor가 전 MCP 툴을 친다는 릴리스 게이트만 읽기. PMGS 빌드·PyPI 설치·외부 게시 없음.

### [shuji-bonji/pdf-reader-mcp](https://github.com/shuji-bonji/pdf-reader-mcp/releases/tag/v0.12.0) — `github-shuji-bonji-pdf-reader-mcp-v0-12-0`

일본 거주 shuji-bonji의 pdf-reader-mcp v0.12.0이 23일 나왔다. 텍스트 없음을 3상태로 나누고, 실제 PNG/JPEG를 주며, 스캔 PDF용 render\_page와 관측 기반 next 힌트를 추가했다.

- 왜 중요한가: 빈 문자열로 '텍스트 없음'을 뭉개지 않는 관측 계약. summarize.next는 후보만 주고 Skill이 시퀀스를 소유.
- 추천: **읽기** — 텍스트 추출을 extracted/no\_text\_layer/not\_extractable/not\_observed로 나누고, 이미지는 실제 PNG/JPEG, 스캔은 render\_page, 순서는 Skill 층. MCP와 Agent Skills 역할 분리와 맞닿음. 코딩 에이전트 코어 하네스는 아님. 같은 날 pdf-read Skill이 v0.12.0+를 요구. 도구 카탈로그 교체 근거는 아님.
- 주의할 점:
  - pdf.js+canvas는 segfault·빈 페이지로 폐기되어 렌더 경로가 WASM 의존.
  - 4MB 응답 예산으로 omitted\[\]가 늘 수 있음.
  - Skill 시퀀스가 없으면 next 힌트만으로 루프가 안 닫힘.
- 다음 단계: v0.12.0 노트와 pdf-read Skill 의존만 대조. 스캔 PDF 렌더 실험·외부 게시 없음.

### [takushio2525/tako](https://github.com/takushio2525/tako/releases/tag/v0.7.8) — `github-takushio2525-tako-v0-7-8`

지바공대 takushio2525의 에이전트 함대 터미널 tako가 24일 20:04Z에 nightly v0.7.8을 냈다. 컨테이너 없는 sessions, 화면 깜빡임 visual-test, 탭 전환 리사이즈 수정이 들어 있고 Claude Code MCP serve 경로가 그대로다.

- 왜 중요한가: 함대 탭의 리사이즈/깜빡임 관측과 컨테이너 없이 세션 목록을 보는 운영 편의. Claude Code MCP serve 경로는 유지.
- 추천: **지켜보기** — 에이전트 함대 터미널 nightly. 창 증분은 컨테이너 없는 sessions·visual-test·탭 리사이즈이지 신규 MCP가 아님. 이전 v0.7.7 WATCH를 유지. skip-ids는 v0.7.7만 있어서 중복 IGNORE는 아님. pre-release nightly라 EXPERIMENT 보류. 스타/지리가중 없음.
- 주의할 점:
  - v0.7.8은 pre-release nightly. 연속 태그(v0.7.5–7) 위 증분.
  - 자산은 macos-arm64 zip. Windows는 문서 매트릭스만.
  - MCP 경로가 릴리스 본문에 남아 있으나 이번 태그의 신규 사실이 아님.
- 다음 단계: v0.7.8 노트에서 sessions/visual-test/#932만 읽고 v0.7.7 WATCH와 델타 확인. 설치·외부 게시 없음.

### [Codex CLI user-skill boundary](https://zenn.dev/clopy/articles/codex-ignore-flags-user-skill-boundary) — `zenn-clopy-codex-ignore-user-skills`

Clopy가 Codex CLI 0.147.0에서 --ignore-user-config --ignore-rules를 켜도 $HOME/.agents/skills 본문의 마커가 그대로 나오는 대조 실험을 기록했다. 플래그만으로 사용자 스킬 격리를 단정하면 안 된다.

- 왜 중요한가: CI/평가 러너가 개발자 HOME을 물려받으면 사용자 스킬이 주입됨. 빈 HOME oracle과 카탈로그 격리를 실패 닫힘으로 고정.
- 추천: **읽기** — Codex CLI 0.147.0에서 --ignore-user-config --ignore-rules를 켜도 $HOME/.agents/skills 마커가 로드된 대조 실험. Codex·Agent Skills·evaluation·sandboxing에 직접 맞음. 플래그는 config.toml/execpolicy 층이고 스킬 카탈로그 경계가 아님. 이미 측정된 평가라 재실험으로 올리지 않음. 버전 고정 결과라 ADOPT 대상 아님.
- 주의할 점:
  - 측정은 Codex CLI 0.147.0 / 2026-08-15 1회+1회. 이후 버전에서 달라질 수 있음.
  - ignore 플래그를 스킬 격리로 오해하면 평가 오염이 남음.
  - author GitHub 미연결(패킷 sourceWarning).
- 다음 단계: 본문 대조표와 ignore 플래그 층만 현재 평가 러너 HOME/스킬 경로와 대조. 실 HOME에서 Codex 재실행·외부 게시 없음.

### [estie Cockpit (mru-cockpit)](https://zenn.dev/estie/articles/06fc8455ae24cb) — `zenn-estie-claude-code-cockpit`

도쿄 부동산테크 주식회사estie가 Claude Code 공유 컨텍스트와 Skill을 리포지토리가 아니라 팀 단위 Cockpit 한 곳에 모았다. system-map.yaml이 라우터이고, Slack @Claude로 비즈니스도 같은 입구를 쓴다.

- 왜 중요한가: 팀 단위 컨텍스트 소유와 라우터(system-map.yaml)로 창에 텍스트를 덜 넣는 패턴. Slack @Claude 입구와 사람 리뷰 고객 회신 경계.
- 추천: **읽기** — 팀이 공유 Claude Code 컨텍스트·Skill을 리포별 .claude가 아니라 Cockpit 한 곳에 두고 system-map.yaml로 제품→리포→Jira를 고른 뒤 문서를 읽게 함. Claude Code·Agent Skills·context engineering에 직접 맞음. /harvest는 pantry에만 쓰고 사람이 승격. 내부 사례(~4개월)라 설치 EXPERIMENT/ADOPT 아님. 클론 수·지리가중 없음. relatedCategories는 스키마상 \[\] 유지.
- 주의할 점:
  - stale pointer, 코드·지식 동일 PR 불가, 암묵지는 부재 시에만 드러난다고 저자가 적음.
  - self-serve vs 사람 수정은 아직 미측정.
  - Cockpit 리포(mru-cockpit)는 내부라 이 글만으로 재현 설치 불가.
  - 비즈니스 Slack @Claude 입구가 권한·비밀 경계를 글 밖으로 확장할 수 있음.
- 다음 단계: system-map.yaml 역할과 /harvest→사람 승격 규칙만 현재 Skill/컨텍스트 배치와 대조. Cockpit 복제·Slack 봇 연결·외부 게시 없음.

### [Windows-MCP vs Claude Code computer-use](https://zenn.dev/marvelousu/articles/windows-mcp-vs-computer-use) — `zenn-marvelousu-windows-mcp-vs-computer-use`

Zenn의 Tom이 같은 메모장 입력 작업을 Claude Code 내장 computer-use(5스텝, 픽셀)와 Windows-MCP UI Automation 스냅샷(2스텝, 이름 지정)으로 비교했다. 일본어 Windows에서는 PYTHONUTF8=1이 필요하고, UIA가 없는 앱은 vision으로 돌아간다.

- 왜 중요한가: UIA가 있을 때 구조화 MCP가 픽셀 computer-use보다 짧은 경로라는 대조 데이터. 일본어 Windows 인코딩 실패를 bring-up 버그로 분리.
- 추천: **읽기** — 같은 메모장 작업을 computer-use 5스텝(픽셀)과 Windows-MCP 2스텝(UIA)으로 비교한 측정. computer-use·MCP interest에 맞으나 Windows 11 1인 측정이고 UIA 없는 창은 vision으로 후퇴. PYTHONUTF8=1은 모델 문제가 아님. 이 패킷만으로 데스크톱 스택 교체 아님.
- 주의할 점:
  - 2026-08-20 Windows 11·Claude Code 데스크톱 1회 측정.
  - Claude Code 자체 창은 UIA 트리가 비어 이름 지정 실패.
  - 첫 uvx가 CONNECT\_TIMEOUT이면 툴이 등록되지 않음.
  - author GitHub location 공백(패킷 sourceWarning).
- 다음 단계: 본문 스텝 수·PYTHONUTF8=1·UIA 공백 후퇴만 읽기. Windows-MCP 설치·외부 게시 없음.

### [Even Terminal + ロリポップ！ゼロトラストリンク](https://zenn.dev/pepabo/articles/even-terminal-lolipop-ztl) — `zenn-pepabo-even-g2-ztl-codex-claude`

GMO페파보 엔지니어가 Even G2 안경에서 로리팝 ZTL로 Mac의 Codex/Claude Code 세션을 조작했다. --expose 없이 utun4에 Even Terminal 0.6.5를 묶고, iPhone ZTL IP의 200 GET /api/sessions를 남겼다.

- 왜 중요한가: 코딩 에이전트 제어면을 임시 공개가 아니라 이름 있는 제로트러스트 인터페이스에 묶는 경로. Claude는 --provider claude로 동일.
- 추천: **읽기** — Even G2가 맥에 직접 붙지 않고, 로리팝 ZTL utun4에 Even Terminal을 묶어 --expose 없이 Codex/Claude Code 세션을 조작. Codex·Claude Code·harness 원격 제어와 맞닿음. 측정은 Even Terminal 0.6.5의 200 GET /api/sessions. 안경·ZTL 전제라 EXPERIMENT 아님. 벤더·지리가중 없음. relatedCategories는 \[\] 유지.
- 주의할 점:
  - 실측은 Even Terminal 0.6.5이고 README --interface는 0.8.1 기준이라 버전 어긋남.
  - 토큰이 QR에 들어가며 공유 금지라고만 적음. 유출 시 세션 제어권 상실.
  - 기본은 같은 LAN Wi-Fi. ZTL은 대체 경로이지 일반 원격 접속 표준이 아님.
  - iPhone Even App이 중계하므로 폰 분실·앱 권한이 새 경계가 됨.
- 다음 단계: utun4 바인딩과 --expose 회피, QR 토큰 주의만 읽고 현재 원격 세션 노출면과 대조. Even/ZTL 가입·외부 게시 없음.

### [Claude Code supervisor / Agent view](https://zenn.dev/uehaj/articles/claude-code-supervisor-agent-view) — `zenn-uehaj-claude-code-supervisor-agent-view`

NTT테크노크로스 우에하라가 Claude Code supervisor 데몬(claude daemon run)과 Agent view를 실측했다. 세션은 프로세스가 아니라 transcript·roster.json이며, 서브에이전트와 백그라운드 세션을 수명·회수 경로로 구분한다.

- 왜 중요한가: 터미널을 닫아도 작업이 남는 이유와 HTTP\_PROXY가 데몬 spawn 시점에 고정되는 점을 운영 체크리스트로 둠.
- 추천: **읽기** — Claude Code supervisor 데몬과 Agent view를 v2.1.220에서 실측. 세션 단위가 프로세스가 아니라 transcript·roster.json이고 서브에이전트와 백그라운드 세션 수명이 다름. Claude Code·harness·context에 직접 맞음. 해부 글이라 설치 실험은 불필요.
- 주의할 점:
  - 실측 버전이 v2.1.220이라 이후 릴리스에서 roster/socket 경로가 바뀔 수 있음.
  - 빈 프롬프트 ← 가 세션을 백그라운드하므로 실수로 분리될 수 있음.
- 다음 단계: 글의 daemon status·roster.json·서브 vs 백그라운드 수명만 현재 Claude Code 설정과 대조. 새 데몬 기동·외부 게시 없음.

## 국제

### [Lyellr88/marm-memory](https://github.com/Lyellr88/marm-memory/releases/tag/v2.44.0) — `lyellr88-marm-memory-v2-44-0`

marm-memory v2.44.0이 코드 그래프 자동 인덱싱을 고정 폴링에서 파일시스템 워처 기반 이벤트 구동으로 바꿨다(저장·커밋·브랜치 전환·머지 후 수 초 내, 디바운스·재시작 내구성). 같은 태그의 v2.43.0은 메모리 엔티티와 코드 심볼을 모호하지 않은 증거로만 연결한다고 적는다.

- 왜 중요한가: 저장·커밋·브랜치 전환 후 수 초 내 그래프 갱신과, 추측 없는 메모리–코드 링크로 에이전트 컨텍스트 오염을 줄임.
- 추천: **작게 실험** — 로컬 퍼스트 MCP 메모리가 코드 그래프 인덱싱을 30초 폴링에서 fs/git 이벤트 구동으로 바꾸고, 메모리–심볼 링크를 모호하면 만들지 않는 fail-closed 증거로 고정. MCP·context engineering에 직접 맞음. 이전 v2.41.1 EXPERIMENT는 skip. 이번 태그는 운영적으로 다른 증분이라 중복 IGNORE 아님. 스타/지리가중 없음.
- 주의할 점:
  - 한 태그에 v2.43.0과 v2.44.0 노트가 묶여 있음.
  - 워처 누락·리스 상실·비git 디렉터리 경로가 남고 주기적 reconcile에 의존.
  - 로컬 코드 그래프가 시크릿·생성물을 인덱싱할 수 있음.
  - 이전 v2.41.1 실험이 skip된 같은 프로젝트 후속이라 중복 실험 가능.
- 다음 단계: 한 로컬 레포에 v2.44.0만 붙여 파일 저장 1회 후 그래프 갱신과 모호 심볼에서 링크가 안 생기는지만 확인. 외부 게시·SoT 쓰기 없음.

### [microsoft/agent-lightning](https://github.com/microsoft/agent-lightning/releases/tag/v1.0.1) — `microsoft-agent-lightning-v1-0-1`

Microsoft Agent Lightning v1.0.1이 Agent Lightning Skill의 첫 공식 릴리스라고 명시. 편집 가능한 에이전트와 벤치마크를 주면 코딩 에이전트가 프롬프트·도구·워크플로·모델·추론 설정을 측정 반복으로 개선하도록 안내하며, Claude Code·Codex·GitHub Copilot에 gh skill install로 설치한다고 적는다.

- 왜 중요한가: 편집 가능한 에이전트+벤치를 주면 코딩 에이전트가 측정 반복으로 최적화하는 스킬 루프. \`gh skill install microsoft/agent-lightning\` 경로가 Claude Code/Codex에 바로 붙음.
- 추천: **작게 실험** — 공식 Agent Lightning Skill 첫 릴리스가 코딩 에이전트(Claude Code·Codex·Copilot)로 다른 에이전트의 프롬프트·도구·워크플로·모델·추론을 벤치 루프로 개선하라고 명시. Agent Skills·evaluation·harness interest에 직접 맞음. 효과 수치는 미측정이고 v1.0.0 RL/SWE-bench는 창 밖이라 ADOPT 아님. 브랜드 비가중. 이 패킷은 international 5/5이며 korea 동창은 jikji 로컬 검색 하네스, japan 대응 후보는 이 핸드오프에 없음.
- 주의할 점:
  - 스킬 효과·벤치 이득·설치 성공이 이 패스에서 미측정.
  - v1.0.0 학습/SWE-bench 주장을 창 안 사실로 쓰면 안 됨.
  - 다른 에이전트를 코딩 에이전트가 고치게 하면 회귀·비용 폭주 가능.
- 다음 단계: 폐기 가능한 에이전트 한 개와 작은 벤치에 \`gh skill install microsoft/agent-lightning agent-lightning --agent \<agent\>\`만 적용해 1회 측정 루프. 외부 게시·SoT 쓰기·채택 권고 없음.

### [OpenAI / Kiro](https://openai.com/index/gpt-5-6-in-kiro) — `openai-gpt-5-6-in-kiro-2026-08-24`

OpenAI가 2026-08-24에 GPT-5.6 패밀리(Sol·Terra·Luna)를 소프트웨어 개발 에이전트 Kiro에 제공한다고 공식 발표. 스펙 기반 계획·코드베이스 컨텍스트·체크포인트 리뷰·property-based testing을 언급하고 OpenAI와 AWS가 Kiro 환경을 최적화했다고 적는다.

- 왜 중요한가: Kiro 쪽 spec/checkpoint/PBT 워크플로와 5.6 패밀리 라우팅이 공개 벤치에 나타나면 모델 라우팅 비교 재료가 됨.
- 추천: **지켜보기** — GPT-5.6 패밀리(Sol·Terra·Luna)를 Kiro 코딩 에이전트에 넣었다는 공식 가용 공지. 스펙 계획·코드베이스 컨텍스트·체크포인트·PBT는 관심사와 인접하나 가격·성능·품질 주장은 벤더 카피. Codex/Claude Code/Grok 교체 근거 아님. 모델 브랜드 비가중.
- 주의할 점:
  - 가격대비 성능·반복 횟수·품질 주장은 미측정 벤더 카피.
  - RSS 시각 12:00:00Z는 noon 기본값일 수 있음(달력 날짜는 창 안).
  - 가용 공지를 품질 신호로 읽으면 과대평가.
- 다음 단계: 공식 페이지만 읽고 spec/checkpoint/PBT 문장을 체크리스트로 옮김. Kiro 가입·모델 호출·외부 게시 없음.

### [xhluca/session-migrate](https://github.com/xhluca/session-migrate/releases/tag/v0.7.1) — `xhluca-session-migrate-v0-7-1`

session-migrate 0.7.1이 창 안에서 Claude/Pi/Codex 간 제목 지정 세션 전송(smigrate transfer --title)을 추가. 저장소 설명은 Claude Code·Codex·Pi·OpenCode·Copilot CLI·Antigravity·Cursor·Mistral Vibe 세션을 마이그레이션한다고 한다.

- 왜 중요한가: 같은 제목의 세션을 Claude↔Pi/Codex로 옮기는 최소 경로. 멀티 하네스 운영에서 대화 이력 재입력 비용을 줄임.
- 추천: **읽기** — Claude Code·Codex·Pi 등 코딩 에이전트 세션 이식 CLI. 창 안 변경은 \`--title\` 전송과 fail-closed 제목 매칭. 8 하네스 확장(v0.7.0)은 창 밖. 상호운용은 harness interest에 맞으나 자격증명/정책 미이관·포맷 호환 미재시험. 스타 수 비가중. 실세션 이주는 EXPERIMENT로 올리지 않음.
- 주의할 점:
  - 창 안 0.7.1은 제목 전송/데모 증분이고 0.7.0 하네스 확장을 창 안 사실로 쓰면 안 됨.
  - Cursor는 프로젝트도 experimental로 적혀 있고 자격증명/정책은 이관하지 않음.
  - 실세션 이주는 프롬프트·비밀이 다른 하네스 로그로 새어 나갈 수 있음.
- 다음 단계: 릴리스 노트와 \`smigrate transfer --title\` 실패 닫힘 규칙만 읽기. 실세션 이주·외부 게시 없음.

### [yegge.ai / Wheelhouse](https://yegge.ai/essays/fences-not-sandboxes/) — `yegge-fences-not-sandboxes-2026-08-24`

Steve Yegge가 2026-08-24에 에이전트 통제를 샌드박스·가드레일이 아니라 역할·규칙·절차를 명시한 '펜스'(법률 체계형 거버넌스)로 해야 한다는 에세이를 공개. 본인 Wheelhouse 소프트웨어 공장과 50–60 에이전트 클러스터에서 에이전트가 constitution·관할·판례 유사 장치를 만들었다고 1인칭 서술한다.

- 왜 중요한가: 장시간 멀티에이전트 운영에서 fence/ratchet/governor/tripwire/latch 어휘와 Slack·이메일 경계 설계를 체크리스트로 흡수.
- 추천: **읽기** — 에이전트 통제를 OS 샌드박스·가드레일이 아니라 역할·규칙·절차(펜스)로 두라는 1차 에세이. sandboxing·harness interest와 맞닿으나 재현 가능한 구현·보안 증명은 없음. 50–60 에이전트·600k LOC는 저자 서술이라 EXPERIMENT/ADOPT 아님. HN 점수 비가중.
- 주의할 점:
  - 에이전트 수·토큰·Wheelhouse 규모는 저자 보고이며 독립 검증 없음.
  - 샌드박스 포기를 권하는 것처럼 읽히면 격리 계층을 약화할 수 있음.
  - 재현 가능한 fence 구현이나 보안 증명이 없음.
  - 페이지에 시각이 없고 달력 날짜만 있음.
- 다음 단계: 에세이 본문만 읽고 현재 에이전트 하네스의 역할/채널 경계를 펜스 어휘로 1:1 대조. 클러스터 재현·외부 게시 없음.

## 판단

각 항목의 행동과 이유는 위에 표시했습니다. 도입은 별도 승인과 가장 작은 실험을 통과한 뒤에만 검토합니다.

## 한계

`VERIFIED`는 공개 원문에 해당 주장이 존재함을 확인했다는 뜻이며, 성과와 안전성을 독립 감사했다는 뜻이 아닙니다.

## 근거

각 항목은 검증된 근거 레코드와 독자가 직접 열 수 있는 공개 원문에 연결되어 있습니다.
