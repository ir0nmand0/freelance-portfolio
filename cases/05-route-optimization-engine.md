# Route Optimization Engine

**Client:** NDA client (Fortune 500 energy company subsidiary)
**Role:** Developer
**Duration:** 1 month
**Status:** Production

---

## Problem

Enterprise client needed to calculate optimal routes from service bases to 2,000+ locations (gas stations across a national network). The existing process:

1. **Fully manual** — dispatchers calculated routes by hand using paper maps and web tools
2. **Inaccurate** — manual calculations didn't account for real-time road conditions, one-way streets, or seasonal restrictions
3. **Time-consuming** — calculating routes for the full network took days of manual work

## Solution

Built a batch route calculation engine:

**Core Logic:**
- Spring Boot 3.5, Java 21, WebFlux for non-blocking I/O
- GraphHopper v10 for offline routing (road graph stored locally — no per-request API costs)
- Regional Maps API for real-time traffic adjustments and geocoding (same integration pattern as Google Maps Directions API)
- Reactive streams for parallel route calculation

**Business Integration:**
- Excel input/output (Apache POI) — business users upload a spreadsheet, get results in the same format
- Cross-platform: runs on both Windows (.cmd) and Linux (.bash)
- Docker containerized for server deployment
- Template-based output with customizable report formats

## Result

| Metric | Value |
|--------|-------|
| Locations covered | **2,000+** routes calculated automatically |
| Processing time | **~5 minutes** for full network (was 3+ days of manual work) |
| Accuracy | Real-time road conditions and traffic data vs. manual estimation |
| Codebase | **2,416** Java LOC, production-ready |
| Cost | Zero per-request costs (local GraphHopper graph) |

## Tech Stack

`Spring Boot 3.5` `Java 21` `WebFlux` `GraphHopper v10` `Maps Geocoding API` `Apache POI` `Docker`
