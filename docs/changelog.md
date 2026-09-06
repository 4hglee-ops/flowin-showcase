# Flowin Product Changelog

> Public, portfolio-safe changelog. 사용자 관점에서 의미 있는 제품 변화만 기록하며 내부 자격 증명, 민감한 보안 구현과 개인 데이터는 포함하지 않습니다.

## 2026-09-06 — Project Hub v0.2

Project 상세을 단순 Task 목록에서 **실행·계획·기록이 연결되는 Hub**로 확장했습니다.

### Overview
- Attention과 Next Action을 가장 먼저 표시
- 진행 중 작업과 다음 작업 요약
- Task 진행 현황과 Completion Criteria를 분리
- 핵심 자료와 최근 활동을 Project context로 연결

### Work
- List / Board / Timeline 제공
- 빠른 보기, 검색, 단계, 우선순위 필터
- workflow를 `Backlog → To Do → In Progress → Done`으로 정리
- `On Hold`는 정상 workflow 밖의 별도 상태로 관리
- Board Drag & Drop으로 단계 변경

### Timeline
- Schedule range는 bar, 단일 날짜 Schedule은 point
- Task Deadline은 ◆ marker
- Project Deadline은 별도 vertical marker
- Today line과 Week / Month 탐색
- Parent/Subtask hierarchy + collapse/expand
- 실행 큐에 있지만 Schedule이 없는 Task를 `계획 필요`로 분리
- Planning Tray에서 Task를 열어 일정 설정 가능

### Records
- Completion Criteria / Decisions / Resources / Activity를 sub-tab으로 분리
- Decisions / Resources / Activity에 검색·필터·번호형 pagination 적용

### Validation
- 실제 약 100-Task MRP Project로 dogfood UX audit
- queue state와 Next Action 의미 일관성 보강
- Typecheck / 144 tests / Production build / lint 통과 후 main 반영

---

## 2026-09-06 — Closed Alpha Feedback Round 4

실제 사용자 피드백을 기준으로 UX와 운영 흐름을 보강했습니다.

- 새로운 소식 Featured / Archive 구조
- 사용하지 않는 Area archive + undo
- 사용 중인 Area의 안전한 보호
- GPT 작업 결과에서 미확인 항목 식별 강화
- 가입 신청 개인정보 수집·이용 동의
- 개인정보 처리방침을 실제 운영 흐름 기준으로 정리
- Project 재진입 시 최근 데이터를 우선 표시해 로딩 체감 개선
- Quick Capture의 “먼저 기록하고 나중에 정리” 흐름 안내 보강

---

## 2026-09-06 — Security & Operations Hardening

Closed Alpha 운영을 위한 계정·접속·기기 보안 baseline을 강화했습니다.

- Security Center에서 접속 국가와 기준 국가 확인
- 선택적 해외 일반 Web 접근 보호
- 새 국가 로그인 알림
- 실패 로그인 기록 및 중복 완화
- 최근 Security Activity / 전체 활동 조회
- Windows Companion / Desktop API 민감 작업의 서버 권한 경계 강화
- 보안 이벤트 90일 retention 정책

---

## 2026-09-03 — Windows Companion Microsoft Store

Windows용 Quick Capture 경험을 Store 배포 수준으로 정리했습니다.

- Microsoft Store 인증 통과
- MSIX 기반 기본 설치 흐름
- Companion 첫 실행 및 PC 연결 안내
- Windows 어디서나 Quick Capture
- 연결 과정의 민감값 노출을 줄이는 연결 ticket 방식

---

## 2026-08-30 — Closed Alpha Feedback Round 3

- Project 사용자 지정 순서
- Task / Capture / AI Activity 삭제 및 복구 흐름
- GPT Actions 설정 안내
- Claude MCP 연결 안내
- OAuth 연결 허용 / 취소 / 해제
- Vercel / Supabase 리전 정렬
- 새로운 소식 unread 표시

---

## 2026-08-26 — Closed Alpha Feedback Round 2

- Planned 화면을 Calendar 중심으로 재구성
- 날짜 선택 후 해당 날짜 Task 확인
- 날짜 미정 Task 별도 노출
- 지난 마감 표시
- 모바일 Calendar / floating action UX 보완

---

## 2026-08-25 — Closed Alpha Feedback Round 1

- 계정별 즐겨찾기 수정
- Area 생성 / 관리
- Focus 직접 추가
- GPT 없이 Task 직접 생성
- Task 생성 시 Project / Area / Deadline / Priority / Memo / Focus 설정
- 화면 전환 체감 개선
- Project Task 상태 정확도 및 보류 상태 노출
- Task autosave 개선
- Inbox Capture archive / restore
- 모바일 홈 화면 설치 구성
- 새로운 소식 진입 위치 개선

---

## Changelog policy

Flowin은 모든 내부 commit을 공개 changelog에 옮기지 않습니다.

공개 changelog에는 다음 기준을 만족하는 변화만 기록합니다.

1. 사용자가 실제로 체감할 수 있는 변화
2. 제품 구조나 운영 방향을 이해하는 데 의미 있는 변화
3. 공개해도 보안·개인정보 위험이 없는 변화

세부 구현과 민감한 운영 정보는 비공개 제품 저장소에서 관리합니다.
