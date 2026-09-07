---
title: Network Database
type: PostgreSQL database
description: Telecom radio network database for analyzing cells, sites, circles, 4G/LTE and 5G/NR radio performance, network KPIs, coverage, outages, network-related complaints, and root cause analysis. This database focuses on network infrastructure and network performance rather than subscriber or customer-profile information.

tags:
  - network
  - radio network
  - cell
  - site
  - circle
  - 4g
  - lte
  - 5g
  - nr
  - network kpi
  - radio kpi
  - coverage
  - throughput
  - utilization
  - latency
  - outage
  - network complaint
  - rca
  - root cause

purpose: >
  The Network database contains radio access network (RAN) and network
  infrastructure data used to monitor, measure, and troubleshoot network
  performance. It is the primary database for questions about cells,
  sites, radio technologies, telecom circles, network KPIs, coverage,
  traffic, capacity, utilization, outages, and network performance
  across 4G/LTE and 5G/NR.

business_scope:
  - cell and site performance
  - radio network performance
  - 4G/LTE performance
  - 5G/NR performance
  - circle-level network performance
  - network traffic and data volume
  - user throughput
  - network capacity and congestion
  - radio resource utilization
  - spectrum and bandwidth utilization
  - network accessibility
  - network retainability
  - network availability
  - mobility and handover performance
  - coverage and radio signal quality
  - packet loss and BLER
  - latency
  - VoLTE network performance
  - network outages
  - network-related complaints
  - network fault analysis
  - root cause analysis
  - network optimization
  - vendor performance
  - frequency and bandwidth analysis

primary_business_entities:
  - cell
  - site
  - circle
  - radio network
  - network KPI
  - coverage
  - outage
  - network complaint
  - root cause analysis
  - network vendor
  - technology
  - frequency
  - bandwidth

main_datasets:
  - cell KPI 4G
  - cell KPI 5G
  - circle KPI 4G
  - circle KPI 5G
  - coverage
  - outage
  - complaint
  - root cause analysis

network_kpi_concepts:
  - DL user throughput
  - UL user throughput
  - download speed
  - upload speed
  - data volume
  - DL data volume
  - UL data volume
  - traffic
  - user load
  - RSRP
  - RSRQ
  - SINR
  - RSSI
  - CQI
  - radio resource utilization
  - DL resource utilization
  - UL resource utilization
  - RB utilization
  - spectrum utilization
  - capacity
  - congestion
  - latency
  - packet loss
  - BLER
  - accessibility
  - retainability
  - availability
  - call drop
  - drop rate
  - handover success
  - mobility
  - VoLTE performance

network_events:
  - cell outage
  - site outage
  - network outage
  - network fault
  - network alarm
  - degraded network performance
  - poor coverage
  - poor signal quality
  - high latency
  - high packet loss
  - low throughput
  - high utilization
  - congestion
  - call drops
  - handover failures
  - network-related complaints
  - root cause
  - network optimization

common_query_concepts:
  - network
  - cell
  - cells
  - site
  - sites
  - tower
  - sector
  - circle
  - coverage
  - radio
  - RAN
  - 4G
  - LTE
  - 5G
  - NR
  - VoLTE
  - KPI
  - performance
  - throughput
  - download speed
  - upload speed
  - data volume
  - traffic
  - utilization
  - capacity
  - congestion
  - accessibility
  - retainability
  - availability
  - latency
  - packet loss
  - BLER
  - RSRP
  - RSRQ
  - SINR
  - RSSI
  - CQI
  - PRACH
  - PUCCH
  - PUSCH
  - outage
  - alarm
  - fault
  - call drop
  - drop rate
  - handover
  - mobility
  - RCA
  - root cause
  - optimization
  - vendor
  - frequency
  - bandwidth

database_boundary: >
  The Network database is focused on network infrastructure, radio
  measurements, network performance, and network events. It should be
  preferred when a query concerns cells, sites, radio networks, 4G or 5G
  performance, throughput, latency, utilization, coverage, signal quality,
  outages, network faults, network-related complaints, or root cause
  analysis. It should not be selected merely because a query contains
  generic terms such as customer, service, complaint, issue, or data
  unless those concepts are connected to network performance or network
  events.

primary_dimensions:
  - date
  - circle name
  - site name
  - cell name
  - technology
  - frequency
  - bandwidth
  - vendor
  - city
  - pincode

database_identity: >
  Network means radio network, cells, sites, 4G/5G, network KPIs,
  coverage, outages, network performance, network faults, and network
  root cause analysis.
  