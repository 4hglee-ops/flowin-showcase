# Flowin Architecture

> This document intentionally describes only the public, portfolio-safe architecture of Flowin.

## High-level architecture

```text
User
  │
  ├──────────────► Windows Companion / Quick Capture
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
  ├──────────────► AI / MCP Integration
  │
  ▼
Supabase
PostgreSQL · Auth · RLS
```

## Frontend

Flowin uses Next.js App Router with React and TypeScript. UI routes are kept separate from reusable components and application logic.

Main product surfaces include Home / Focus, Inbox, Today / Planned, Project Hub, Search, Logbook, Settings and security/connection flows.

## Application layer

Product behavior is organized around domains such as:

- Capture / Inbox
- Tasks
- Projects / Project Hub
- Areas
- Search
- Logbook
- AI Activity
- Admin / onboarding

Project Hub itself separates execution, planning and project memory into Overview / Work / Records instead of treating a Project as only a Task list.

## Data / auth layer

The project began with a Notion-backed prototype for fast product validation. As Flowin moved into real multi-user Closed Alpha testing, the production architecture transitioned to Supabase with PostgreSQL, authentication and Row Level Security.

The repository/application boundary keeps product logic from depending directly on one UI or data-source implementation.

## AI integration

AI is treated as an application capability rather than an isolated chatbot.

```text
User context
+ Flowin data
+ Processing rules
       ↓
AI processing
       ↓
Structured Flowin result
       ↓
Review / correction / traceability
```

This makes AI output part of the product workflow while preserving the ability to inspect and correct results.

Flowin also experiments with MCP / ChatGPT integration so external AI clients can operate on Flowin context through explicit authentication and product boundaries.

## Windows Companion

Windows Companion extends Quick Capture outside the browser. The public architecture intentionally omits credential, pairing and security-sensitive implementation details; the important product boundary is that desktop capture and sensitive operations are mediated through the Flowin service rather than exposing privileged credentials to the client.

## Security / operations

Closed Alpha operation includes a public-facing security baseline around authentication, account/device visibility, access protection and security activity. Exact detection logic, credentials and sensitive enforcement details are intentionally not documented in this showcase.

## Public repository boundary

This showcase does not expose:

- production credentials
- environment variables
- private application source
- user data
- security-sensitive implementation details

Architecture documentation is intentionally maintained at a level suitable for a public portfolio.
