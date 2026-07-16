---
description: Circle-level LTE (4G) network performance KPI dataset used for regional performance monitoring, benchmarking, customer experience analysis, and service quality reporting.
resource: circle_kpi_4g
tags:
- telecom
- 4g
- lte
- circle
- performance
- volte
- kpi
title: circle_kpi_4g
type: PostgreSQL Table
---

## Overview

Contains aggregated LTE (4G) performance measurements at telecom circle level.

Each record represents KPI measurements for a specific circle on a specific date.

Primary use cases:

- Circle-level performance monitoring
- Regional benchmarking
- Accessibility analysis
- Retainability analysis
- Mobility analysis
- Throughput analysis
- Customer experience analysis
- Complaint trend monitoring
- Outage impact assessment
- Executive KPI reporting

## Grain

One record per:

- date
- circle_name

## Key Dimensions

- date
- circle_name

## KPI Categories

### Traffic & Usage

- data_volume_dl_gb
- data_volume_ul_gb
- volte_traffic_erl_total
- max_connected_user
- avg_connected_user

### Accessibility

- volte_cssr
- rrc_setup_sr
- erab_setup_sr
- volte_prach_sr
- csfb_succss_rate

### Retainability

- volte_dcr
- data_drop_call_rate
- volte_packet_loss_rate_dl
- volte_packet_loss_rate_ul
- ps_packet_loss_rate_dl
- ps_packet_loss_rate_ul

### Mobility

- inter_hosr
- intra_hosr
- irat_hosr
- srvcc_sr
- volte_srvcc
- volte_intra_frequency_handover
- volte_inter_frequency_handover
- ping_pong_ho

### Throughput & Capacity

- dl_user_throughput_mbps
- ul_user_throughput_mbps
- dl_cell_throughput_mbps

### Radio Quality

- avg_cqi
- cqi_7
- pusch_rssi
- pusch_sinr
- pucch_rssi
- avg_ue_dist

### Error & Quality Metrics

- ps_bler
- ps_bler_dl
- ps_bler_ul
- volte_bler
- volte_bler_dl
- volte_bler_ul

### Customer Experience Metrics

- total_complaints
- voice_complaints
- data_complaints

### Service Availability Metrics

- outage_duration_min

## Related Metrics

- ../../references/metrics/volte_cssr.md
- ../../references/metrics/volte_dcr.md
- ../../references/metrics/rrc_setup_sr.md
- ../../references/metrics/erab_setup_sr.md
- ../../references/metrics/inter_hosr.md
- ../../references/metrics/intra_hosr.md
- ../../references/metrics/data_drop_call_rate.md
- ../../references/metrics/dl_user_throughput_mbps.md
- ../../references/metrics/ul_user_throughput_mbps.md
- ../../references/metrics/avg_cqi.md
- ../../references/metrics/total_complaints.md
- ../../references/metrics/outage_duration_min.md

## Related Joins

- ../../references/joins/circle_level_analysis.md
- ../../references/joins/complaint_correlation.md
- ../../references/joins/outage_impact_analysis.md

## Related Tables

- cell_kpi_4g.md
- complaint.md
- coverage.md
- outage.md
- rca.md

## Common Join Keys

Primary:

- date
- circle_name

## Schema

| Name | Type | Description |
|--------|--------|--------|
| date | date | Measurement date |
| circle_name | text | Telecom circle or licensed service area |
| data_volume_dl_gb | double precision | Downlink payload traffic volume in GB |
| data_volume_ul_gb | double precision | Uplink payload traffic volume in GB |
| volte_traffic_erl_total | double precision | Total VoLTE traffic in Erlangs |
| max_connected_user | double precision | Peak connected users |
| avg_connected_user | double precision | Average connected users |
| volte_cssr | double precision | VoLTE Call Setup Success Rate |
| rrc_setup_sr | double precision | RRC Setup Success Rate |
| srvcc_sr | double precision | SRVCC Success Rate |
| volte_dcr | double precision | VoLTE Drop Call Rate |
| inter_hosr | double precision | Inter-frequency Handover Success Rate |
| intra_hosr | double precision | Intra-frequency Handover Success Rate |
| volte_packet_loss_rate_dl | double precision | Downlink VoLTE Packet Loss Rate |
| volte_packet_loss_rate_ul | double precision | Uplink VoLTE Packet Loss Rate |
| erab_setup_sr | double precision | E-RAB Setup Success Rate |
| data_drop_call_rate | double precision | Data Session Drop Rate |
| dl_user_throughput_mbps | double precision | Average Downlink User Throughput (Mbps) |
| ul_user_throughput_mbps | double precision | Average Uplink User Throughput (Mbps) |
| dl_cell_throughput_mbps | double precision | Cell Downlink Throughput |
| avg_cqi | double precision | Average Channel Quality Indicator |
| pusch_rssi | double precision | PUSCH Received Signal Strength Indicator |
| pusch_sinr | double precision | PUSCH Signal-to-Interference-plus-Noise Ratio |
| pucch_rssi | double precision | PUCCH Received Signal Strength Indicator |
| irat_hosr | double precision | Inter-RAT Handover Success Rate |
| volte_srvcc | double precision | Successful SRVCC Events |
| volte_prach_sr | double precision | VoLTE PRACH Success Rate |
| total_complaints | double precision | Total customer complaints reported in the circle |
| voice_complaints | double precision | Voice service related complaints |
| data_complaints | double precision | Data service related complaints |
| outage_duration_min | double precision | Total outage duration in minutes |


## Common Query Patterns

```sql
-- Identify worst performing circles by VoLTE DCR
SELECT
    circle_name,
    AVG(volte_dcr) AS avg_volte_dcr
FROM circle_kpi_4g
GROUP BY circle_name
ORDER BY avg_volte_dcr DESC;

-- Compare circle accessibility performance
SELECT
    circle_name,
    AVG(volte_cssr) AS avg_volte_cssr,
    AVG(rrc_setup_sr) AS avg_rrc_setup_sr
FROM circle_kpi_4g
GROUP BY circle_name;

-- Analyze complaints by circle
SELECT
    circle_name,
    SUM(total_complaints) AS total_complaints
FROM circle_kpi_4g
GROUP BY circle_name
ORDER BY total_complaints DESC;
```