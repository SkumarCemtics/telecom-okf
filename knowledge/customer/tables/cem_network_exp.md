---
description: Customer network experience dataset containing user-level quality, coverage, latency, voice, streaming, gaming, and diagnostic indicators used to analyze customer experience and service quality.
resource: cem_network_exp
tags:
- customer
- network-experience
- customer-experience
- quality
- service-performance
title: cem_network_exp
type: PostgreSQL Table
---

## Overview

Contains customer-level network experience measurements collected across voice, data, streaming, gaming, coverage, and service quality dimensions.

Each record represents a customer's network experience for a specific date and location context.

Primary use cases:

- Customer experience analysis
- Service quality monitoring
- Churn root cause analysis
- Network experience diagnostics
- Customer satisfaction assessment
- Voice quality analysis
- Streaming quality analysis
- Gaming experience analysis
- Network issue identification
- Customer journey monitoring

## Grain

One record per:

- date
- user_id
- location_type

## Key Dimensions

- date
- week_number
- user_id
- location_type
- cell_technology
- customer_category
- service_availed
- circle_name
- cell_name
- issue_location

## KPI Categories

### Data Experience

- user_streaming_throughput
- user_latency
- user_packet_loss
- user_video_resolution
- user_buffering_events
- user_data_usages_mb

### Voice Experience

- user_total_calls
- user_repeat_calls
- user_mute_calls
- voice_jitter
- user_voice_drop_call
- user_user_voice_calls

### Gaming & Streaming Experience

- gaming_usage
- streamer_gamer
- streaming_nd_vc_usage

### Mobility & Continuity

- user_irat_events
- user_ping_pong
- user_time_on_tech

### Service Availability

- user_availability
- user_critical_alarms
- user_neighbour_health
- user_transport_health

### Coverage & Quality

- user_coverage
- user_quality
- user_capacity

### Diagnostics & Root Cause

- user_rca
- diagnosis
- primary_rca
- impacted_service
- site_config_change

### Device & Service Context

- device_performance
- service_availed
- customer_category
- cell_technology

## Related Metrics

- ../../references/metrics/user_latency.md
- ../../references/metrics/user_packet_loss.md
- ../../references/metrics/user_availability.md
- ../../references/metrics/user_coverage.md
- ../../references/metrics/user_quality.md
- ../../references/metrics/user_capacity.md
- ../../references/metrics/user_streaming_throughput.md
- ../../references/metrics/user_voice_drop_call.md

## Related Joins

- ../../references/joins/profile_network_experience.md
- ../../references/joins/churn_network_experience.md
- ../../references/joins/customer_quality_correlation.md
- ../../references/joins/network_root_cause_analysis.md

## Related Tables

- cem_profile.md
- cem_churn.md
- cell_kpi_5g.md

## Common Join Keys

Primary:

- user_id

Secondary:

- date
- circle_name
- cell_name
- customer_category

## Common Analysis Questions

- Which customers experience poor network quality?
- How does latency impact customer satisfaction?
- Are packet loss and buffering contributing to churn?
- Which locations generate the worst customer experience?
- What are the primary root causes affecting customers?
- Do premium customers receive better network experience?
- How do gaming and streaming users experience the network?
- Which circles have the highest concentration of service issues?

## Root Cause Categories

Typical causes include:

- Coverage Issues
- Capacity Issues
- Availability Issues
- Transport Issues
- Configuration Issues
- Neighbor Relation Issues
- Voice Quality Issues
- Data Quality Issues

## Schema

| Name | Type | Description |
|--------|--------|--------|
| date | date | Measurement date |
| week_number | double precision | Calendar week number |
| user_id | text | Unique customer identifier |
| location_type | text | Customer location category where experience was measured |
| cell_technology | text | Technology used by the customer (4G, 5G, etc.) |
| customer_category | text | Customer value segment such as Platinum, Gold, Silver, or Other |
| service_availed | text | Primary service usage category |
| streaming_nd_vc_usage | text | Streaming and video conferencing usage classification |
| streamer_gamer | text | Indicates streaming or gaming user behavior |
| gaming_usage | text | Gaming activity classification |
| calls_within_nw | text | Call activity within the operator network |
| user_streaming_throughput | double precision | Streaming throughput experienced by the customer |
| user_latency | double precision | Network latency experienced by the customer |
| user_packet_loss | double precision | Packet loss experienced by the customer |
| user_video_resolution | double precision | Video resolution delivered to the customer |
| user_buffering_events | double precision | Number of video buffering events |
| user_total_calls | double precision | Total voice calls made by the customer |
| user_repeat_calls | double precision | Repeat call attempts indicating possible call quality issues |
| user_mute_calls | double precision | Calls affected by mute or one-way audio issues |
| voice_jitter | text | Voice jitter quality indicator |
| user_irat_events | double precision | Inter-RAT mobility events experienced by the customer |
| user_availability | double precision | Network availability experienced by the customer |
| user_critical_alarms | double precision | Critical alarms impacting the customer |
| user_neighbour_health | double precision | Health of neighboring cells affecting mobility |
| site_config_change | text | Indicates recent site configuration changes |
| user_transport_health | double precision | Transport or backhaul health impacting customer experience |
| user_coverage | double precision | Coverage quality experienced by the customer |
| user_quality | double precision | Overall service quality rating |
| user_capacity | double precision | Capacity availability experienced by the customer |
| user_ping_pong | double precision | Ping-pong handover occurrences affecting the customer |
| user_time_on_tech | double precision | Time spent on the preferred network technology |
| device_performance | text | Customer device performance classification |
| user_user_voice_calls | double precision | Voice call volume generated by the customer |
| user_data_usages_mb | double precision | Total customer data usage in MB |
| user_voice_drop_call | double precision | Count of dropped voice calls experienced by the customer |
| user_repeat_call | double precision | Count of repeated call attempts |
| impacted_service | text | Service impacted by the issue (Voice, Data, or Both) |
| issue_location | text | Customer-reported location of the issue |
| circle_name | text | Telecom circle or licensed service area |
| user_rca | text | Customer-level root cause category |
| diagnosis | text | Diagnostic assessment of the issue |
| primary_rca | text | Primary root cause identified |
| cell_name | text | Serving network cell identifier |