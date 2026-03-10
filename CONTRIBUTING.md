# CONTRIBUTING.md

## Contributing to ConvoLayer

First of all — **thank you for considering contributing to ConvoLayer**.

ConvoLayer is an open-source platform that brings **AI-powered intelligence into team communication platforms** such as Slack, Discord, and Microsoft Teams.

We welcome contributions from developers, designers, researchers, and technical writers.

---

# Ways to Contribute

You can contribute in many ways, including:

### Code Contributions

- implementing new features
- fixing bugs
- improving performance
- adding new chat connectors

---

### AI Improvements

- improving prompts
- refining response formats
- evaluating model outputs

---

### Documentation

- improving architecture documentation
- adding tutorials
- improving developer onboarding

---

### Integrations

Build new connectors for platforms such as:

- Telegram
- WhatsApp
- GitHub Discussions
- Web chat widgets

---

# Development Workflow

ConvoLayer uses a standard GitHub workflow.

### 1. Fork the Repository

Click **Fork** and clone your fork locally.

```bash
git clone https://github.com/YOUR_USERNAME/convopilot.git
```

---

### 2. Create a Branch

Use descriptive branch names.

Examples:

```bash
feature/slack-thread-summary
fix/api-authentication-bug
docs/improve-architecture-guide
```

---

### 3. Make Your Changes

Follow the project architecture and development guidelines.

Key rules:

- keep services modular
- maintain clean separation of responsibilities
- avoid introducing tight coupling between components

---

### 4. Run the Project Locally

Install dependencies:

```bash
npm install
```

Run the development environment:

```bash
docker-compose up
```

Start the development server:

```bash
npm run dev
```

---

### 5. Submit a Pull Request

Push your branch and open a Pull Request.

Please include:

- a clear description of the change
- screenshots or examples if applicable
- relevant issue references

Example:

```
Fixes #42
Adds Slack thread summarization support.
```

---

# Project Structure

The repository uses a **monorepo architecture**.

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

infra/
    docker/
    terraform/
```

Please keep code changes within the correct module.

---

# Code Style Guidelines

### General Principles

- write clear, readable code
- prefer simplicity over cleverness
- maintain consistent naming

---

### Type Safety

Ensure type compatibility when modifying shared packages.

Shared interfaces are located in:

```
packages/shared-types
```

---

### Prompt Design

All AI prompts must live in:

```
packages/prompts
```

Do not embed prompts inside application code.

---

# Adding a New Connector

Connectors allow ConvoLayer to integrate with new chat platforms.

Steps:

### 1. Create Connector Directory

```
apps/connectors/{platform}
```

Example:

```
apps/connectors/telegram
```

---

### 2. Implement Connector Logic

Responsibilities:

- receive platform events
- forward messages to the ConvoLayer API
- return AI responses

Connectors should remain **thin adapters**.

---

### 3. Update Documentation

Add documentation under:

```
docs/connectors/
```

---

# Adding a New AI Feature

Example features:

- message classification
- sentiment analysis
- meeting summarization

Steps:

1. Define prompt template in:

```
packages/prompts
```

2. Implement logic in:

```
apps/ai-engine
```

3. Expose API endpoint in:

```
apps/api
```

---

# Testing

All new features should include tests when possible.

Test areas include:

- API endpoints
- AI response formatting
- connector event handling

Tests help ensure that the platform remains stable as new features are added.

---

# Good First Issues

If you are new to the project, look for issues labeled:

```
good first issue
```

These tasks are designed to help contributors get familiar with the codebase.

Examples include:

- improving documentation
- adding prompt templates
- building small connector features

---

# Code of Conduct

Please be respectful and collaborative when interacting with the community.

We want ConvoLayer to be a welcoming environment for developers of all experience levels.

---

# Questions or Discussions

If you have questions or ideas, feel free to:

- open a GitHub issue
- start a discussion
- submit a proposal

---

# Thank You

Every contribution helps make ConvoLayer better.

We appreciate the time and effort you invest in improving the project.
