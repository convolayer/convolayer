# AGENTS.md

## AI Agent Operating Guide for ConvoLayer

This document provides guidance for **AI coding agents** interacting with the ConvoLayer repository.

It defines:

- system architecture context
- component responsibilities
- development rules
- modification boundaries
- recommended workflows

Agents should read this file **before making code changes**.

---

# Project Overview

ConvoLayer is an **AI infrastructure layer for team communication platforms**.

It enables AI-powered features such as:

- message rewriting
- conversation summarization
- tone detection
- action item extraction

These capabilities integrate into platforms like:

- Slack
- Discord
- Microsoft Teams
- GitHub Discussions

ConvoLayer acts as an intermediary layer between **communication platforms and AI models**.

---

# System Architecture

High-level architecture:

```
Chat Platforms
(Slack / Discord / Teams)
        │
        ▼
   Connector Services
        │
        ▼
     ConvoLayer API
        │
        ▼
      AI Engine
        │
        ▼
   LLM Providers
(OpenAI / Anthropic / Local Models)
```

---

# Core System Components

Agents should understand the responsibilities of each component before modifying code.

---

## API Service

Location:

```
apps/api/
```

Responsibilities:

- authentication
- request routing
- connector coordination
- AI task orchestration

The API is the **central gateway of the system**.

Do not introduce direct AI calls from connectors.
All AI processing must pass through the API layer.

---

## AI Engine

Location:

```
apps/ai-engine/
```

Responsibilities:

- prompt construction
- model orchestration
- message rewriting
- summarization
- tone analysis
- action item extraction

Agents should modify prompts and AI pipelines **only within this module**.

---

## Connectors

Location:

```
apps/connectors/
```

Examples:

```
slack/
discord/
teams/
github/
```

Responsibilities:

- receiving platform events
- sending AI responses back to chat platforms

Connectors should remain **thin adapters**.

Business logic should not be implemented inside connectors.

---

## Shared Packages

Location:

```
packages/
```

Contains:

```
sdk/
prompts/
shared-types/
```

These packages provide shared interfaces used across services.

Agents must ensure **type compatibility across packages** when making changes.

---

# Event Flow

Typical request lifecycle:

```
User sends message in Slack
        │
        ▼
Slack connector receives event
        │
        ▼
Connector forwards event to API
        │
        ▼
API queues AI processing job
        │
        ▼
AI Engine processes request
        │
        ▼
Result returned to connector
        │
        ▼
Connector posts response to Slack
```

Agents should **not bypass this flow**.

---

# Modification Guidelines

Agents must follow these rules when editing the repository.

---

## Rule 1: Preserve Service Boundaries

Responsibilities must remain separated:

| Component  | Responsibility    |
| ---------- | ----------------- |
| Connectors | platform adapters |
| API        | orchestration     |
| AI Engine  | model processing  |

Do not merge responsibilities across services.

---

## Rule 2: Avoid Tight Coupling

Services must communicate via:

- REST APIs
- message queues
- shared interfaces

Avoid direct imports between unrelated services.

---

## Rule 3: Maintain Prompt Isolation

AI prompts must live inside:

```
packages/prompts/
```

Do not hardcode prompts inside services.

---

## Rule 4: Maintain Extensibility

The system is designed to support additional connectors.

Agents must avoid changes that prevent adding connectors for new platforms.

---

## Rule 5: Prefer Asynchronous Processing

AI operations may be slow.

Always prefer async processing using queues for AI tasks.

---

# Directory Map

Agents should use the following map to navigate the repository.

```
apps/
    api/
    ai-engine/
    connectors/

packages/
    prompts/
    sdk/
    shared-types/

docs/
    architecture/
    components/
    connectors/

infra/
    docker/
    terraform/
```

---

# Common Tasks for Agents

## Add a New AI Feature

Steps:

1. Define prompt in `packages/prompts`
2. Implement pipeline in `apps/ai-engine`
3. Add API endpoint in `apps/api`
4. Update connectors if necessary

---

## Add a New Chat Platform Connector

Steps:

1. Create directory in:

```
apps/connectors/{platform}
```

2. Implement event handler
3. Forward events to API
4. Implement response sender

Do not embed AI logic in connectors.

---

## Modify AI Prompt Behavior

Prompts should only be modified in:

```
packages/prompts/
```

Ensure prompt changes are compatible with:

- rewrite
- summary
- action extraction pipelines.

---

# Testing Expectations

Agents modifying logic should update or create tests.

Test areas include:

- AI pipeline outputs
- API routes
- connector event handling

Tests should validate both:

- expected outputs
- error handling paths

---

# Observability

System observability includes:

- logging
- metrics
- tracing

Agents should avoid removing instrumentation hooks.

Important metrics include:

- AI latency
- queue processing time
- connector event throughput

---

# Security Considerations

Agents must avoid introducing vulnerabilities.

Important rules:

- never expose API keys
- sanitize external inputs
- protect webhook endpoints
- enforce authentication boundaries

---

# Documentation Updates

If agents introduce architectural changes, they must update:

```
docs/architecture/system-overview.md
```

If new connectors are added, update:

```
docs/connectors/
```

---

# Long-Term Vision

ConvoLayer aims to become:

> The open infrastructure layer for AI-powered communication platforms.

Agents should prioritize changes that:

- maintain modularity
- improve extensibility
- enable new integrations

---

# Summary

AI agents interacting with this repository should:

- respect system architecture
- maintain service boundaries
- keep connectors lightweight
- isolate AI logic in the AI engine
- preserve extensibility

This ensures ConvoLayer remains a **scalable and modular AI communication platform**.
