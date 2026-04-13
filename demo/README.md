# Live Code & Public Repositories

Public repositories and live deployments that demonstrate my engineering skills. All code is mine — no team projects except where noted.

---

## Live Production Systems

| Project | URL | What it is |
|---------|-----|------------|
| Education Platform #1 | [learn.arcanespectrum.ru](https://learn.arcanespectrum.ru/) | Online courses with Telegram bot, triple payment integration, PDF certificates |
| Education Platform #2 | [learn.domhair.ru](https://learn.domhair.ru/) | Second instance — same backend, different client and course content |
| B2C Service | [arcanespectrum.ru](https://arcanespectrum.ru/) | Landing page for AI-powered subscription platform with Telegram bot backend |

> All three services run on my GitOps infrastructure: GitHub Actions → Harbor → ArgoCD → K3s cluster
>
> **Note:** Client-facing content is in Russian. The backend architecture, payment integration, and deployment infrastructure are language-independent.

---

## Microservices & Spring Cloud

### [java-plus-graduation](https://github.com/ir0nmand0/java-plus-graduation) — Diploma Project

Event management platform with 3 microservices: `core` + `stats` + `recommendation`

**Demonstrates:** Multi-module Maven, Kafka (event streaming), Avro (schema registry), gRPC + Protobuf (inter-service communication), Spring Cloud, QueryDSL, JaCoCo coverage, SpotBugs static analysis, Checkstyle

### [plus-smart-home-tech](https://github.com/ir0nmand0/plus-smart-home-tech) — Smart Home Platform

IoT platform with `commerce` and `telemetry` microservices

**Demonstrates:** Eureka service discovery, Kafka + Avro for telemetry streaming, gRPC for synchronous calls, Spring Cloud, Confluent Platform integration, Flyway migrations, Mermaid architectural diagrams

---

## Spring Boot & REST API Design

### [java-shareit](https://github.com/ir0nmand0/java-shareit) — Sharing Economy Service

Item rental/sharing service with Gateway + Server architecture

**Demonstrates:** Spring Security, API Gateway pattern, MapStruct DTO mapping, JaCoCo, SpotBugs, Checkstyle, Docker Compose

### [java-filmorate](https://github.com/ir0nmand0/java-filmorate) — Social Film Rating Network

Film rating platform with social features (friends, recommendations)

**Demonstrates:** Spring Boot, PostgreSQL, JPA, ER diagram design, REST API

---

## Algorithms & Computer Science

### [leetcode-solutions](https://github.com/ir0nmand0/leetcode-solutions) — LeetCode by Patterns

Systematic algorithm practice organized by patterns: Two Pointers, Sliding Window, Binary Search, HashMap, Stack, Trees, DP, Greedy

**Demonstrates:** Clean Java solutions with pattern-based organization

---

## How I Work

All my production projects follow the same engineering practices:

```
Code Quality:        Maven multi-module, SpotBugs, Checkstyle, JaCoCo
Testing:             JUnit 5, TestContainers (real DB in tests)
Database:            PostgreSQL + Flyway (version-controlled migrations)
Containerization:    Multi-stage Docker builds, JVM tuning (G1GC, GC logging)
CI/CD:               GitHub Actions → Harbor → ArgoCD (GitOps)
Monitoring:          Prometheus + Grafana + Loki (Spring Boot Actuator + Micrometer)
Architecture docs:   Mermaid diagrams, OpenAPI/Swagger specs
```

> **Note:** Most production repositories are private (NDA). The public repos above are educational projects that demonstrate the same engineering approach I apply to commercial work. See [cases/](../cases/) for production project details.
