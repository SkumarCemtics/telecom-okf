---
description: Customer complaint dataset containing voice and data service complaints mapped to network cells and circles for customer experience and service quality analysis.
resource: complaint
tags:
- telecom
- complaint
- customer-experience
- service-quality
title: complaint
type: PostgreSQL Table
---

## Overview

Contains customer complaints associated with network services.

Each record represents complaint counts for a specific cell on a specific date.

Primary use cases:

- Customer experience analysis
- Service quality monitoring
- Complaint hotspot identification
- Coverage issue correlation
- Network performance impact assessment
- Outage impact analysis
- Root cause investigations

## Grain

One record per:

- date
- cell_name

## Key Dimensions

- date
- circle_name
- cell_name
- cell_technology

## KPI Categories

### Customer Experience

- data_complaints
- voice_complaints

### Complaint Distribution

- circle-level complaint trends
- technology-specific complaints
- cell-level complaint hotspots

## Related Metrics

- ../../references/metrics/data_complaints.md
- ../../references/metrics/voice_complaints.md
- ../../references/metrics/total_complaints.md

## Related Joins

- ../../references/joins/complaint_coverage.md
- ../../references/joins/complaint_outage.md
- ../../references/joins/complaint_rca.md
- ../../references/joins/customer_experience_analysis.md

## Related Tables

- coverage.md
- outage.md
- rca.md
- cell_kpi_4g.md
- cell_kpi_5g.md
- circle_kpi_4g.md
- circle_kpi_5g.md

## Common Join Keys

Primary:

- date
- cell_name

Secondary:

- circle_name
- cell_technology

## Common Analysis Questions

- Which cells generate the highest customer complaints?
- Are complaints correlated with poor coverage?
- Are outages driving customer complaints?
- Which circles show deteriorating customer experience?
- Are voice complaints or data complaints increasing?
- Which network KPIs correlate with complaint growth?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| date | date | Complaint reporting date |
| circle_name | text | Telecom circle or licensed service area |
| cell_name | text | Network cell associated with the complaint |
| data_complaints | integer | Number of customer complaints related to mobile data services |
| voice_complaints | integer | Number of customer complaints related to voice services |
| cell_technology | text | Technology associated with the complaint (4G, 5G, etc.) |

## Common Query Patterns

```sql
-- Identify cells with highest complaints
SELECT
    cell_name,
    SUM(data_complaints + voice_complaints) AS total_complaints
FROM complaint
GROUP BY cell_name
ORDER BY total_complaints DESC;

-- Analyze complaints by circle
SELECT
    circle_name,
    SUM(data_complaints) AS data_complaints,
    SUM(voice_complaints) AS voice_complaints
FROM complaint
GROUP BY circle_name;

-- Analyze complaint trend over time
SELECT
    date,
    SUM(data_complaints) AS data_complaints,
    SUM(voice_complaints) AS voice_complaints
FROM complaint
GROUP BY date
ORDER BY date;
```
