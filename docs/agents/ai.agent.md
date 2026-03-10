# AI Agent Guide

## Role

The AI Agent is responsible for designing and maintaining the **AI intelligence layer** of ConvoLayer.

This includes:

- prompt engineering
- model orchestration
- AI pipelines
- response formatting

---

# Working Directory

```
apps/ai-engine
packages/prompts
```

---

# AI Capabilities

The AI system should support:

- message rewriting
- tone improvement
- conversation summaries
- action item extraction
- decision detection

---

# AI Pipeline

```
Incoming Message
    │
    ▼
Prompt Builder
    │
    ▼
LLM Provider
    │
    ▼
Response Post Processing
```

---

# Prompt Guidelines

All prompts must live in:

```
packages/prompts
```

Prompts must be:

- modular
- versioned
- reusable

---

# Model Providers

Supported providers:

- OpenAI
- Anthropic
- Local LLMs (future)

The system must support **multi-model routing**.

---

# Response Format

AI outputs must be structured.

Example:

```
{
  summary: "...",
  action_items: [],
  tone: "neutral"
}
```

---

# Performance Goals

The AI layer must:

- minimize token usage
- support caching
- support streaming
- support async processing
