---
description: Customer churn and retention dataset containing customer experience indicators, usage behavior, recharge patterns, service quality perception, and churn risk factors.
resource: cem_churn
tags:
- customer
- churn
- retention
- customer-experience
- revenue
title: cem_churn
type: PostgreSQL Table
---

## Overview

Contains customer churn indicators, churn drivers, network experience assessments, revenue trends, recharge behavior, and retention risk signals.

Each record represents a customer's churn-related profile and behavioral indicators.

Primary use cases:

- Churn prediction
- Customer retention analysis
- Customer experience analysis
- Revenue risk assessment
- Customer segmentation
- Network experience impact analysis
- Product upgrade targeting
- Loyalty and retention campaigns

## Grain

One record per:

- user_id

## Key Dimensions

- user_id
- customer_category
- circle_name
- churn_reason

## KPI Categories

### Churn Risk Indicators

- churn_probability_high
- churn_reason
- bill_overdue_days

### Customer Experience

- overall_network_exp
- home_exp
- work_exp
- data_exp
- voice_exp
- lwp_nw_exp

### Revenue & Recharge Behaviour

- recharge_frequency
- recharge_recency_lm
- tot_rev_grow_degrow_tag
- overall_rcr_tag
- home_rcr_tag
- outside_rcr_tag

### Service Usage

- service_availed
- premium_services
- video_conferencing
- total_data_volume_tag

### Network Quality Indicators

- user_throughput
- customer_data_rca
- poor_voice_reason

### Customer Engagement

- plan_upgrade
- voip_grow_degrow_tag

## Related Metrics

- ../../references/metrics/churn_probability.md
- ../../references/metrics/user_throughput.md
- ../../references/metrics/recharge_frequency.md
- ../../references/metrics/bill_overdue_days.md
- ../../references/metrics/arpu.md

## Related Joins

- ../../references/joins/profile_churn.md
- ../../references/joins/churn_network_experience.md
- ../../references/joins/customer_quality_correlation.md

## Related Tables

- cem_profile.md
- cem_network_exp.md
- cell_kpi_5g.md

## Common Join Keys

Primary:

- user_id

Secondary:

- circle_name
- customer_category

## Common Churn Drivers

- Network Issues
- Poor Data Experience
- Poor Voice Experience
- Revenue Decline
- Recharge Inactivity
- Billing Issues
- Limited Service Usage
- Low Customer Engagement

## Common Analysis Questions

- Which customer segments have the highest churn probability?
- What are the primary reasons for customer churn?
- Does poor network experience increase churn risk?
- Are premium customers more likely to churn?
- How does recharge behavior affect churn?
- Which circles have the highest churn concentration?
- Does throughput impact customer retention?
- Which customers should be targeted for retention campaigns?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| user_id | text | Unique customer identifier |
| customer_category | text | Customer value segment such as Platinum, Gold, Silver, or Other |
| service_availed | text | Primary service usage category used by the customer |
| sim_support | text | SIM or device capability classification |
| circle_name | text | Customer's primary telecom circle |
| churn_reason | text | Primary reason associated with customer churn |
| voip_grow_degrow_tag | text | Trend indicator for VoIP usage growth or decline |
| customer_data_rca | text | Root cause category associated with poor data experience |
| poor_voice_reason | text | Root cause category associated with poor voice experience |
| recharge_recency_lm | text | Recent recharge activity indicator |
| overall_network_exp | text | Overall network experience assessment |
| home_exp | text | Customer experience at home location |
| work_exp | text | Customer experience at work location |
| video_conferencing | text | Indicates whether the customer regularly uses video conferencing applications |
| total_data_volume_tag | text | Customer data usage classification such as Very High, High, Medium, or Low |
| user_throughput | double precision | Average throughput experienced by the customer |
| tot_rev_grow_degrow_tag | text | Revenue growth or decline trend indicator |
| overall_rcr_tag | text | Overall recharge consistency rating |
| home_rcr_tag | text | Recharge consistency rating at home location |
| outside_rcr_tag | text | Recharge consistency rating outside home location |
| premium_services | text | Indicates subscription to premium services |
| plan_upgrade | text | Indicates recent plan upgrade activity |
| recharge_frequency | double precision | Number of recharge transactions within a defined period |
| data_exp | text | Overall customer perception of data service quality |
| voice_exp | text | Overall customer perception of voice service quality |
| lwp_nw_exp | text | Network experience indicator used for churn and retention analysis |
| churn_probability_high | text | High churn risk indicator (Yes/No) |
| bill_overdue_days | double precision | Number of days a bill payment remains overdue |