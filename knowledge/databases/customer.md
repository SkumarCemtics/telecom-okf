---
title: Customer Database
type: PostgreSQL database
description: Customer and subscriber analytics database containing customer profiles, subscriber behavior, revenue, recharge, device information, customer experience, churn, and customer-centric service usage. This database focuses on the customer or subscriber as the primary entity, not network infrastructure or radio network performance.
tags:
  - customer
  - subscriber
  - user
  - consumer
  - customer profile
  - customer experience
  - cem
  - churn
  - churn prediction
  - customer behavior
  - customer segmentation
  - revenue
  - arpu
  - recharge
  - device
  - handset
  - ott
  - service usage
  - customer satisfaction
---

# Customer Database

## Purpose

The Customer database contains **customer-centric and subscriber-centric information** used for customer analytics, Customer Experience Management (CEM), churn analysis, customer segmentation, revenue analysis, behavioral analysis, and service-usage analysis.

The primary business entity is the **customer, subscriber, or user**. Data describes who the customer is, how the customer behaves, what services the customer uses, customer value, device information, customer experience, and churn-related indicators.

This database focuses on the **customer perspective of telecom services**, rather than the underlying network infrastructure.

## Business Scope

This database supports analysis related to:

- Customer profiles and demographics
- Subscriber information
- Customer experience and CEM
- Customer behavior and usage
- Customer segmentation
- Customer value and revenue
- ARPU
- Recharge behavior
- Recharge frequency
- Device and handset information
- Service and application usage
- OTT usage
- Premium service adoption
- Customer satisfaction
- Customer journey
- Customer mobility and roaming behavior
- Customer network experience
- Voice and data experience from the customer perspective
- Churn prediction
- Churn probability
- Churn drivers and churn reasons
- Customer issue analysis
- Customer-centric root cause analysis

## Primary Business Entities

- Customer
- Subscriber
- User
- Consumer
- Customer Profile
- Customer Experience
- Customer Journey
- Customer Network Experience
- Customer Segment
- Churn
- Revenue
- Recharge
- Device
- Handset
- Service Usage
- Application Usage

## Main Datasets

- Customer Profile
- Customer Experience
- Customer Network Experience
- Customer Churn
- Customer Usage
- Customer Revenue
- Customer Recharge
- Customer Device

## Typical Questions

This database can answer questions such as:

- Which customers are likely to churn?
- Why are customers churning?
- Which customer segments have the highest churn?
- Which customers have poor customer experience?
- Which premium customers are experiencing service issues?
- What is the ARPU of different customer segments?
- Which customers generate the highest revenue?
- Which users have poor voice or data experience?
- Which subscribers use OTT services?
- Which customers frequently recharge?
- Which customers have upgraded their devices?
- Which customers use specific applications or services?
- Which users experience high latency or packet loss from a customer-experience perspective?
- Which customers belong to a specific city or telecom circle?
- Which customers experience poor coverage or frequent call drops?
- How does customer behavior vary across regions?
- How does churn vary by customer category?
- Which customer segments have the highest revenue?
- What are the major drivers of customer churn?
- Which customers have low or declining usage?
- Which customer groups are high-value or premium?

## Common Query Concepts

This database is relevant when a query refers to:

- customer
- customers
- subscriber
- subscribers
- user
- users
- consumer
- account
- customer profile
- subscriber profile
- customer experience
- CEM
- customer journey
- customer satisfaction
- customer behavior
- customer segment
- segmentation
- churn
- churn prediction
- churn probability
- churn reason
- churn driver
- customer value
- revenue
- ARPU
- recharge
- recharge frequency
- device
- handset
- smartphone
- OTT
- application usage
- service usage
- premium service
- demographic
- customer category
- age
- gender
- roaming
- travel
- mobility
- usage pattern
- voice experience
- data experience
- customer network experience
- buffering
- video streaming
- gaming
- packet loss
- latency

## Customer-Specific Interpretation

Strong indicators for selecting the Customer database include:

- customer
- subscriber
- user
- consumer
- account
- profile
- demographics
- churn
- churn prediction
- churn probability
- churn reason
- customer segment
- customer satisfaction
- ARPU
- revenue
- recharge
- device
- handset
- OTT
- application usage
- customer behavior
- customer experience
- customer journey

Terms such as **latency, packet loss, voice experience, data experience, buffering, or coverage** should be interpreted as Customer-related when the query is asking about the **customer's experience or behavior**.

Terms such as **cell, site, radio KPI, RSRP, RSRQ, SINR, CQI, utilization, throughput, network outage, network fault, or network infrastructure performance** are primarily Network database concepts unless the query explicitly asks for their impact on customers.

## Database Boundary

**Customer = customers + subscribers + users + profiles + behavior + experience + churn + revenue + recharge + devices + service usage.**

Prefer this database when the query is primarily about:

- customers
- subscribers
- users
- customer profiles
- customer behavior
- customer experience
- churn
- revenue
- ARPU
- recharge
- devices
- OTT
- service usage
- customer satisfaction
- customer segmentation

Do **not** select this database merely because a query contains generic terms such as:

- latency
- packet loss
- coverage
- throughput
- utilization
- outage
- network
- performance

These terms should favor the **Network database** when they refer to network infrastructure, cells, sites, radio KPIs, or network performance.

## Database Identity

**Customer = customers + subscribers + users + profiles + customer experience + behavior + churn + revenue + recharge + devices + service usage.**

The Customer database represents the **customer-side view of telecom services**, while the Network database represents the **network infrastructure and network-performance view**.

## Primary Keys

The database is primarily organized around:

- User ID
- Customer ID
- Subscriber ID
- Date
- Customer Category
- Circle Name