# Architecture Agent Guide

## Role

The Architecture Agent maintains the **overall system design** and ensures architectural consistency.

This agent enforces:

- system boundaries
- modular design
- scalability
- maintainability

---

# Core Architecture

```
Chat Platforms
    │
    ▼
Connectors
    │
    ▼
API Layer
    │
    ▼
AI Engine
```

---

# Architecture Rules

### Rule 1

Connectors must remain **thin adapters**.

### Rule 2

AI logic must exist only inside **AI Engine**.

### Rule 3

API must remain the **central orchestrator**.

---

# System Design Goals

The architecture must support:

- horizontal scaling
- asynchronous processing
- connector extensibility
- model flexibility
