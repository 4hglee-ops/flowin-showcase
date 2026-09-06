# Flowin Roadmap

> Public roadmap. Flowin은 기능 약속 목록보다 현재 제품 단계와 실제 사용에서 확인되는 문제를 기준으로 우선순위를 조정합니다.

## Current phase

**Closed Alpha · Active Dogfooding / Iteration**

핵심 제품 흐름은 실제 사용 가능한 상태이며, 현재는 새로운 기능을 무조건 늘리기보다 실제 사용에서 반복되는 마찰과 신뢰성 문제를 줄이는 단계입니다.

현재 구현된 주요 축:

- Capture → Inbox → AI 정리 → Task / Note
- Today / Focus / Planned / Calendar
- Project Hub v0.2
- Supabase multi-user / Authentication / RLS
- Search / Logbook
- Admin / onboarding
- MCP / ChatGPT integration
- Windows Companion / Microsoft Store
- Security Center / operational security baseline

## Now

- 직접 사용과 Closed Alpha dogfooding
- 반복해서 드러나는 UX 마찰 개선
- 회귀 버그와 데이터 일관성 점검
- 화면 전환·복구·오류 상황의 신뢰성 유지
- 보안 및 운영 baseline 유지
- 실제 제품 변화에 맞춘 공개 showcase / changelog 갱신

## Iteration policy

새 기능은 단순히 구현할 수 있다는 이유로 우선하지 않습니다.

다음 조건이 겹칠수록 우선순위를 높입니다.

1. 실제 사용 중 문제가 발견된다.
2. 같은 문제가 반복된다.
3. 사용자가 일을 관리하는 데 쓰는 판단과 조작을 줄일 수 있다.
4. 기존 핵심 흐름을 복잡하게 만들지 않고 해결할 수 있다.

## Exploration

아래 항목은 확정 일정이 아니라 제품 사용을 통해 필요성이 검증되면 다시 평가합니다.

- Weekly Review
- Recurring Tasks
- Note / Idea dedicated views
- Richer AI assistance inside Flowin
- Semantic Search / RAG
- Natural-language views
- Resource recommendations
- Personalized Agent behavior
- Cross-tool work context
- Project Timeline의 richer planning interaction

## Recently completed

### Project Hub v0.2 · 2026-09-06

- Overview / Work / Records IA
- Backlog → To Do → In Progress → Done workflow
- On Hold separate handling
- List / Board / Timeline
- Schedule / Task Deadline / Project Deadline separation
- Planning-needed flow
- Completion Criteria / Decisions / Resources / Activity
- 100-Task Project dogfood audit

### Closed Alpha feedback rounds

사용자 피드백을 기반으로 Planned/Calendar, 삭제/복구, Area 관리, GPT 결과 식별, 개인정보 동의, 로딩 체감, Quick Capture 안내 등을 반복 개선했습니다.

### Security & operations

Security Center, 접속 보호, 보안 활동, 실패 로그인 기록, Windows Companion 권한 경계와 보관 정책 등을 보강했습니다.

## Guiding question

Every roadmap item is ultimately evaluated against one question:

> Does this help the user spend less effort managing work and more effort actually doing it?
