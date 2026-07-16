---
description: Customer profile dataset containing demographic, behavioral, device, mobility, subscription, and customer value attributes used for segmentation, personalization, churn analysis, and customer experience analytics.
resource: cem_profile
tags:
- customer
- profile
- segmentation
- demographics
- customer-value
title: cem_profile
type: PostgreSQL Table
---

## Overview

Contains customer demographic, behavioral, usage, mobility, device, and account characteristics used to understand customer segments, value, preferences, and engagement patterns.

Each record represents a unique customer profile.

Primary use cases:

- Customer segmentation
- Customer value analysis
- Churn analysis
- Personalized recommendations
- Customer journey analysis
- Marketing campaign targeting
- Device and technology adoption analysis
- Customer experience analytics

## Grain

One record per:

- user_id

## Key Dimensions

- user_id
- customer_category
- circle_name
- gender
- device_brand
- device_model

## Profile Categories

### Customer Segmentation

- customer_category
- voice_data_user
- voice_tag
- data_tag

### Demographics

- customer_age
- gender

### Revenue & Value

- arpu
- locality_value
- customer_category

### Recharge Behaviour

- recharge_mode
- recharge_type
- bonus_recency

### Device Profile

- device_brand
- device_model
- sim_support
- handset_upgrade_or_dual_sim
- aod

### Mobility & Lifestyle

- num_of_domestictrips
- num_of_internationaltrips
- work_pattern
- home_type

### Digital Services

- ott_subscription
- voip_usage_tag
- credit_card

### Interests & Behaviour

- hobbies_interest
- facebook_video_vc_usage_delta
- outgoing_calls_delta

### Customer Lifecycle

- aon
- aod

## Related Metrics

- ../../references/metrics/arpu.md
- ../../references/metrics/aon.md
- ../../references/metrics/aod.md
- ../../references/metrics/customer_value.md
- ../../references/metrics/customer_engagement.md

## Related Joins

- ../../references/joins/profile_churn.md
- ../../references/joins/profile_network_experience.md
- ../../references/joins/profile_interest.md
- ../../references/joins/profile_recommendation.md
- ../../references/joins/customer_segmentation.md

## Related Tables

- cem_churn.md
- cem_network_exp.md
- cem_interest.md
- cem_product_recommendation.md

## Common Join Keys

Primary:

- user_id

Secondary:

- customer_category
- circle_name

## Common Analysis Questions

- Which customer segments generate the highest revenue?
- Which customers are most likely to churn?
- How do usage patterns differ across customer categories?
- Which devices are most commonly used by premium customers?
- How does mobility behavior impact customer value?
- Which customer profiles are most suitable for premium offers?
- How do OTT subscribers differ from non-subscribers?
- What factors influence customer engagement and retention?

## Customer Categories

Typical categories include:

- Platinum
- Gold
- Silver
- Other

Higher tiers generally represent higher-value customers.

## Schema

| Name | Type | Description |
|--------|--------|--------|
| user_id | text | Unique customer identifier |
| customer_category | text | Customer value segment such as Platinum, Gold, Silver, or Other |
| voice_data_user | text | Customer service usage profile such as Voice, Data, or Data & Voice |
| sim_support | text | Device or SIM capability classification |
| recharge_mode | text | Recharge channel such as Digital or Non Digital |
| recharge_type | text | Billing type such as Prepaid or Postpaid |
| circle_name | text | Customer's primary telecom circle |
| customer_age | double precision | Customer age |
| gender | text | Customer gender |
| voice_tag | text | Voice usage classification such as Low, Medium, or High |
| data_tag | text | Data usage classification such as Low, Medium, or High |
| handset_upgrade_or_dual_sim | text | Device upgrade or dual SIM behavior indicator |
| device_brand | text | Device manufacturer |
| num_of_domestictrips | double precision | Number of domestic trips taken by the customer |
| num_of_internationaltrips | double precision | Number of international trips taken by the customer |
| work_pattern | text | Customer movement pattern such as Mobile, Routine, or HomeBound |
| home_type | text | Customer home classification |
| arpu | double precision | Average Revenue Per User |
| hobbies_interest | text | Primary interest or activity category |
| device_model | text | Device model used by the customer |
| bonus_recency | text | Indicates whether the customer recently received a bonus or promotion |
| ott_subscription | text | Indicates active OTT service subscriptions |
| credit_card | text | Indicates credit card usage for payments or recharges |
| voip_usage_tag | text | OTT voice calling usage classification |
| locality_value | text | Spending or value classification of the customer's locality |
| facebook_video_vc_usage_delta | text | Trend in social media, video, and video conferencing usage |
| outgoing_calls_delta | text | Trend in outgoing call activity |
| aon | double precision | Age on Network representing customer tenure |
| aod | double precision | Age of Device representing duration of current device usage |