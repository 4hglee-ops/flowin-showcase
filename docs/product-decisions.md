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
초기 Notion 기반 프로토타입에서 Supabase 기반 데이터 구조로 발전시킵니다.

### Why
초기에는 빠른 검증이 중요했지만 실제 사용자 테스트 단계에서는 계정별 데이터 분리, 인증, 권한 관리와 안정적인 데이터 모델이 필요해졌기 때문입니다.

---

## 6. Product decisions themselves are portfolio artifacts

Flowin은 완성 화면만 보여주는 프로젝트가 아니라, 문제 발견 → 가설 → 구현 → 피드백 → 수정의 반복 과정을 보여주는 프로젝트로 발전시키고 있습니다.
