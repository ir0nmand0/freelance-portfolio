# Enterprise Field Service Management System

**Client:** NDA client (Fortune 500 energy company subsidiary)
**Role:** Developer, collaborating with field engineering teams and management
**Duration:** 2+ years (started 2022, active development)
**Status:** Production

---

## Problem

Fortune 500 energy company with 1,000+ remote sites had no systematic approach to:

1. **Pre-trip safety checks** — field engineers dispatched without standardized safety verification, creating compliance and liability risk
2. **Duty scheduling** — shift rotation managed manually across multiple teams and regions via spreadsheets
3. **Reporting** — management relied on manual data collection for service metrics, causing delays and inaccuracies

## Solution

Built a Telegram-based field service control system:

**Access Control:**
- Spring Security with 7-role hierarchical model (from field engineer to regional director)
- Role-based data visibility — each role sees only their authorized scope

**Safety Compliance:**
- Mandatory pre-trip questionnaire — the system blocks dispatch until all safety checks are completed
- Questionnaire responses stored with timestamps for audit trail

**Reporting Engine:**
- PDF report generation (iText + JasperReports) — automated daily/weekly/monthly reports
- Excel exports (Apache POI) for management dashboards and ad-hoc analysis
- Email notification system for escalations and schedule changes

**Operations:**
- Duty schedule management with shift rotation logic
- PostgreSQL with Flyway migrations
- Docker deployment with CI/CD

## Result

| Metric | Value |
|--------|-------|
| Safety compliance | **100% enforced** — no field visit possible without completing pre-trip check |
| Reporting | Automated — weekly reports that took 2 days of manual work now generated instantly |
| Codebase | **20,673** Java LOC, **213** files |
| Coverage | Field engineering teams across 8+ regions |
| Production | Running since 2022, 3+ years of uptime |

## Tech Stack

`Spring Boot 3.4` `Java 21` `PostgreSQL` `Flyway` `Spring Security` `Spring Mail` `iText` `JasperReports` `Apache POI` `Telegram Bot API` `Docker`
