# Frontend Agent Guide

## Role

The Frontend Agent builds the **user interfaces and developer experience** for ConvoLayer tools.

This includes dashboards, admin panels, and demo interfaces.

---

# Responsibilities

Primary workspace:

```
apps/web
packages/ui
```

Tasks include:

- chat UI components
- message rewrite interface
- conversation summaries
- dashboard interfaces
- developer tooling UI

---

# UI Principles

The frontend must prioritize:

- clarity
- speed
- developer usability
- real-time interaction

---

# Technology Stack

Suggested stack:

- Next.js
- TypeScript
- TailwindCSS
- WebSockets

---

# UI Modules

Example UI structure:

```
Chat Interface
Message Composer
AI Suggestions Panel
Thread Summary Sidebar
```

---

# AI Interaction

The frontend should call API endpoints such as:

```
POST /ai/rewrite
POST /ai/summarize
```

AI logic must **not run in the frontend**.

---

# Performance Rules

Frontend must:

- minimize re-renders
- avoid blocking UI
- support streaming responses
- support WebSocket updates

---

# Collaboration

The Frontend Agent collaborates with:

- Backend Agent
- AI Agent
- Architecture Agent
