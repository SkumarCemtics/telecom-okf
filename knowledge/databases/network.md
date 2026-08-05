---

title: Network Database
type: PostgreSQL database
description: Network analytics database containing radio network KPIs, coverage, outages, complaints, and root cause analysis information.
tags:

- network
- telecom
- 4g
- 5g
- radio
- kpi
- coverage
- outage
- rca

---

# Network Database

## Purpose

The Network database contains network-centric information used for radio network monitoring, performance management, capacity planning, coverage analysis, fault management, and root cause analysis. The primary entities are cells, sites, and telecom circles, with data describing network performance, coverage, service quality, outages, complaints, and operational KPIs across 4G and 5G networks.

## Business Scope

This database supports analysis related to:

- Cell performance monitoring
- Circle-level network performance
- 4G and 5G radio KPIs
- Coverage analysis
- Signal strength and signal quality
- Capacity planning
- Traffic analysis
- User throughput
- Accessibility KPIs
- Retainability KPIs
- Mobility and handover performance
- VoLTE performance
- Packet loss and BLER analysis
- Latency analysis
- Spectrum utilization
- Radio resource utilization
- Network availability
- Vendor performance comparison
- Network outage monitoring
- Customer complaint analysis
- Root cause analysis (RCA)
- Network optimization

## Primary Business Entities

- Cell
- Site
- Circle
- Radio Network
- Coverage
- Network KPI
- Outage
- Complaint
- Root Cause Analysis
- Vendor

## Main Datasets

- Cell KPI 4G
- Cell KPI 5G
- Circle KPI 4G
- Circle KPI 5G
- Coverage
- Complaint
- Outage
- Root Cause Analysis (RCA)

## Typical Questions

This database can answer questions such as:

- Which cells have poor throughput?
- Which circles have the highest traffic?
- Which cells have poor RSRP, RSRQ, SINR, or CQI?
- Which sites have the highest user load?
- Which cells have high packet loss or BLER?
- Which circles have poor accessibility or retainability KPIs?
- Which sites have frequent outages?
- Which vendors have the best or worst network performance?
- Which cells require optimization?
- Which cells have poor VoLTE performance?
- Which areas have poor coverage?
- Which circles have the highest complaints?
- What is the root cause of a network issue?
- Which cells have the highest latency?
- Compare 4G and 5G network performance.
- Which locations have the highest call drop rate?
- Which cells have poor handover success rates?

## Common Query Concepts

This database is relevant when a query refers to:

- network
- cell
- site
- sector
- tower
- circle
- city
- coverage
- radio
- 4G
- LTE
- 5G
- NR
- KPI
- performance
- throughput
- traffic
- data volume
- user throughput
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
- VoLTE
- call drop
- drop rate
- CSSR
- HOSR
- handover
- mobility
- outage
- alarm
- complaint
- RCA
- root cause
- optimization
- vendor
- frequency
- bandwidth

## Primary Keys

The database is primarily organized around:

- Date
- Cell Name
- Site Name
- Circle Name
- Technology

## Relationships

Network datasets are correlated using shared identifiers including:

- Cell Name
- Site Name
- Circle Name
- Date
- Technology

These relationships enable end-to-end analysis across network KPIs, coverage, outages, complaints, and RCA information.

## Not Intended For

This database is not intended for:

- Customer profiling
- Subscriber demographics
- Customer behavior analysis
- Customer experience management (CEM)
- Churn prediction
- Customer segmentation
- Recharge analysis
- ARPU analysis
- Device ownership
- Customer revenue analysis

Those use cases belong to the **Customer Database**.
