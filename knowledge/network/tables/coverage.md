---
description: Coverage and mobility dataset containing signal quality, handover performance, call outcomes, and service experience measurements used to evaluate network coverage and user experience.
resource: coverage
tags:
- telecom
- coverage
- radio
- mobility
- service-quality
title: coverage
type: PostgreSQL Table
---

## Overview

Contains network coverage, radio quality, mobility, and call experience measurements at cell level.

Each record represents coverage and mobility measurements for a specific cell on a specific date.

Primary use cases:

- Coverage analysis
- Signal quality assessment
- Mobility analysis
- Handover performance monitoring
- VoLTE service quality analysis
- Customer experience correlation
- Network optimization
- Root cause investigations

## Grain

One record per:

- date
- cell_name

## Key Dimensions

- date
- circle_name
- cell_name
- site_name
- frequency
- bandwidth
- vendor
- city
- pincode
- cell_technology

## KPI Categories

### Coverage & Radio Quality

- rsrp
- rsrq

### Mobility Performance

- irat_4g_3g_attempts_success
- irat_4g_2g_attempts_success
- s1_intra_ho_attempts_success
- s1_inter_ho_attempts_success
- x2_intra_ho_attempts_success
- x2_inter_ho_attempts_success
- srvcc_attempts_success

### Mobility Failures

- irat_4g_3g_attempts_failure
- irat_4g_2g_attempts_failure
- srvcc_attempts_failure
- s1_intra_failures
- s1_inter_failures
- x2_intra_failures
- x2_inter_failures

### Handover Performance

- total_ho_attempts_success
- total_ho_attempts_failure
- total_x2ho
- total_x2ho_data
- total_x2ho_volte

### Voice Experience

- total_call_count_volte
- total_normal_calls_volte
- total_block_calls_volte
- total_drop_calls_volte
- total_setup_failure_volte
- total_cs_fallback_volte

### Data Experience

- total_normal_calls_data
- total_block_calls_data
- total_drop_calls_data
- total_setup_failure_data
- total_cs_fallback_data

### Service Quality

- total_normal_calls
- total_unspecified_calls
- total_block_calls
- total_drop_calls
- total_setup_failure
- total_cs_fallback

### User Behaviour

- latched_instances

## Related Metrics

- ../../references/metrics/rsrp.md
- ../../references/metrics/rsrq.md
- ../../references/metrics/handover_success_rate.md
- ../../references/metrics/irat_success_rate.md
- ../../references/metrics/srvcc_success_rate.md
- ../../references/metrics/drop_call_rate.md

## Related Joins

- ../../references/joins/coverage_4gkpi.md
- ../../references/joins/coverage_5gkpi.md
- ../../references/joins/complaint_coverage.md
- ../../references/joins/cell_level_analysis.md

## Related Tables

- complaint.md
- cell_kpi_4g.md
- cell_kpi_5g.md
- outage.md
- rca.md

## Common Join Keys

Primary:

- date
- cell_name

Secondary:

- circle_name
- site_name

## Common Analysis Questions

- Which cells have poor RSRP or RSRQ?
- Are mobility failures concentrated in specific circles?
- Which cells experience excessive handover failures?
- Is poor coverage contributing to customer complaints?
- Which locations have high call drop rates?
- Are VoLTE users affected by mobility issues?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| date | date | Measurement date |
| circle_name | text | Telecom circle or licensed service area |
| cell_name | text | Network cell identifier |
| site_name | text | Site identifier |
| frequency | integer | Operating carrier frequency |
| bandwidth | text | Allocated bandwidth |
| vendor | text | Network equipment vendor |
| city | text | Site location city |
| pincode | integer | Site postal code |
| rsrp | double precision | Reference Signal Received Power used to evaluate signal strength |
| rsrq | double precision | Reference Signal Received Quality used to evaluate signal quality |
| irat_4g_3g_attempts_success | double precision | Successful 4G to 3G inter-RAT handovers |
| irat_4g_2g_attempts_success | double precision | Successful 4G to 2G inter-RAT handovers |
| s1_intra_ho_attempts_success | double precision | Successful intra-site S1 handovers |
| s1_inter_ho_attempts_success | double precision | Successful inter-site S1 handovers |
| x2_intra_ho_attempts_success | double precision | Successful intra-site X2 handovers |
| x2_inter_ho_attempts_success | double precision | Successful inter-site X2 handovers |
| srvcc_attempts_success | double precision | Successful SRVCC handovers |
| irat_4g_3g_attempts_failure | double precision | Failed 4G to 3G handovers |
| irat_4g_2g_attempts_failure | double precision | Failed 4G to 2G handovers |
| srvcc_attempts_failure | double precision | Failed SRVCC handovers |
| total_call_count_volte | double precision | Total VoLTE call attempts |
| total_ho_attempts_success | double precision | Total successful handovers |
| total_ho_attempts_failure | double precision | Total failed handovers |
| total_normal_calls | double precision | Successfully completed calls |
| total_drop_calls | double precision | Dropped calls |
| total_setup_failure | double precision | Call setup failures |
| total_cs_fallback | double precision | Circuit switched fallback attempts |
| total_normal_calls_data | double precision | Successfully completed data sessions |
| total_drop_calls_data | double precision | Dropped data sessions |
| total_setup_failure_data | double precision | Data session setup failures |
| total_normal_calls_volte | double precision | Successfully completed VoLTE calls |
| total_drop_calls_volte | double precision | Dropped VoLTE calls |
| total_setup_failure_volte | double precision | VoLTE setup failures |
| cell_technology | text | Technology type associated with the measurement |

## Common Query Patterns

```sql
-- Identify cells with poor coverage
SELECT
    cell_name,
    AVG(rsrp) AS avg_rsrp,
    AVG(rsrq) AS avg_rsrq
FROM coverage
GROUP BY cell_name
ORDER BY avg_rsrp ASC;

-- Analyze handover performance
SELECT
    circle_name,
    SUM(total_ho_attempts_success) AS ho_success,
    SUM(total_ho_attempts_failure) AS ho_failure
FROM coverage
GROUP BY circle_name;

-- Analyze VoLTE call drops
SELECT
    cell_name,
    SUM(total_drop_calls_volte) AS volte_drops
FROM coverage
GROUP BY cell_name
ORDER BY volte_drops DESC;
```