# Backend Agent Guide

## Role

The Backend Agent is responsible for building and maintaining the **core API and service logic** of the ConvoLayer platform.

This agent ensures the backend services remain:

- modular
- scalable
- maintainable
- secure

---

# Responsibilities

The Backend Agent works primarily inside:

```
apps/api
packages/shared-types
packages/sdk
```

Core responsibilities include:

- implementing API endpoints
- managing authentication
- orchestrating AI tasks
- managing message processing pipelines
- maintaining service boundaries

---

# Key Backend Principles

### Separation of Concerns

Responsibilities must remain separated across components.

| Component  | Responsibility                 |
| ---------- | ------------------------------ |
| Connectors | receive/send platform messages |
| API        | orchestration layer            |
| AI Engine  | AI processing                  |

The backend must **not embed AI logic**.

---

### API Design

The API should be:

- RESTful
- versioned
- predictable
- well-documented

Example endpoint:

```
POST /ai/rewrite
POST /ai/summarize
POST /ai/extract-actions
```

---

# Event Flow

```
Connector Event
    │
    ▼
API Endpoint
    │
    ▼
Queue Task
    │
    ▼
AI Engine Processing
```

The API should always act as the **central orchestrator**.

---

# Backend Technologies

Suggested stack:

- Node.js / TypeScript
- Express / Fastify
- PostgreSQL
- Redis
- BullMQ

---

# Performance Guidelines

Backend code must prioritize:

- non-blocking operations
- asynchronous processing
- efficient message handling
- minimal latency

AI calls must never block API response loops.

---

# Collaboration

The Backend Agent collaborates with:

- AI Agent (AI features)
- DevOps Agent (deployment)
- Architecture Agent (system design)

---

# When Adding New Features

Steps:

1. Define API endpoint
2. Define request schema
3. Queue AI task
4. Return structured response
