---
description: Root Cause Analysis (RCA) dataset containing network incidents, fault classifications, ownership information, resolution status, remediation recommendations, and operational root causes.
resource: rca
tags:
- telecom
- rca
- operations
- troubleshooting
- service-quality
title: rca
type: PostgreSQL Table
---

## Overview

Contains root cause analysis records used to diagnose, classify, track, and resolve network issues impacting service quality and customer experience.

Each record represents an investigated network issue associated with a specific cell and date.

Primary use cases:

- Root cause identification
- Service degradation analysis
- Network troubleshooting
- Incident management
- Resolution tracking
- Network optimization
- Preventive maintenance planning
- Customer complaint correlation

## Grain

One record per:

- date
- cell_name
- issue

## Key Dimensions

- date
- issue_startdate
- circle_name
- cell_name
- cluster_id
- technology
- priority_category
- assigned_team
- ticket_status

## RCA Categories

### Incident Management

- ticket_status
- priority_category
- days_to_resolve
- assigned_team

### Network Domains

- primary_rca
- radio
- capacity
- avail
- fm
- cm
- pm
- tx

### Neighbor & Optimization Issues

- nbr_issue
- nbr_mat
- nbr_cm_phy
- nbr_capacity
- tilt
- new_carrier_add

### Business Impact

- revenue

### Recommendations

- recommendation_1
- recommendation_2

## Related Metrics

- ../../references/metrics/days_to_resolve.md
- ../../references/metrics/outage_duration_min.md
- ../../references/metrics/service_availability.md

## Related Joins

- ../../references/joins/outage_rca.md
- ../../references/joins/complaint_rca.md
- ../../references/joins/root_cause_analysis.md

## Related Tables

- outage.md
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

- circle_name
- technology

## Common Root Causes

- Radio
- Availability
- Capacity
- Fault Management (FM)
- Configuration Management (CM)
- Performance Management (PM)
- Transport (TX)
- Neighbor Relationship Issues
- Carrier Expansion Requirements
- Tilt Optimization Issues

## Common Analysis Questions

- What are the most common causes of network degradation?
- Which RCA categories generate the highest complaints?
- Which issues require the longest resolution time?
- Which teams resolve incidents fastest?
- Are outages associated with specific root causes?
- Which circles experience recurring Radio or Availability issues?
- What corrective actions are recommended most frequently?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| days_to_resolve | integer | Number of days required to resolve the issue |
| date | date | RCA reporting date |
| issue_startdate | date | Date when the issue was first detected |
| cell_name | text | Network cell affected by the issue |
| cluster_id | integer | Cluster identifier grouping related network elements |
| priority_category | text | Priority classification of the issue |
| circle_name | text | Telecom circle or licensed service area |
| ticket_status | text | Current investigation or resolution status |
| rca_summary | text | Summary of the diagnosed issue |
| technology | text | Network technology affected by the issue |
| revenue | text | Business or revenue impact classification |
| assigned_team | text | Team responsible for resolution |
| primary_rca | text | Primary root cause category |
| pm | text | Performance Management related issue indicator |
| cm | text | Configuration Management related issue indicator |
| fm | text | Fault Management related issue indicator |
| avail | text | Availability related issue indicator |
| radio | text | Radio network related issue indicator |
| capacity | text | Capacity related issue indicator |
| tilt | text | Antenna tilt related issue indicator |
| nbr_issue | text | Neighbor relation issue indicator |
| nbr_mat | text | Neighbor matrix related issue indicator |
| nbr_cm_phy | text | Neighbor configuration or physical relation issue indicator |
| nbr_capacity | text | Neighbor capacity issue indicator |
| new_carrier_add | text | Requirement for new carrier deployment indicator |
| tx | text | Transport or transmission related issue indicator |
| recommendation_1 | text | Primary recommended corrective action |
| recommendation_2 | text | Secondary recommended corrective action |
