---
title: Customer Database
type: PostgreSQL database
description: Customer analytics database containing subscriber profiles, customer experience, churn, and customer behavior information.
tags:

* customer
* cem
* subscriber
* churn
* customer experience
* telecom


---

# Customer Database

## Purpose

The Customer database contains subscriber-centric information used for customer analytics, customer experience management (CEM), churn analysis, customer segmentation, and behavioral analysis. The primary entity is the customer (user), with data describing customer profiles, network experience, service usage, and churn indicators.

## Business Scope

This database supports analysis related to:

* Customer profiles and demographics
* Customer experience (CEM)
* Subscriber behavior and usage
* Customer segmentation
* Customer value and revenue (ARPU)
* Recharge behavior
* Device and handset information
* Customer mobility and travel patterns
* OTT and application usage
* Premium service adoption
* Customer satisfaction
* Customer network experience
* Churn prediction and churn drivers
* Root cause analysis for customer issues

## Primary Business Entities

* Customer
* Subscriber
* User
* Customer Profile
* Customer Experience
* Customer Journey
* Customer Network Experience
* Churn
* Revenue
* Recharge
* Device
* Service Usage

## Main Datasets

* Customer Profile
* Customer Network Experience
* Customer Churn

## Typical Questions

This database can answer questions such as:

* Which customers are likely to churn?
* Why are customers churning?
* Which customers have poor network experience?
* Which premium customers are experiencing issues?
* What is the ARPU of different customer segments?
* Which users have poor voice or data experience?
* Which subscribers use OTT services?
* Which customers upgraded their devices?
* Which customers frequently recharge?
* Which users experience high latency or packet loss?
* Which customers belong to a specific city or telecom circle?
* Which users have poor coverage or frequent call drops?
* Which customer segments generate the highest revenue?
* How does customer behavior vary across regions or categories?

## Common Query Concepts

This database is relevant when a query refers to:

* customer
* subscriber
* user
* consumer
* account
* profile
* CEM
* customer experience
* churn
* churn prediction
* churn probability
* churn reason
* customer satisfaction
* network experience
* voice experience
* data experience
* gaming
* video streaming
* buffering
* packet loss
* latency
* recharge
* recharge frequency
* revenue
* ARPU
* device
* handset
* OTT
* premium service
* demographic
* customer category
* age
* gender
* travel
* roaming
* usage pattern

## Primary Keys

The database is primarily organized around:

* User ID
* Date
* Cell Name
* Circle Name

## Relationships

Customer records can be correlated with network data through shared identifiers such as:

* Cell Name
* Circle Name
* Date

This enables customer experience analysis together with network KPIs and infrastructure performance stored in the Network database.

## Not Intended For

This database is not intended for:

* Cell-level network KPI analysis
* Site performance analysis
* Radio performance metrics
* Coverage engineering
* Network optimization
* Alarm monitoring
* Transport or backhaul analysis
* RF engineering metrics

Those use cases belong to the **Network Database**.
