---
description: Customer product recommendation dataset containing upsell, retention, and personalized offer recommendations based on customer profile, segment, and service characteristics.
resource: cem_product_recommendation
tags:
- customer
- recommendations
- upsell
- retention
- personalization
title: cem_product_recommendation
type: PostgreSQL Table
---

## Overview

Contains customer-specific product recommendations, retention strategies, and promotional offers generated based on customer characteristics, service usage, and value segments.

Each record represents recommended products and offers for a specific customer.

Primary use cases:

- Product recommendation
- Upsell targeting
- Retention campaign planning
- Customer value management
- Offer personalization
- Marketing analytics
- Revenue growth initiatives
- Customer engagement optimization

## Grain

One record per:

- user_id

## Key Dimensions

- user_id
- customer_category
- sim_support
- circle_name

## Recommendation Categories

### Upsell Recommendations

- upsell_ret_cat
- product_reco

### Retention Recommendations

- upsell_ret_cat
- offer_details

### Customer Segmentation

- customer_category
- sim_support
- circle_name

### Offer Management

- product_reco
- offer_details

## Related Metrics

- ../../references/metrics/customer_value.md
- ../../references/metrics/arpu.md
- ../../references/metrics/churn_probability.md
- ../../references/metrics/customer_engagement.md

## Related Joins

- ../../references/joins/profile_recommendation.md
- ../../references/joins/churn_recommendation.md
- ../../references/joins/recommendation_interest.md
- ../../references/joins/customer_retention.md

## Related Tables

- cem_profile.md
- cem_churn.md
- cem_interest.md
- cem_network_exp.md

## Common Join Keys

Primary:

- user_id

Secondary:

- customer_category
- circle_name

## Common Analysis Questions

- Which products are most frequently recommended to high-value customers?
- What retention offers are assigned to customers with high churn risk?
- Which customer segments receive upsell recommendations?
- How do recommendations vary across circles?
- Are recommended offers aligned with customer interests?
- Which offers are targeted toward premium customers?
- What products are commonly recommended to heavy data users?

## Recommendation Types

Typical recommendation categories include:

- Retention Offers
- Plan Upgrades
- Data Pack Recommendations
- Voice Bundle Recommendations
- Premium Service Offers
- Device Upgrade Opportunities
- Loyalty Rewards
- Personalized Promotions

## Schema

| Name | Type | Description |
|--------|--------|--------|
| user_id | text | Unique customer identifier |
| customer_category | text | Customer value segment such as Platinum, Gold, Silver, or Other |
| sim_support | text | Device or SIM capability classification |
| circle_name | text | Customer's primary telecom circle |
| upsell_ret_cat | text | Recommendation category used for upsell or retention actions |
| product_reco | text | Recommended product, tariff, service, or package |
| offer_details | text | Details of the recommended offer, promotion, discount, or retention benefit |