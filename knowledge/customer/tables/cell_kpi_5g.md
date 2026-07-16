---
description: Cell-level NR (5G) network performance KPI dataset used to correlate customer experience, churn behavior, and service quality with underlying 5G network conditions.
resource: cell_kpi_5g
tags:
- telecom
- 5g
- nr
- customer-experience
- network-quality
- kpi
title: cell_kpi_5g
type: PostgreSQL Table
---

## Overview

Contains cell-level 5G NR performance measurements used to understand how network conditions impact customer experience, service quality, and retention.

Each record represents KPI measurements for a specific 5G cell on a specific date.

Primary use cases:

- Customer experience analysis
- Churn root cause analysis
- Network experience correlation
- 5G service quality monitoring
- Throughput analysis
- Accessibility analysis
- Session retainability analysis
- Capacity utilization analysis
- Recommendation and retention analytics

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
- city
- vendor
- pincode
- cell_technology

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

## Related Metrics

- ../../references/metrics/rasr.md
- ../../references/metrics/reestablish_sr.md
- ../../references/metrics/nr_session_ps_drop_rate.md
- ../../references/metrics/dl_user_throughput_mbps.md
- ../../references/metrics/ul_user_throughput_mbps.md
- ../../references/metrics/avg_cqi.md
- ../../references/metrics/user_latency.md
- ../../references/metrics/user_packet_loss.md

## Related Joins

- ../../references/joins/customer_network_experience.md
- ../../references/joins/customer_quality_correlation.md
- ../../references/joins/churn_network_correlation.md

## Related Tables

- cem_network_exp.md
- cem_profile.md
- cem_churn.md

## Common Join Keys

Primary:

- date
- cell_name

Secondary:

- circle_name

## Common Analysis Questions

- Do customers connected to poor-performing 5G cells have higher churn probability?
- How does throughput impact customer experience?
- Are packet loss and latency contributing to churn?
- Which circles have poor customer network experience?
- Do high-value customers experience degraded 5G performance?
- Which network KPIs most strongly impact customer satisfaction?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| date | date | Measurement date |
| circle_name | text | Telecom circle or licensed service area |
| site_name | text | Site identifier |
| cell_name | text | 5G cell identifier |
| frequency | integer | Operating carrier frequency |
| bandwidth | text | Allocated bandwidth |
| city | text | Site city |
| pincode | integer | Site postal code |
| vendor | text | Network equipment vendor |
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
| pusch_rssi | double precision | PUSCH Received Signal Strength Indicator |
| nr_session_ps_drop_rate | double precision | 5G session drop rate |
| dl_latency | double precision | Downlink latency |
| reestablish_sr | double precision | Session re-establishment success rate |
| spectral_efficiency_dl | double precision | Downlink spectral efficiency |
| spectral_efficiency_ul | double precision | Uplink spectral efficiency |
| ps_packet_loss_rate_dl | double precision | Downlink packet loss rate |
| ps_packet_loss_rate_ul | double precision | Uplink packet loss rate |
| pusch_sinr | double precision | PUSCH Signal-to-Interference-plus-Noise Ratio |
| pucch_sinr | double precision | PUCCH Signal-to-Interference-plus-Noise Ratio |
| pucch_rssi | double precision | PUCCH Received Signal Strength Indicator |
| initial_bler_in_pdsch | double precision | Initial BLER in PDSCH |
| initial_bler_in_pusch | double precision | Initial BLER in PUSCH |
| cell_technology | text | Technology type (5G NR) |