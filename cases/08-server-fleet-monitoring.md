# Server Fleet Monitoring & Predictive Analytics Platform

**Client:** NDA client (Fortune 500 energy company subsidiary)
**Role:** Sole developer (backend + frontend via AI pair programming)
**Duration:** 4+ months (active development)
**Status:** In development / staging

---

## Problem

2,000+ servers across a national gas station network had **zero monitoring**:

1. **No visibility** — disk failures, memory issues, and hardware degradation discovered only after causing downtime
2. **No dedicated monitoring infra** — deploying Zabbix/Nagios across 2,000+ sites was not feasible (budget, network constraints)
3. **Reactive maintenance** — every failure was an emergency, with no ability to predict or prevent

## Solution

Built a predictive monitoring platform that leverages the existing Enterprise Service Bus — no new infrastructure deployment needed:

**Backend Architecture (17-module Maven modular monolith):**
- Spring Boot 4, Java 25
- SNMP v3 data collection (authPriv: SHA authentication + AES encryption) via SNMP4J
- PostgreSQL 18 for metric storage and analytics
- Redis 8 for caching frequently accessed metrics

**Predictive Analytics:**
- Disk lifecycle prediction based on SMART data trends
- Proactive alerting before failures occur
- Historical trend analysis for capacity planning

**Security & Enterprise Integration:**
- Spring Security with Kerberos/SPNEGO + LDAP for enterprise SSO
- Role-based access control integrated with Active Directory
- MapStruct for DTO mapping, Springdoc-OpenAPI for API documentation

**Frontend:**
- React 19, TypeScript, TanStack React Query
- Developed via AI pair programming with Claude Code

## Result

| Metric | Value |
|--------|-------|
| Coverage | **2,000+ hosts** — from zero to full visibility |
| Approach | Predictive (proactive) vs. reactive maintenance |
| Infrastructure cost | **$0 additional** — uses existing ESB |
| Architecture | **17-module** Maven modular monolith |
| Auth | Enterprise SSO (Kerberos/SPNEGO + LDAP) |

## Tech Stack

`Spring Boot 4` `Java 25` `PostgreSQL 18` `Redis 8` `SNMP4J (SNMPv3)` `Spring Security (Kerberos/SPNEGO + LDAP)` `MapStruct` `Springdoc-OpenAPI` `React 19` `TypeScript` `TanStack React Query` `Maven (17 modules)` `Docker`
