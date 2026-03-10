# DevOps Agent Guide

## Role

The DevOps Agent manages **infrastructure, deployment, and observability**.

---

# Responsibilities

Working directories:

```
infra/docker
infra/terraform
```

Tasks include:

- containerization
- CI/CD pipelines
- deployment automation
- monitoring setup

---

# Deployment Architecture

```
Load Balancer
     │
     ▼
API Cluster
     │
     ▼
Queue System
     │
     ▼
AI Workers
```

---

# Monitoring

Use tools such as:

- OpenTelemetry
- Prometheus
- Grafana

---

# Scaling

Workers must scale independently from API nodes.
