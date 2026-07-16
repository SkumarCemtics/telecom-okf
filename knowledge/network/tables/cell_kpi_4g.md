---
description: Cell-level LTE (4G) network performance KPI dataset used for accessibility, retainability, mobility, throughput, capacity, and VoLTE service analysis.
resource: cell_kpi_4g
tags:
- telecom
- 4g
- lte
- performance
- volte
- kpi
title: cell_kpi_4g
type: PostgreSQL Table
---

## Overview

Contains cell-level LTE (4G) performance measurements for network monitoring and service quality analysis.

Each record represents KPI measurements for a specific cell on a specific date.

Primary use cases:

- LTE network performance monitoring
- VoLTE service analysis
- Accessibility analysis
- Retainability analysis
- Mobility analysis
- Throughput analysis
- Capacity analysis
- Customer complaint correlation
- Root cause analysis

## Grain

One record per:

- date
- cell_name

## Key Dimensions

- date
- circle_name
- site_name
- cell_name
- frequency
- bandwidth
- cell_technology
- vendor
- city
- pincode

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

## Related Joins

- ../../references/joins/coverage_4gkpi.md
- ../../references/joins/cell_level_analysis.md

## Related Tables

- circle_kpi_4g.md
- coverage.md
- complaint.md
- outage.md
- rca.md

## Common Join Keys

Primary:

- date
- cell_name

Secondary:

- circle_name
- site_name

## Schema

| Name | Type | Description |
|--------|--------|--------|
| date | date | Measurement date |
| circle_name | text | Telecom circle or licensed service area |
| site_name | text | Unique site identifier |
| cell_name | text | Unique LTE cell identifier |
| frequency | integer | LTE carrier frequency |
| bandwidth | text | LTE bandwidth configuration |
| cell_technology | text | Technology type (4G LTE) |
| vendor | text | Network equipment vendor |
| city | text | Site location city |
| pincode | integer | Site location postal code |
| data_volume_dl_gb | double precision | Downlink payload traffic volume in GB |
| data_volume_ul_gb | double precision | Uplink payload traffic volume in GB |
| volte_traffic_erl_total | double precision | Total VoLTE traffic in Erlangs |
| max_connected_user | double precision | Maximum connected users |
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
| cqi_7 | double precision | CQI Category Metric |
| rank2_samples | double precision | Rank-2 MIMO Sample Count |
| ps_bler | double precision | Packet Switched Block Error Rate |
| volte_bler | double precision | VoLTE Block Error Rate |
| dl_cell_throughput_mbps | double precision | Cell Downlink Throughput |
| irat_hosr | double precision | Inter-RAT Handover Success Rate |
| csfb_succss_rate | double precision | Circuit Switched Fallback Success Rate |
| avg_cqi | double precision | Average Channel Quality Indicator |
| volte_srvcc | double precision | Successful SRVCC Events |
| volte_intra_frequency_handover | double precision | VoLTE Intra-Frequency Handover Performance |
| volte_inter_frequency_handover | double precision | VoLTE Inter-Frequency Handover Performance |
| volte_prach_sr | double precision | VoLTE PRACH Success Rate |
| volte_successful_calls_ratio | double precision | Successful VoLTE Calls Ratio |
| ul_user_throughput_mbps | double precision | Average Uplink User Throughput (Mbps) |
| srvcc_rate_per_call | double precision | SRVCC Rate per Call |
| ps_bler_dl | double precision | Downlink PS BLER |
| ps_bler_ul | double precision | Uplink PS BLER |
| volte_bler_dl | double precision | Downlink VoLTE BLER |
| volte_bler_ul | double precision | Uplink VoLTE BLER |
| pusch_rssi | double precision | PUSCH Received Signal Strength Indicator |
| pusch_sinr | double precision | PUSCH Signal-to-Interference-plus-Noise Ratio |
| pucch_rssi | double precision | PUCCH Received Signal Strength Indicator |
| avg_ue_dist | double precision | Average User Distance from Serving Site |
| ps_packet_loss_rate_dl | double precision | Downlink Packet Loss Rate |
| ps_packet_loss_rate_ul | double precision | Uplink Packet Loss Rate |
| ping_pong_ho | double precision | Ping-Pong Handover Rate |