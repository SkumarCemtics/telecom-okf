---
description: Customer interest and digital behavior dataset containing application preferences, content interests, and inferred customer interest segments used for personalization and recommendation analytics.
resource: cem_interest
tags:
- customer
- interests
- personalization
- recommendations
- digital-behavior
title: cem_interest
type: PostgreSQL Table
---

## Overview

Contains customer application preferences, usage interests, and derived behavioral segments.

Each record represents interests associated with a specific customer.

Primary use cases:

- Customer segmentation
- Interest profiling
- Product recommendation
- Personalized marketing
- Campaign targeting
- Digital engagement analysis
- Lifestyle and affinity analysis

## Grain

One record per:

- user_id
- app_of_interest

## Key Dimensions

- user_id
- circle_name
- sim_support
- app_group
- app_of_interest
- derived_interest

## Interest Categories

### Application Interests

- app_group
- app_of_interest

### Behavioral Interests

- derived_interest

### Customer Attributes

- sim_support
- circle_name

## Related Metrics

- ../../references/metrics/customer_engagement.md
- ../../references/metrics/digital_usage.md

## Related Joins

- ../../references/joins/profile_interest.md
- ../../references/joins/recommendation_interest.md
- ../../references/joins/customer_segmentation.md

## Related Tables

- cem_profile.md
- cem_product_recommendation.md
- cem_churn.md

## Common Join Keys

Primary:

- user_id

Secondary:

- circle_name

## Common Analysis Questions

- What are the most common customer interests?
- Which app categories are most popular by customer segment?
- Which interest groups have the highest engagement?
- What products should be recommended to customers based on interests?
- Do certain interests correlate with churn risk?
- How do customer interests vary by circle?
- Which customers are likely candidates for premium digital services?

## Schema

| Name | Type | Description |
|--------|--------|--------|
| user_id | text | Unique customer identifier |
| sim_support | text | Device or SIM capability classification |
| circle_name | text | Customer's primary telecom circle |
| app_group | text | High-level application category such as social media, streaming, gaming, communication, or productivity |
| app_of_interest | text | Specific application or service showing customer affinity or engagement |
| derived_interest | text | Inferred customer interest category derived from application usage patterns |