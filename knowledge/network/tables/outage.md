---
description: Network outage dataset containing outage events, durations, affected cells, technologies, vendors, and outage causes used for service availability and impact analysis.
resource: outage
tags:
- telecom
- outage
- availability
- operations
title: outage
type: PostgreSQL Table
---

## Overview

Contains network outage events affecting telecom services.

Each record represents an outage event associated with a specific cell and date.

Primary use cases:

- Outage monitoring
- Service availability analysis
- Customer impact assessment
- Network operations reporting
- Root cause investigations
- Vendor performance analysis
- Technology-specific outage tracking

## Grain

One record per:

- date
- cell_name

## Key Dimensions

- date
- circle_name
- site_name
- cell_name
- vendor
- cell_technology

## KPI Categories

### Service Availability

- outage_duration_min

### Outage Classification

- outage_cause
- vendor
- cell_technology

### Impact Analysis

- affected cell
- affected site
- affected circle
- affected technology

## Related Metrics

- ../../references/metrics/outage_duration_min.md
- ../../references/metrics/service_availability.md

## Related Joins

- ../../references/joins/outage_rca.md
- ../../references/joins/complaint_outage.md
- ../../references/joins/outage_impact_analysis.md

## Related Tables

- rca.md
- complaint.md
- coverage.md
- cell_kpi_4g.md
- cell_kpi_5g.md
- circle_kpi_4g.md
- circle_kpi_5g.md

## Common Join Keys

Primary:

- date
- cell_name

Secondary:

- site_name
- circle_name
- cell_technology

## Common Analysis Questions

- Which circles experience the highest outage duration?
- Which outage causes occur most frequently?
- Which vendors contribute most to outages?
- Which technologies are most affected by outages?
- Are outages driving customer complaints?
- What is the impact of outages on network KPIs?
- Which sites experience recurring outages?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| circle_name | text | Telecom circle or licensed service area impacted by the outage |
| vendor | text | Network equipment vendor associated with the affected site |
| cell_technology | text | Technology affected by the outage (4G, 5G, etc.) |
| date | date | Outage occurrence date |
| cell_name | text | Affected network cell identifier |
| site_name | text | Site associated with the outage |
| outage_duration_min | double precision | Total outage duration in minutes |
| outage_cause | text | Reported cause of the outage event |
| cell_tech_1 | text | Additional technology classification associated with the outage |

## Common Query Patterns

```sql
-- Identify outage events with the longest duration
SELECT
    date,
    circle_name,
    site_name,
    cell_name,
    outage_duration_min
FROM outage
ORDER BY outage_duration_min DESC
LIMIT 10;

-- Analyze outage duration by outage cause
SELECT
    outage_cause,
    COUNT(*) AS outage_count,
    SUM(o*tage_duration_min) AS total_outage*duration_min
FROM outage
GROUP BY *utage_cause
ORDER BY total_outage_duration_min DESC;

-- Compare outage impact by vendor and technology
SELECT
    vendor,
    cell_technology,
    COUNT(*) AS outage_count,
    AVG(outage_duration_min) AS avg_outage_duration_min
FROM outage
GROUP BY vendor, cell_technology
ORDER BY avg_outage_duration_min DESC;
```
