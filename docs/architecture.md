# Flowin Architecture

> This document intentionally describes only the public, portfolio-safe architecture of Flowin.

## High-level architecture

```text
User
  │
  ▼
Flowin Web UI
Next.js / React / TypeScript
  │
  ▼
Application Services
Capture · Task · Project · Search · AI
  │
  ▼
Domain / Repository Layer
  │
  ├──────────────► AI Integration
  │
  ▼
Supabase
PostgreSQL · Auth · RLS
```

## Frontend

Flowin uses Next.js App Router with React and TypeScript. UI routes are kept separate from reusable components and application logic.

## Application layer

Product behavior is organized around domains such as:

- Capture / Inbox
- Tasks
- Projects
- Areas
- Search
- Logbook
- AI Activity

## Data layer

The project began with a Notion-backed prototype. As the product moved toward real multi-user testing, the architecture was migrated toward Supabase with authentication and Row Level Security.

## AI integration

AI is treated as an application capability rather than an isolated chatbot. The intended flow is:

```text
User context
+ Flowin data
+ Processing rules
       ↓
AI processing
       ↓
Structured Flowin result
       ↓
Activity / traceability
```

This makes AI output part of the product workflow while preserving the ability to inspect and correct results.

## Public repository boundary

This showcase does not expose:

- production credentials
- environment variables
- private application source
- user data
- security-sensitive implementation details

Architecture documentation is intentionally maintained at a level suitable for a public portfolio.
