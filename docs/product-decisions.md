# Product Decisions

Flowin은 구현 결과뿐 아니라 제품을 만들면서 내린 판단과 그 이유를 기록합니다.

## 1. Capture first

### Decision
입력 단계에서는 Task, Note, Project 등을 먼저 선택하게 하지 않습니다.

### Why
기록 순간의 분류 비용을 줄이고 생각을 놓치지 않는 것이 더 중요하기 때문입니다.

---

## 2. Capture와 Task를 별도 엔티티로 관리

### Decision
원문 Capture와 정리된 Task를 분리합니다.

### Why
AI나 사용자가 정리한 결과가 잘못되어도 원문으로 돌아갈 수 있고, 하나의 Capture가 여러 결과로 발전할 가능성도 보존할 수 있습니다.

---

## 3. AI는 독립된 챗봇보다 제품 흐름 안에 배치

### Decision
AI 대화를 별도 기능으로 끝내지 않고 Inbox 정리, Task/Note 생성, Project 연결 같은 실제 제품 동작과 연결합니다.

### Why
Flowin에서 AI의 가치는 답변 생성보다 반복적인 관리 판단을 줄이는 데 있다고 보기 때문입니다.

---

## 4. 기능 수와 체감 복잡도를 분리해서 판단

### Decision
필요한 기능이라는 판단이 서면 단순히 기능 수를 줄이기 위해 제거하지 않습니다.

### Why
제품의 복잡도는 기능 개수만으로 결정되지 않습니다. 온보딩, 화면 계층, 기본값, 점진적 노출, 정보 구조를 통해 많은 기능도 이해하기 쉽게 제공할 수 있다고 봅니다.

---

## 5. Prototype data source에서 multi-user backend로 전환

### Decision
초기 Notion 기반 프로토타입에서 Supabase / PostgreSQL / Auth / RLS 기반 데이터 구조로 전환했습니다.

### Why
초기에는 빠른 검증이 중요했지만 실제 사용자 테스트 단계에서는 계정별 데이터 분리, 인증, 권한 관리와 안정적인 데이터 모델이 필요해졌기 때문입니다.

---

## 6. Project를 Task container가 아니라 Hub로 확장

### Decision
Project 상세를 `Overview / Work / Records`로 나누고, 실행·계획·기록을 한 맥락에서 다룹니다.

### Why
Project에서 Task 목록만 보는 것으로는 사용자가 실제로 궁금한 세 질문에 답하기 어려웠기 때문입니다.

1. 지금 무엇을 해야 하는가?
2. 이 Project의 작업을 어떻게 보고 계획할 것인가?
3. 언제 완료되며, 왜 이렇게 결정했고 어떤 근거가 남아 있는가?

Project Hub v0.2는 이 세 질문을 각각 Overview / Work / Records로 분리합니다.

---

## 7. Next Action과 Workflow Status를 분리

### Decision
`Backlog → To Do → In Progress → Done`을 작업 단계로 사용하고, Next Action은 별도의 실행 overlay로 유지합니다.

### Why
Status는 “이 일이 어디까지 왔는가?”를 설명하고, Next Action은 “그래서 지금 무엇을 해야 하는가?”를 설명합니다. 두 의미를 하나의 상태 값으로 합치면 Project와 Today/Focus의 실행 의미가 흐려집니다.

`On Hold` 역시 정상 선형 Workflow가 아니라 잠시 멈춘 예외 상태로 별도 취급합니다.

---

## 8. Schedule과 Deadline을 같은 날짜로 취급하지 않음

### Decision
Timeline에서 Schedule, Task Deadline, Project Deadline을 서로 다른 시각 언어로 표현합니다.

### Why
실행하려는 날과 반드시 끝내야 하는 날은 다른 의미입니다. Flowin은 계획을 보기 쉽게 만들기 위해 두 날짜를 합쳐 단순화하기보다 의미 차이를 유지합니다.

- Schedule: 실행 시점/기간
- Task Deadline: Task 최종 기한
- Project Deadline: Project 전체 기한

---

## 9. Backlog는 날짜가 없어도 정상

### Decision
Timeline에서 날짜가 없는 모든 Task를 `계획 필요`로 보지 않습니다. 실행 큐에 올라온 To Do / In Progress인데 Schedule이 없는 경우만 계획 필요로 봅니다.

### Why
Backlog는 아직 실행 큐에 올리지 않은 작업이므로 일정이 없는 상태 자체가 문제는 아닙니다. 모든 Backlog에 날짜를 강요하면 계획 도구가 다시 관리 부담을 늘리게 됩니다.

---

## 10. 실제 사용에서 반복되는 문제를 우선

### Decision
핵심 제품 흐름을 구축한 이후에는 기능을 계속 추가하기보다 dogfooding과 Closed Alpha 사용에서 반복되는 문제를 우선 개선합니다.

### Why
제품이 어느 정도 완성된 이후에는 가능한 기능의 수보다 실제 마찰을 줄이는 것이 더 중요합니다. 기능 후보는 backlog에 둘 수 있지만, 반복되는 사용 문제라는 근거가 생기기 전까지 구현 약속으로 취급하지 않습니다.

---

## 11. Product decisions themselves are portfolio artifacts

Flowin은 완성 화면만 보여주는 프로젝트가 아니라, **문제 발견 → 가설 → 구현 → 실제 사용 → 피드백 → 재설계 → 운영 안정화**의 반복 과정을 보여주는 프로젝트로 발전시키고 있습니다.
