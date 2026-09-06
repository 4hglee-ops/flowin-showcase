# Flowin Product Overview

## Product statement

Flowin은 사용자가 생각나는 내용을 빠르게 Capture하고, 이를 실행 가능한 형태로 정리해 현재 해야 할 일에 집중하도록 돕는 AI-assisted personal work system입니다.

## Current phase

**Closed Alpha · Active Dogfooding / Iteration**

핵심 제품 흐름과 운영 기반은 구현되어 있으며, 현재는 실제 사용에서 반복적으로 드러나는 마찰과 신뢰성 문제를 우선적으로 개선합니다.

## Problem

기존 생산성 도구에서는 기록하는 순간부터 유형, 프로젝트, 날짜, 우선순위 같은 결정을 요구하는 경우가 많습니다. Flowin은 이 작은 결정들이 누적되어 기록과 실행 모두에 마찰을 만든다고 봅니다.

## Core loop

```text
Capture → Inbox → Organize → Focus → Execute → Review
```

### Capture
생각이 생겼을 때 분류보다 기록을 먼저 합니다.

### Inbox
아직 정리되지 않은 Capture를 모아두고 원문을 보존합니다.

### Organize
AI와 사용자가 Capture를 Task, Note, Idea 등의 실제 결과로 정리합니다.

### Focus
오늘 실행해야 할 작업과 다음 행동을 좁혀 보여줍니다.

### Execute
사용자는 관리보다 실제 작업 수행에 집중합니다.

### Review
완료 기록, Project Records와 Logbook을 통해 과거 작업과 판단을 다시 확인합니다.

## Main product areas

- Home / Focus
- Quick Capture
- Inbox
- Today / Planned / Calendar
- Project Hub
- Areas
- Search
- Logbook
- AI Activity / GPT integration
- Admin / onboarding
- Security Center
- Windows Companion

## Project Hub v0.2

Project는 단순 Task container가 아니라 실행·계획·기록이 연결되는 작업 맥락으로 확장했습니다.

```text
Project
├─ Overview
│  ├─ Attention
│  ├─ Next Action
│  └─ Execution / Context
├─ Work
│  ├─ List
│  ├─ Board
│  └─ Timeline
└─ Records
   ├─ Completion Criteria
   ├─ Decisions
   ├─ Resources
   └─ Activity
```

핵심 설계:

- Workflow: `Backlog → To Do → In Progress → Done`
- `On Hold`는 정상 Workflow 밖의 예외 상태
- `Next Action`은 workflow status가 아니라 실행 overlay
- Timeline에서 Schedule / Task Deadline / Project Deadline을 분리
- 실행 큐에 있지만 일정이 없는 Task를 `계획 필요`로 표시
- Project의 완료 기준과 Task 진행률을 별도 개념으로 유지

## AI-assisted organization

AI는 독립 챗봇보다 제품 workflow의 정리 레이어로 사용합니다.

```text
Flowin context
+ user request
+ organization rules
        ↓
AI processing
        ↓
Task / Note / Project result
        ↓
review / correction / traceability
```

원문 Capture와 결과 관계를 보존해 AI가 틀렸을 때 다시 확인하고 수정할 수 있는 구조를 지향합니다.

## Platform direction

초기에는 Notion API 기반 prototype으로 빠르게 제품 가설을 검증했고, Closed Alpha 단계에서 Supabase / PostgreSQL / Auth / RLS 기반 multi-user 구조로 전환했습니다.

Web 제품 외에도 Windows Companion과 MCP / ChatGPT integration을 통해 Capture와 AI 정리 경험을 다른 사용 맥락까지 연결합니다.

## Design direction

Flowin은 필요한 기능을 단순히 제거하기보다, 정보 구조와 점진적 노출을 통해 기능이 많아져도 사용자가 복잡하게 느끼지 않는 제품을 목표로 합니다.

또한 현재 단계에서는 새로운 기능 수보다 **실제 사용에서 반복되는 판단 비용과 조작 비용을 얼마나 줄이는가**를 우선합니다.
