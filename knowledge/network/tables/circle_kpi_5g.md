---
description: Circle-level NR (5G) network performance KPI dataset used for regional performance monitoring, benchmarking, customer experience analysis, and service quality reporting.
resource: circle_kpi_5g
tags:
- telecom
- 5g
- nr
- circle
- performance
- kpi
title: circle_kpi_5g
type: PostgreSQL Table
---

## Overview

Contains aggregated 5G NR performance measurements at telecom circle level.

Each record represents KPI measurements for a specific circle on a specific date.

Primary use cases:

- Circle-level 5G performance monitoring
- Regional benchmarking
- Accessibility analysis
- Session retainability analysis
- Throughput analysis
- Capacity utilization analysis
- Mobility analysis
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
- max_user_endc
- max_drb_user
- active_ue_dl
- active_ue_ul
- avg_user_endc

### Accessibility

- rasr
- sgnb_addition_sr_lte
- reestablish_sr

### Retainability

- nr_session_ps_drop_rate
- ps_packet_loss_rate_dl
- ps_packet_loss_rate_ul

### Mobility

- inter_sgnodeb_pscell_change_sr
- intra_sgnodeb_pscell_change_sr

### Throughput & Capacity

- dl_user_throughput_mbps
- ul_user_throughput_mbps
- dl_cell_throughput_mbps
- ul_cell_throughput_mbps
- pdsch_utilization
- pusch_utilization
- dl_rbsym_utilization
- ul_rbsym_utilization

### Radio Quality

- avg_cqi
- pusch_rssi
- pusch_sinr
- pucch_sinr
- pucch_rssi

### Modulation Efficiency

- dl_qpsk_sample
- dl_16qam_sample
- dl_64qam_sample
- dl_256qam_sample
- ul_qpsk_sample
- ul_16qam_sample
- ul_64qam_sample
- ul_256qam_sample

### Latency & Efficiency

- dl_latency
- spectral_efficiency_dl
- spectral_efficiency_ul
- avg_admission_holding_time_sec

### Error Metrics

- initial_bler_in_pdsch
- initial_bler_in_pusch

### Customer Experience Metrics

- total_complaints
- voice_complaints
- data_complaints

### Service Availability Metrics

- outage_duration_min

## Related Metrics

- ../../references/metrics/rasr.md
- ../../references/metrics/reestablish_sr.md
- ../../references/metrics/nr_session_ps_drop_rate.md
- ../../references/metrics/dl_user_throughput_mbps.md
- ../../references/metrics/ul_user_throughput_mbps.md
- ../../references/metrics/avg_cqi.md
- ../../references/metrics/spectral_efficiency_dl.md
- ../../references/metrics/spectral_efficiency_ul.md
- ../../references/metrics/total_complaints.md
- ../../references/metrics/outage_duration_min.md

## Related Joins

- ../../references/joins/circle_level_analysis.md
- ../../references/joins/complaint_correlation.md
- ../../references/joins/outage_impact_analysis.md

## Related Tables

- cell_kpi_5g.md
- coverage.md
- complaint.md
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
| max_user_endc | double precision | Maximum EN-DC connected users |
| max_drb_user | double precision | Maximum active DRB users |
| active_ue_dl | double precision | Active downlink users |
| active_ue_ul | double precision | Active uplink users |
| avg_user_endc | double precision | Average EN-DC connected users |
| rasr | double precision | Radio Access Success Rate |
| sgnb_addition_sr_lte | double precision | Secondary gNodeB addition success rate |
| pdsch_utilization | double precision | Downlink resource utilization |
| pusch_utilization | double precision | Uplink resource utilization |
| dl_user_throughput_mbps | double precision | Average downlink user throughput (Mbps) |
| ul_user_throughput_mbps | double precision | Average uplink user throughput (Mbps) |
| avg_cqi | double precision | Average Channel Quality Indicator |
| dl_qpsk_sample | double precision | Downlink QPSK modulation samples |
| dl_16qam_sample | double precision | Downlink 16QAM modulation samples |
| dl_64qam_sample | double precision | Downlink 64QAM modulation samples |
| dl_256qam_sample | double precision | Downlink 256QAM modulation samples |
| ul_qpsk_sample | double precision | Uplink QPSK modulation samples |
| ul_16qam_sample | double precision | Uplink 16QAM modulation samples |
| ul_64qam_sample | double precision | Uplink 64QAM modulation samples |
| ul_256qam_sample | double precision | Uplink 256QAM modulation samples |
| pusch_rssi | double precision | PUSCH Received Signal Strength Indicator |
| inter_sgnodeb_pscell_change_sr | double precision | Inter gNodeB PSCell change success rate |
| intra_sgnodeb_pscell_change_sr | double precision | Intra gNodeB PSCell change success rate |
| nr_session_ps_drop_rate | double precision | 5G session drop rate |
| dl_rbsym_utilization | double precision | Downlink RB symbol utilization |
| ul_rbsym_utilization | double precision | Uplink RB symbol utilization |
| dl_cell_throughput_mbps | double precision | Cell downlink throughput |
| ul_cell_throughput_mbps | double precision | Cell uplink throughput |
| dl_latency | double precision | Downlink latency experienced by users |
| reestablish_sr | double precision | Session re-establishment success rate |
| avg_admission_holding_time_sec | double precision | Average session holding time |
| spectral_efficiency_dl | double precision | Downlink spectral efficiency |
| spectral_efficiency_ul | double precision | Uplink spectral efficiency |
| ps_packet_loss_rate_dl | double precision | Downlink packet loss rate |
| ps_packet_loss_rate_ul | double precision | Uplink packet loss rate |
| pusch_sinr | double precision | PUSCH Signal-to-Interference-plus-Noise Ratio |
| pucch_sinr | double precision | PUCCH Signal-to-Interference-plus-Noise Ratio |
| pucch_rssi | double precision | PUCCH Received Signal Strength Indicator |
| initial_bler_in_pdsch | double precision | Initial BLER in PDSCH |
| initial_bler_in_pusch | double precision | Initial BLER in PUSCH |
| total_complaints | double precision | Total customer complaints reported in the circle |
| voice_complaints | double precision | Voice service related complaints |
| data_complaints | double precision | Data service related complaints |
| outage_duration_min | double precision | Total outage duration in minutes |


## Common Query Patterns

```sql
-- Identify circles with highest 5G session drops
SELECT
    circle_name,
    AVG(nr_session_ps_drop_rate) AS avg_drop_rate
FROM circle_kpi_5g
GROUP BY circle_name
ORDER BY avg_drop_rate DESC;

-- Compare 5G accessibility performance
SELECT
    circle_name,
    AVG(rasr) AS avg_rasr
FROM circle_kpi_5g
GROUP BY circle_name;

-- Analyze outage impact by circle
SELECT
    circle_name,
    SUM(outage_duration_min) AS outage_minutes
FROM circle_kpi_5g
GROUP BY circle_name
ORDER BY outage_minutes DESC;
```