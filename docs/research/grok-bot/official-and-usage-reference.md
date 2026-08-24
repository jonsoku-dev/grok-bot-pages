---
{}
---

# Grok Bot 공식·사용 레퍼런스

> > 기준일: 2026-08-24 (JST)
> 목적: 이 문서는 Grok Bot을 이 저장소의 제어면에 연결할 때의 제품 사실, 관찰된 사용례, 그리고 미확인 경계를 한곳에 모은다. Git의 선언값이나 로컬 UI 관찰을 제품의 공식 보장으로 바꾸지 않는다.

# Grok Bot 공식·사용 레퍼런스

> 기준일: 2026-08-24 (JST)
> 목적: 이 문서는 Grok Bot을 이 저장소의 제어면에 연결할 때의 제품 사실, 관찰된 사용례, 그리고 미확인 경계를 한곳에 모은다. Git의 선언값이나 로컬 UI 관찰을 제품의 공식 보장으로 바꾸지 않는다.

## 읽는 법과 근거 등급

- **공식**: SpaceXAI/xAI가 운영하는 Grok Bot 문서 또는 제품 페이지가 직접 말한 내용이다. 제품 변경과 계정·플랜·롤아웃 차이는 별도로 확인한다.
- **관찰/커뮤니티**: 작성자가 공개한 저장소·문서에 따른 자기 보고다. Grok Bot의 지원 기능이나 보안 보장을 뜻하지 않으며, 설치·실행 전에 소스와 권한을 독립 검토한다.
- **이 저장소에의 함의**: 위 사실과 현재 저장소의 GitOps 원칙을 결합한 운영 권고다. 제품 기능의 공식 보장은 아니다.

## 1. 제품 용어와 경계

### Bot

공식 문서에서 Bot은 이름, 역할, 개별 대화와 시간이 지나며 축적되는 작업 문맥을 가진 지속형 AI 동료다. 역할은 소유 결과물, 도구·출처, 작업 방식, 승인 경계, 반복 일정이 분명할 때 분리하라고 안내한다. Bot 설명에는 계속 유효한 책임·금지·승인 규칙을 두고, 일회성 지시는 대화에 둔다. [Create and manage Bots](https://docs.x.ai/grok-bot/bots), [Overview](https://docs.x.ai/grok-bot/overview)

대화와 역할 문맥은 Bot별이지만, 이것은 접근권한 분리가 아니다. 한 계정의 모든 Bot은 파일·브라우저 로그인·명령줄 자격증명을 공유하는 사용자 단위 컴퓨터를 쓴다. Bot을 여러 개 만들었다는 이유만으로 비밀·회사 데이터·게시 권한이 격리되었다고 판단하면 안 된다. [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps), [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy)

계정은 Bot과 그룹 채팅을 합쳐 최대 50개까지 둘 수 있다고 문서화되어 있다. Bot 삭제는 해당 프로필·대화·루틴을 제거하지만 공유 컴퓨터의 파일과 로그인까지 삭제한다는 뜻은 아니다. 숨기기는 삭제와 다르고, 숨긴 Bot의 루틴도 계속 동작할 수 있다. [Create and manage Bots](https://docs.x.ai/grok-bot/bots)

### Group(그룹 채팅)

그룹은 2~6개의 Bot에게 공통 결과물과 눈에 보이는 인수인계를 부여하는 대화 공간이다. `@Bot`으로 소유자를 지목하거나 필요할 때만 여러 Bot을 멘션할 수 있으며, Bot끼리 그룹 안에서 메시지를 주고받는다. 그룹은 협업 기록을 보존하는 수단이지 별도 실행 환경이나 보안 테넌트가 아니다. [Message and collaborate](https://docs.x.ai/grok-bot/chat-and-collaboration)

### Skill(스킬)

스킬은 반복 작업의 방법을 담는 재사용 지침이다. 공식 문서는 사용 조건, 필요한 입력·접근, 작업 순서, 검증법, 반환물, 승인 필요 작업을 포함하라고 권장한다. 스킬은 여러 Bot에서 사용할 수 있지만 해당 Bot에 커넥터·로그인이 있어야 할 수 있고, 비공개 스킬은 Bot별 활성화가 필요할 수 있다. 작성기에서 `/`로 스킬을 참조한다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

`Teach a task`가 제공되는 계정에서는 한 번의 브라우저 작업 시연으로 초안 스킬을 만들 수 있다. 기록은 최대 10분이며 마이크 오디오는 기록하지 않는다. 그러나 한 번의 시연이 실패 처리·결정 규칙·승인 경계를 충분히 포착한다고 볼 수 없으므로, 공식 문서도 초안 검토와 안전한 입력의 재시험을 요구한다. 이 기능은 점진 배포될 수 있다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

### Routine(루틴)

루틴은 **한 Bot**이 워크플로를 언제 실행할지 정하는 자동화다. 일정 기반 또는 지원되는 경우 이벤트 기반으로 동작하며, 스케줄·시간대·입력 출처·예상 결과·승인 경계·출처 부재 시 행동을 확인한 뒤 만든다. 백그라운드 루틴은 노트북이 닫혀 있어도 클라우드에서 실행될 수 있다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations), [FAQ](https://docs.x.ai/grok-bot/faq)

Bot당 루틴은 최대 50개, 최근 실행 기록은 루틴당 20개라는 문서상 한계가 있다. 테스트 실행은 실제 웹 탐색, 파일 변경, 연결 도구 호출을 할 수 있으므로 안전한 입력과 실제 승인 경계가 필요하다. 삭제는 즉시 적용되며 되돌리기가 없다고 설명한다. 장기간 부재 뒤에는 무인 실행 지속 여부를 묻거나 루틴을 일시 정지할 수 있다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

설정의 `Timezone`이 루틴 일정에 쓰인다. 공식 문서가 확인하라고 한 것은 시간대와 다음 실행이며, 일광절약시간 전환·재시도 간격·중복 방지의 세부 의미는 여기서 공개적으로 확인하지 못했다. [Settings and notifications](https://docs.x.ai/grok-bot/settings-and-notifications), [Troubleshooting](https://docs.x.ai/grok-bot/troubleshooting)

### Plugins, connectors, MCP

현재 앱에서는 지원 서비스 연결기가 **Plugins**로 표시된다. Settings → Plugins에서 마켓플레이스의 커넥터와 패키지형 스킬을 찾고, 설치 후 브라우저 인증을 완료한 다음 대화에서 `@`로 연결기를 붙인다. 설치된 커넥터는 계정 전체에 적용되며 Bot별 격리가 아니다. 구조화된 커넥터가 있으면 일반 브라우저 조작보다 신뢰성이 높을 수 있으나, 모든 화면 작업을 대체한다는 보장은 없다. [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps), [Settings and notifications](https://docs.x.ai/grok-bot/settings-and-notifications)

일반 Grok 커넥터 카탈로그는 GitHub에 대해 저장소·이슈·PR·코드를 연결 대상으로 열거하고, 공개 인터넷에서 접근 가능한 커스텀 MCP 서버를 추가할 수 있다고 설명한다. 다만 이 문서는 Grok 전체의 연결기 문서다. 따라서 **이 계정의 Grok Bot에 GitHub 커넥터가 실제로 보이고 어떤 쓰기 권한을 갖는지는 별도 관찰·승인 대상**이다. [Grok Connectors](https://docs.x.ai/grok/connectors)

이벤트 기반 루틴은 Slack 메시지나 GitHub 알림 같은 Cursor 계정 통합 이벤트로 시작될 수 있다고 명시되어 있다. 이는 Slack/GitHub 플러그인과 별도 연결 흐름일 수 있다. 넓은 이벤트 구독은 노이즈·사용량·오작동 위험을 키우므로 좁은 매칭 규칙만 권장된다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

## 2. 실행 환경, 지속성, 파일

Grok Bot의 기본 실행 환경은 계정에 할당된 지속형 클라우드 컴퓨터다. 팀 문서는 이를 멤버 전용의 관리형 Linux VM이라고 설명하고, Bot은 브라우저·터미널·파일·플러그인/MCP를 쓸 수 있다고 한다. 각 Bot에는 별도 화면이 있어 병렬 화면 작업은 가능하지만, 한 Bot의 화면에서 컴퓨터 사용 작업은 한 번에 하나다. [Teams and enterprises](https://docs.x.ai/grok-bot/teams-and-enterprises), [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps)

지속성이 보장되는 범위는 조심해서 해석해야 한다. 공식 문서는 `/workspace`의 명확한 프로젝트 폴더에 중요한 결과를 두고, 최종 결과는 대화에도 남기거나 링크하라고 권장한다. 파일·브라우저 상태·지원 로그인은 일반 업데이트·복구를 견디도록 설계되었지만, 임시 디렉터리, 수동 설치 패키지, 커밋되지 않은 애플리케이션 상태는 교체 가능하다고 명시한다. Reset은 최근의 저장되지 않았거나 동기화되지 않은 작업을 잃을 수 있다. [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps), [Files and results](https://docs.x.ai/grok-bot/files-and-results)

로컬 Mac/Windows 실행은 클라우드 VM과 별개다. 설정의 `Execution on Local Computer`에서 매번 승인·항상 허용·항상 금지를 고르고, 기본값은 매번 묻기다. 팀 문서는 첫 로컬 작업에서 동의를 받고 이후에도 Auto Review와 정확한 명령이 표시되는 승인 카드를 거친다고 설명한다. 로컬 파일·명령이 꼭 필요하지 않으면 금지하는 것이 공식 최소권한 권고와 맞는다. [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy), [Teams and enterprises](https://docs.x.ai/grok-bot/teams-and-enterprises)

## 3. 승인, 보안, 권한의 실제 경계

요청에 Bot이 할 수 있는 일과 멈출 지점을 명시해야 한다. 특히 외부 메시지·게시·구매·송금·삭제·덮어쓰기·권한 변경·프로덕션 변경·법적 약관 수락은 승인 대상으로 지정하라는 것이 공식 지침이다. 승인은 제안한 작업을 통과시키는 것이지 이미 수행한 작업을 되돌리지 않는다. [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy)

데스크톱에서는 한 번 허용/거부와 일치 규칙의 지속 허용을 제공할 수 있으며, Auto Review에서 `Require Approval`과 `Always Allow` 규칙을 설정할 수 있다. 둘이 동시에 맞으면 승인 요구가 우선한다. Auto Review는 모델 기반 보조 수단일 뿐 최소 권한과 명시적 승인 경계를 대체하지 않는다. 규칙은 현재 데스크톱과 그 Grok Bot 컴퓨터에 동기화되므로 다른 데스크톱 설치에 동일하다고 가정할 수 없다. [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy), [Settings and notifications](https://docs.x.ai/grok-bot/settings-and-notifications)

비밀번호·패스키·2FA 코드·CAPTCHA·결제 확인은 사람이 Agent Computer를 인계받아 직접 처리한다. 일반 대화에 비밀번호나 일회용 코드를 입력하지 않는다. 지원 연결기의 보안 비밀 입력은 마스킹되고 대화와 모델에서 제외된다고 명시되지만, 이는 범용 비밀번호 관리자가 아니다. [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps), [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy)

팀 문서에 따르면 호스팅 MCP의 로그인 토큰은 Cursor 백엔드에 남고 컴퓨터에는 저장되지 않는다. 반면 컴퓨터 안의 브라우저 세션·파일·명령줄 자격증명은 같은 계정의 모든 Bot이 공유한다. 커넥터를 제거하거나 출처 서비스에서 권한을 취소하고, 민감한 `/workspace` 파일과 브라우저 로그인을 직접 정리해야 한다. Bot 삭제만으로 공유 로그인·파일이 사라진다고 가정하면 안 된다. [Teams and enterprises](https://docs.x.ai/grok-bot/teams-and-enterprises), [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy)

## 4. GitHub 및 저장소 작업에 적용할 수 있는 사실

공식적으로 확인된 GitHub 관련 진입점은 두 가지다.

1. Grok의 커넥터 카탈로그는 GitHub의 저장소·이슈·PR·코드를 대상으로 든다. 이는 계정·관리자·OAuth 범위에 따라 실제 가용성이 달라질 수 있다. [Grok Connectors](https://docs.x.ai/grok/connectors)
2. Grok Bot 루틴은 지원되는 Cursor 계정 통합을 통해 GitHub 알림을 이벤트로 받을 수 있으며, 해당 흐름은 GitHub 플러그인과 구분된다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

따라서 이 저장소에서는 GitHub를 Bot의 기억이나 `/workspace`의 대체물이 아니라 **선언값·검토·불변 증거·승인된 산출물의 정본**으로 유지해야 한다. Bot이 코드를 읽거나 초안을 만들더라도 다음은 별도 증거가 필요하다.

- GitHub 연결기가 실제로 설치·인증되어 있고, 대상 저장소와 최소 범위 권한만 갖는가.
- 커밋, PR 생성, 이슈 변경, 보호 브랜치 변경 각각이 승인 카드·조직 정책·GitHub 자체 권한 중 어디에서 차단되는가.
- `/workspace`의 작업 사본과 Git 커밋 SHA가 일치하는가.
- GitHub 이벤트 트리거가 저장소·브랜치·이벤트 종류·매칭 규칙을 좁게 제한하는가.

이 네 조건을 제품 문서만으로 충족했다고 결론 내릴 수는 없다. 이 저장소의 `botctl plan → 명시 승인 → apply → 재열람 verify → runtime snapshot` 흐름은 계속 필요하다.

## 5. 자주 보이는 실제 워크플로

### 공식 안내에서 확인되는 패턴

- **하나의 결과를 맡긴 역할 Bot**: 출처·도구·반환 형식·승인 경계를 정해 한 번의 안전한 실제 작업을 수행하고, 수정된 결과가 검토 가능해진 뒤 스킬로 저장한다. 두 번째 입력에서 다시 시험한 후에만 루틴으로 승격한다. [Use cases](https://docs.x.ai/grok-bot/use-cases), [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)
- **가시적 분업**: 연구자·작성자·검토자를 그룹에 넣고, 연구자는 모든 주장에 링크를 남기고 작성자는 초안만 만들며 검토자는 차단 이슈만 돌려준다. 공식 협업 예시는 게시 금지를 명시한 상태로 이런 인수인계를 제안한다. [Message and collaborate](https://docs.x.ai/grok-bot/chat-and-collaboration)
- **검토 우선 자동화**: 일일 요약, 리스크 목록, 지원·분석 조사처럼 준비·조정·추천을 자동화하되 외부 연락·게시·구매·프로덕션 변경은 승인 뒤로 둔다. 루틴은 무자료·오래된 자료·부분 실패를 명시적으로 보고하고 재시도는 멱등적으로 설계한다. [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations)

### 공개 커뮤니티의 자기 보고 (제품 보장 아님)

- Jeff Huber의 공개 저장소는 로컬 macOS 헬퍼를 통해 iMessage를 읽고 분류·검색하며, 보내기는 미리보기와 사람 확인 뒤 AppleScript로 처리하는 스킬을 제시한다. 이는 로컬 권한(Full Disk Access, Automation)과 별도 브리지가 필요한 확장 사례이지, Grok Bot이 iMessage를 기본 지원한다는 증거가 아니다. [jeffhuber/grokbot-imessage-skill](https://github.com/jeffhuber/grokbot-imessage-skill)
- SSBrouhard의 공개 Telegram bridge는 개인이 구축한 Sand gateway 브리지이며, 자체 문서상 데스크톱 전용 설정·비밀·CAPTCHA·영구 권한은 전달하지 않는다. 이는 비공식 우회/브리지가 기능·권한·지원 범위를 제한할 수 있음을 보여주는 사례다. 이 저장소의 자동화 경로로 채택할 근거는 아니다. [SSBrouhard/grokbot-telegram-bridge](https://github.com/SSBrouhard/grokbot-telegram-bridge)
- codeaashu의 공개 `grokbot-shim`은 설치된 데스크톱 앱의 미문서 런타임을 추출해 Linux에서 에이전트 수명주기와 원격 컴퓨터 화면을 다룬다고 보고한다. 작성자도 미문서 통합 지점이 앱 변경에 따라 깨질 수 있음을 밝힌다. 그러므로 공개 사용 흔적으로만 취급하며, 내부 gateway·토큰 파일·로컬 포트·실행 경로를 이 저장소의 제품 연동 계약이나 자동화 대상으로 삼지 않는다. [codeaashu/grokbot-shim](https://github.com/codeaashu/grokbot-shim)
- SpillwaveSolutions의 공개 ContentPack은 Bot이 클라우드 작업 사본을 갖지 못할 때 구조화된 변경 제안 또는 GitHub 브랜치를 쓰도록 안내한다. 이는 한 작성자의 운영 규칙일 뿐 공식 GitHub 작업 계약이 아니다. 다만 공유 작업공간을 정본으로 취급하지 않는 보수적 패턴의 예다. [SpillwaveSolutions/account-management: GROK_BOT.md](https://github.com/SpillwaveSolutions/account-management/blob/main/docs/GROK_BOT.md)

## 6. 알려진 실패 모드와 복구 원칙

- **로그인·2FA·CAPTCHA·사람 확인**: Bot이 우회하면 안 된다. 사람이 컴퓨터를 인계받아 해당 단계만 끝낸 뒤 계속하게 한다. 세션은 만료되거나 민감 작업마다 재확인을 요구할 수 있다. [Troubleshooting](https://docs.x.ai/grok-bot/troubleshooting)
- **컴퓨터 준비/접속 실패**: Retry → 앱 재시작 → 앱 업데이트 → Recover/Update Agent Computer 순서로 복구하며, Reset은 최근 비동기화 작업을 잃을 위험이 있는 최후 수단이다. [Troubleshooting](https://docs.x.ai/grok-bot/troubleshooting)
- **루틴 미실행/부분 실패**: 활성 상태, 일정·시간대, 소유 Bot, 플러그인 인증, 출처 접속, 사용량/계정 상태, 이벤트라면 채널·저장소·매칭 규칙을 점검하고 최근 실행 기록을 본다. 테스트도 실제 부작용을 낼 수 있다. [Troubleshooting](https://docs.x.ai/grok-bot/troubleshooting)
- **웹사이트 차단**: 데이터센터 IP, 자동화 탐지, 로그인 정책으로 막힐 수 있다. 공식 문서는 커넥터가 있으면 우선하고, 사람이 요구되는 단계는 인계하며, 우회하지 말라고 한다. [FAQ](https://docs.x.ai/grok-bot/faq), [Teams and enterprises](https://docs.x.ai/grok-bot/teams-and-enterprises)
- **플러그인 인증·권한 실패**: 설치 여부, 의도한 계정의 브라우저 인증, 조직 변수/관리자 설정, 출처 서비스에서의 권한 철회를 확인한다. [Troubleshooting](https://docs.x.ai/grok-bot/troubleshooting)
- **공유 상태 오염**: 다른 Bot의 파일·로그인·명령줄 자격증명이 보일 수 있다. Bot 분리로 해결하지 말고, 필요한 계정만 로그인하고, 프로젝트 폴더를 명확히 하며, 종료 시 로그아웃·파일 제거·연결기 권한 철회를 수행한다. [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps)

## 7. 이 저장소의 공공 출처 연구 → 기록 → 편집 → 검토 → 게시 파이프라인에의 함의

이 저장소의 GitHub SoT와 runtime snapshot 분리는 제품 문서의 공유 컴퓨터 모델과 잘 맞는다. 운영 원칙은 다음과 같다.

1. **연구**: Scout는 공공 출처만 수집하고, 각 주장에 원문 URL·관찰 시각·원문 제목·사실/해석 구분·접근 실패를 남긴다. Bot 메모리나 스크린샷은 빠르게 바뀌는 사실의 정본이 아니다.
2. **기록**: GitHub SoT Writer만 스키마에 맞는 사실 레코드를 Git에 제안한다. `/workspace`는 중간 산출물 교환소일 뿐 정본이 아니며, 커밋 SHA와 입력 출처가 연결되기 전에는 `VERIFIED`나 `PUBLISHED`로 승격하지 않는다.
3. **편집**: Document Publisher는 승인된 사실 레코드만 읽어 독자용 초안을 만든다. 원문 출처, 검증 시점, 불확실성, 관찰과 해석의 경계를 보존한다. Bot이 만든 초안은 게시물 자체가 아니다.
4. **검토**: Evidence Verifier/Reviewer는 별도 Bot이라는 이유로 독립 보안 검토자라고 가정하지 않는다. 공통 클라우드 컴퓨터의 로그인·파일을 공유하므로, 검토의 독립성은 역할 프롬프트가 아니라 Git diff, 원문 링크 재열람, 스키마 검증, 승인 기록으로 만든다.
5. **게시**: 공식 문서는 외부 전송과 공개 게시를 사람 승인 뒤에 두는 것을 기본 권고한다. 이 저장소는 사용자가 명시적으로 위임한 **공공 출처 블로그 경로**에 한해, 스키마 검증·독립 검토·내용 해시·대상 경로·멱등성 키가 모두 일치하면 자동 게시할 수 있도록 별도 정책으로 좁힌다. Slack·Gmail, 비공개·회사 데이터, 삭제, 권한·프로덕션 변경은 이 예외에 포함하지 않는다. 각 단계는 `auto | review | deny`로 되돌릴 수 있어야 한다.
6. **자동화**: 일일·주간 연구는 스케줄·시간대를 명시하고, no-data/stale-data/부분 실패를 별도 상태로 보고한다. GitHub 알림 트리거는 대상 저장소와 이벤트를 좁히고, 중복 실행이 두 번 게시하지 않도록 idempotency key와 기록된 run identity를 둔다.
7. **운영 증거**: UI를 통한 Bot·Group·Routine 적용은 `plan → 사람 승인 → apply → 재열람 verify → runtime snapshot`으로 닫는다. 제품 UI·플러그인 가용성·이벤트 설정은 롤아웃에 따라 달라질 수 있으므로, 실행 관찰을 원하는 상태의 증거로 오인하지 않는다.

### 이 파이프라인에서 허용하지 않을 추론

- Bot이 `SYNCED`라는 runtime 상태라고 해서 공공 출처에서 의미 있는 최신 데이터를 얻었다는 뜻은 아니다.
- 파일이 `/workspace`에 있다고 해서 Git에 기록되었거나 장기 복구 가능하다는 뜻은 아니다.
- 서로 다른 Bot·Group·대화라고 해서 자격증명 또는 데이터가 격리됐다는 뜻은 아니다.
- GitHub 커넥터 이름이 카탈로그에 있다고 해서 특정 저장소 쓰기·PR 생성·이벤트 트리거가 이 계정에서 승인되었다는 뜻은 아니다.
- Test run이 성공했다고 해서 안전한 무인 게시, 시간대 전환, 중복 실행, 출처 변경까지 검증된 것은 아니다.

## 8. 출처 원장

| 구분 | 직접 URL | 조회일 | 소유자 | 뒷받침하는 주장 | 신뢰도 | 정확한 한계/메모 |
| --- | --- | --- | --- | --- | --- | --- |
| 공식 | [Overview](https://docs.x.ai/grok-bot/overview) | 2026-08-24 | SpaceXAI Docs | Bot의 지속형 클라우드 컴퓨터, 병렬 협업, 공유 컴퓨터 모델 | 높음 | 마케팅/개요 문서이며 계정별 UI·권한은 보장하지 않음 |
| 공식 | [Create and manage Bots](https://docs.x.ai/grok-bot/bots) | 2026-08-24 | SpaceXAI Docs | Bot 역할·설명·대화/메모리, 50개 Bot+그룹 한계, hide/delete 의미 | 높음 | 실제 계정 한도·기능은 변경될 수 있음 |
| 공식 | [Message and collaborate](https://docs.x.ai/grok-bot/chat-and-collaboration) | 2026-08-24 | SpaceXAI Docs | 그룹의 2~6 Bot, `@`/`/` 참조, 대화 기록과 인수인계 | 높음 | 그룹이 보안 경계라는 주장은 없음 |
| 공식 | [Skills and routines](https://docs.x.ai/grok-bot/skills-routines-and-automations) | 2026-08-24 | SpaceXAI Docs | 스킬·루틴 정의, Teach 초안, 일정/이벤트, 50 루틴·20 실행 기록, 실제 Test run | 높음 | Teach 및 이벤트는 점진 배포/지원 범위 의존; DST 세부 규칙 미공개 |
| 공식 | [Use the computer and apps](https://docs.x.ai/grok-bot/computer-and-apps) | 2026-08-24 | SpaceXAI Docs | 사용자 단위 공유 컴퓨터, `/workspace`, 파일 지속성 한계, 커넥터, 로컬 컴퓨터 분리 | 높음 | 임시 상태·수동 설치·미커밋 상태의 보존은 보장하지 않음 |
| 공식 | [Approvals, security, and privacy](https://docs.x.ai/grok-bot/approvals-security-and-privacy) | 2026-08-24 | SpaceXAI Docs | 승인·Auto Review·비밀 인계·로컬 실행 정책·공유 권한 위험 | 높음 | 모델 기반 Auto Review는 완전한 정책 집행 수단이 아님 |
| 공식 | [Teams and enterprises](https://docs.x.ai/grok-bot/teams-and-enterprises) | 2026-08-24 | SpaceXAI Docs | 관리형 Linux VM, MCP 토큰 경계, 로컬 실행, 팀 규칙과 네트워크 | 높음 | 팀/엔터프라이즈 기능과 로컬 실행 ceiling은 롤아웃·계약에 따라 다름 |
| 공식 | [Settings and notifications](https://docs.x.ai/grok-bot/settings-and-notifications) | 2026-08-24 | SpaceXAI Docs | 루틴 시간대, Plugins, 데스크톱별 Auto Review, Update/Reset 경계 | 높음 | 설정 항목은 계정과 롤아웃에 따라 보이지 않을 수 있음 |
| 공식 | [Files and results](https://docs.x.ai/grok-bot/files-and-results) | 2026-08-24 | SpaceXAI Docs | 첨부 제한, reviewable 결과, `/workspace` 중간 산출물과 대화 결과 | 높음 | 파일 읽기 가능 형식·크기 제한은 제품 변경 가능 |
| 공식 | [Troubleshooting](https://docs.x.ai/grok-bot/troubleshooting) | 2026-08-24 | SpaceXAI Docs | 로그인·컴퓨터·웹 차단·루틴·플러그인 실패의 점검 순서 | 높음 | 근본 원인과 서비스 가용성을 보장하지 않음 |
| 공식 | [Grok Connectors](https://docs.x.ai/grok/connectors) | 2026-08-24 | SpaceXAI Docs | GitHub 대상 범위, 커스텀 MCP의 공개 접근성 요구 | 중간 | Grok 전체 문서; 특정 Grok Bot 계정의 GitHub 가용성·쓰기 범위는 확인하지 않음 |
| 관찰/커뮤니티 | [jeffhuber/grokbot-imessage-skill](https://github.com/jeffhuber/grokbot-imessage-skill) | 2026-08-24 | Jeff Huber | 로컬 권한과 사람 확인을 둔 외부 iMessage 브리지 사례 | 낮음~중간 | 저자 자기 보고; 공식 지원·보안 검증이 아님 |
| 관찰/커뮤니티 | [SSBrouhard/grokbot-telegram-bridge](https://github.com/SSBrouhard/grokbot-telegram-bridge) | 2026-08-24 | SSBrouhard | 비공식 브리지의 기능/승인 제한 사례 | 낮음~중간 | 비공식·자가 호스팅; 현재 제품 계약의 근거로 사용하지 않음 |
| 관찰/커뮤니티 | [codeaashu/grokbot-shim](https://github.com/codeaashu/grokbot-shim) | 2026-08-24 | codeaashu | 미문서 데스크톱 런타임/원격 컴퓨터를 다뤘다는 공개 구현 보고 | 낮음 | 미문서 통합이며 버전 의존적; 내부 gateway·토큰·포트를 채택하거나 재사용하지 않음 |
| 관찰/커뮤니티 | [SpillwaveSolutions ContentPack](https://github.com/SpillwaveSolutions/account-management/blob/main/docs/GROK_BOT.md) | 2026-08-24 | SpillwaveSolutions | 클라우드 작업 사본과 Git 증거를 분리하는 운영 규칙 사례 | 낮음 | 외부 프로젝트의 규칙이며 Grok Bot 기능 보장이 아님 |

## 9. 검증되지 않은 항목

- 이 저장소가 사용하는 계정에서 실제로 제공되는 플랜, 모델, 사용량 한도, 조직 정책, 지역 가용성.
- Grok Bot의 공개·지원되는 설정 API 유무와 Bot/Group/Routine/Skill을 코드로 읽고 쓰는 공식 계약. 이 문서는 그런 API를 확인하지 못했다.
- 이 계정의 GitHub connector/이벤트 통합 가용성, OAuth scope, GitHub App 설치 주체, PR·commit·issue·workflow 실행 권한, 감사 로그 형식.
- 이벤트 트리거의 정확한 전달 보장, 중복 제거, 순서, 재시도, 최대 지연, 일광절약시간 처리, 장애 후 catch-up 동작.
- `/workspace` 저장 한도, 백업·보존 기간, 컴퓨터 재생성 시 모든 파일 유형의 내구성, Bot 삭제 뒤 백엔드 보존의 세부 조건.
- 플러그인/패키지 스킬의 공개 매니페스트 규격, 서명·검토·격리 모델, 팀 마켓플레이스의 실제 조직 정책.
- 로컬 컴퓨터 실행의 OS별 세부 권한, 파일 전송 경로, 조직 정책 ceiling의 현재 일반 가용성.
- 공식 문서에서 말하는 Auto Review가 이 저장소의 외부 게시/프로덕션 변경 요구를 충분히 집행하는지 여부. 이 저장소의 공공 출처 블로그 자동 게시 예외는 제품 Auto Review에만 의존하지 않고, 별도의 단계 정책과 정확한 대상·내용 해시 기반 검증을 요구한다.
