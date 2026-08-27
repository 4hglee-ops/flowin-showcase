# Flowin

> **생각나면 툭. 정리는 알아서.**

Flowin은 생각나는 내용을 가볍게 기록하고, 이를 실행 가능한 작업으로 정리해 **지금 무엇을 해야 하는지에 집중할 수 있게 만드는 AI-assisted personal work system**입니다.

이 저장소는 Flowin의 **공개 제품 쇼케이스**입니다. 실제 제품 소스코드는 비공개 저장소에서 관리하며, 여기서는 제품 문제 정의, 핵심 기능, UX 흐름, 아키텍처, 설계 의사결정과 발전 방향을 공개합니다.

---

## Why Flowin?

할 일 관리 도구는 기록 자체보다 기록 이후의 작은 판단을 반복해서 요구할 때가 있습니다.

- 이건 어떤 프로젝트에 넣어야 하지?
- 우선순위는 어떻게 정하지?
- 날짜를 지금 결정해야 하나?
- 메모인가, 할 일인가?
- 그래서 지금 가장 먼저 해야 하는 건 뭔가?

Flowin은 이런 **반복적인 판단 비용을 줄이는 것**에서 시작했습니다.

```text
생각남
  ↓
Quick Capture
  ↓
Inbox
  ↓
AI 정리
  ↓
Today / Focus
  ↓
실행
  ↓
완료 / Logbook
```

---

## Product Principles

- **Capture first** — 입력할 때 분류하지 않는다.
- **Separate capture from execution** — Capture와 Task를 분리한다.
- **AI as an organizing layer** — AI는 반복적인 정리와 판단을 줄이는 보조 레이어로 사용한다.
- **Execution over management** — Home과 Today에서는 관리보다 실행을 우선한다.
- **Recoverable AI** — AI가 틀려도 원문을 추적하고 쉽게 수정할 수 있어야 한다.

---

## Core Experience

### 1. Quick Capture & Inbox

생각나는 내용을 별도 분류 없이 바로 기록합니다.

- 자연어 기반 빠른 입력
- 원문 보존
- 한 줄 / 여러 줄 Capture
- 저장 후 Undo
- 미정리 / 확인 필요 / 메모 / 아이디어 상태
- Windows Quick Capture Helper

입력 단계에서는 사용자가 유형을 먼저 고르지 않고, 정리 이후 목적에 맞게 구분합니다.

### 2. Today & Focus

오늘 실행해야 할 작업을 한곳에서 확인합니다.

- 오늘 일정 / 오늘 마감 / 지난 마감
- Focus 작업과 실행 순서
- 이번 주 다음 후보
- Upcoming / Anytime / Someday 파생 View

### 3. Projects

Project는 단순한 Task 묶음보다 **“이 프로젝트에서 다음에 무엇을 해야 하는가?”**를 보여주는 데 집중합니다.

- Project 목록 / 상세
- Next Action
- Area
- 연결 Task
- 자료 및 결정 기록
- 고정 Project

### 4. Personal Work Hub

자주 사용하는 작업과 외부 리소스에 빠르게 접근합니다.

- Sidebar Quick Links
- Pinned Projects
- Search
- Logbook

### 5. AI-assisted Organization

Flowin의 AI 기능은 단순 채팅보다 **사용자의 현재 작업 맥락을 정리하고 다시 제품으로 되돌려주는 구조**를 지향합니다.

```text
Flowin Context
    +
AI 작업 규칙
    +
사용자 요청
    ↓
AI Processing
    ↓
Task / Note / Project updates
    ↓
Flowin Activity Log
```

주요 방향:

- Inbox Capture 자동 정리
- Task / Note 생성 보조
- 프로젝트 연결 보조
- AI 요청 / 결과 기록
- 관련 Capture / Task / Project 추적
- 잘못된 분류를 수정할 수 있는 흐름

---

## Product Architecture

현재 Flowin은 Next.js 기반 웹 애플리케이션으로 구성되어 있으며, 제품 로직과 데이터 접근 계층을 분리해 확장성을 확보하는 방향으로 개발하고 있습니다.

```text
┌──────────────────────────────┐
│          Flowin UI           │
│   Next.js / React / TS       │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│     Application Services     │
│ Capture / Task / Project     │
│ Search / AI / Logbook        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Domain / Repository    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Data / Auth Layer       │
│   Supabase / External APIs   │
└──────────────────────────────┘
```

> 초기 버전은 Notion API를 데이터 소스로 사용했고, 이후 실제 사용자 확장을 위해 Supabase 기반 구조로 전환하고 있습니다.

---

## Tech Stack

| Area | Stack |
| --- | --- |
| Frontend | Next.js · React · TypeScript |
| Data / Backend | Supabase · PostgreSQL |
| AI Integration | ChatGPT · MCP / Actions · Prompt-based workflows |
| Testing | Vitest · TypeScript Type Check · ESLint |
| Deployment | Vercel |
| Desktop Helper | Windows Quick Capture |

---

## Product Decisions

Flowin은 기능 수보다 **사용자가 느끼는 판단 비용과 복잡도를 줄이는 것**을 중요하게 보고 있습니다.

### Capture와 Task를 분리한 이유

생각나는 순간부터 프로젝트·우선순위·날짜를 정하게 하면 기록 자체가 느려집니다. 따라서 원문 Capture를 먼저 보존하고, 정리된 실행 항목은 별도의 Task로 관리합니다.

### AI 자동화에서 원문을 남기는 이유

AI가 분류를 틀릴 수 있기 때문에 자동화 결과만 남기지 않고 **원본 Capture → 생성된 결과 → AI Activity**를 추적할 수 있도록 설계합니다.

### 기능이 많아도 복잡해 보이지 않게

기능을 줄이는 것만이 단순한 제품을 만드는 방법은 아니라고 보고 있습니다. 필요한 기능은 유지하되, 온보딩·정보 구조·점진적 노출을 통해 처음 사용하는 화면의 복잡도를 낮추는 방향을 선택합니다.

---

## Current Status

**Active Development**

현재 진행 중인 주요 영역:

- Supabase 기반 멀티유저 구조
- Authentication / RLS
- Admin 운영 기능
- Inbox → AI → Task / Note 처리 흐름
- Area / Project / Task 연결
- Today / Planned / Calendar UX
- Search / Logbook 고도화
- 사용자 피드백 기반 UI 개선

---

## Roadmap

### Near Term

- Capture 정리 경험 고도화
- AI 처리 결과 조회 / 수정 UX
- Planned / Calendar 화면 개선
- 온보딩 개선
- 실제 사용자 테스트 반복

### Next

- 반복 Task
- Weekly Review
- Note / Idea 전용 View
- 앱 내부 AI 경험 고도화
- MCP / ChatGPT 연동 확장

### Later

- RAG / Semantic Search
- 자연어 기반 View
- Resource Recommendation
- Personalized Agent

---

## Showcase Structure

```text
flowin-showcase/
├── README.md
├── docs/
│   ├── product-overview.md
│   ├── architecture.md
│   ├── product-decisions.md
│   └── roadmap.md
└── assets/
    ├── screenshots/
    └── diagrams/
```

이 공개 저장소에는 소스코드 대신 **제품을 이해하는 데 필요한 정보와 시각 자료**를 중심으로 정리합니다.

---

## What this project demonstrates

Flowin을 통해 다음 역량을 실제 제품 개발 과정에서 다루고 있습니다.

- 문제 정의와 제품 기획
- UX / 정보 구조 설계
- Next.js 기반 웹 애플리케이션 구현
- Supabase 기반 데이터 모델과 인증 구조
- AI 기능을 제품 흐름에 통합하는 방법
- 사용자 피드백 기반 반복 개선
- 기능 확장과 복잡도 사이의 설계 의사결정

---

## Public Showcase Notice

이 저장소는 **Flowin의 공개 포트폴리오 / 제품 쇼케이스**입니다.

- 실제 애플리케이션 소스코드는 비공개 저장소에서 관리합니다.
- 내부 환경 변수, 사용자 데이터, 운영 자격 증명은 공개하지 않습니다.
- 제품 화면과 문서는 공개 가능한 범위에서 지속적으로 업데이트합니다.

---

## Product Direction

Flowin이 궁극적으로 줄이고 싶은 것은 **할 일의 개수**가 아니라, 할 일을 관리하기 위해 사용자가 반복해서 내려야 하는 **작은 판단의 개수**입니다.

> **생각나면 툭.**  
> **정리는 알아서.**  
> **그리고 사용자는 실행에 집중한다.**
