# gRPC Infrastructure Management Service

**Client:** NDA client (freelance)
**Role:** Sole developer
**Duration:** 3 months
**Status:** Production

---

## Problem

Non-technical end users needed to configure server connections, but the process required:

1. **Manual config file editing** — error-prone, especially for users without technical background
2. **IT support dependency** — every new user required a support ticket for setup
3. **Cross-platform delivery** — configurations needed to work on both mobile and desktop clients

## Solution

Built a Telegram bot + gRPC backend combination:

**gRPC Service Layer:**
- Spring Boot 3.4 with gRPC v1.71 and Protobuf v4
- Strongly typed service contracts (1,525 lines of .proto definitions)
- Server-side configuration generation based on user parameters

**User Experience:**
- Telegram bot interface — users interact through a familiar chat UI
- Automated configuration generation — no manual file editing
- QR code delivery (ZXing library) — users scan a code on their mobile device for instant setup
- PostgreSQL for user profiles and configuration history

**Code Quality:**
- MapStruct for clean DTO ↔ Entity mapping
- Flyway for database migrations

## Result

| Metric | Value |
|--------|-------|
| IT support tickets for setup | **~0** (was 100% manual — every user needed IT help) |
| User self-service rate | **100%** — no technical knowledge required |
| Codebase | **7,533** Java LOC + **2,224** lines Protobuf (65 .proto files) |
| Setup time per user | **Under 1 minute** (was 15–30 min with IT support) |

## Tech Stack

`Spring Boot 3.4` `Java 21` `gRPC v1.71` `Protobuf v4` `PostgreSQL` `Flyway` `ZXing (QR)` `MapStruct` `Telegram Bot API` `Docker`
