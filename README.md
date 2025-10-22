
# LEXI Team - Tata Elxsi Team | O'Reilly Architectural Katas Q4 2025: AI-Enabled Architecture

A structured approach to the Mobility Corp Problem **O'Reilly Architectural Katas Q4 2025: AI-Enabled Architecture**.

## Table of Contents

## Team
 ![Team](/assets/team.png "team")
- [**Jesu Maria Antony sebastian**](https://www.linkedin.com/in/jesumariaantony/) , Senior Solution Architect
- [**Karthick G**](https://www.linkedin.com/in/karthick-gurumoorthy-11775a199/) , Senior AI Engineer
- [**Bhuvaneswari**](https://www.linkedin.com/in/bhuvaneshwari-s-26b2a71a2/) , Senior AI Engineer
- [**Sariga**](https://www.linkedin.com/in/sariga-k-473b63227/) , Senior AI Engineer

## Glossary
[Glossary](business-requirements/glossary.md) to understand more about certain terms.

# Problem definition

## Problem Statement

MobilityCorp needs an AI-driven architecture that dynamically aligns fleet availability, charging logistics, and user demand forecasts to improve service reliability, customer satisfaction, and operational efficiency while ensuring scalability across cities.

## Challenges with MobilityCorp

**Customer Experience**:
1. Customers often find the vehicles they need aren’t available where or when they want them.
2. Inconsistent availability discourages regular use.

**Operations**:
1. It’s hard to predict when and where vehicles will be needed.
2. Prioritizing battery swaps and rebalancing the fleet is challenging.
   
**Usage & Retention**:
1. Most customers use the service sporadically rather than for regular commutes.
   
**Energy Management**:
1. Vehicles sometimes run low on charge before staff can reach them.


1. Vehicles aren’t where customers want them (availability / placement)
2. Dead / low-battery vehicles
3. Low repeat usage / weak conversion -

## Current Operations

1. **Cars and Vans**: Can be booked up to 7 days in advance for a set duration.
2. **Bikes and Scooters**: Can be booked 30 minutes ahead and used for up to 12 hours.
3. **Payments**: Charged per minute, with fines for late returns or parking in the wrong spot.
4. **Return Process**: Vehicles must be returned to designated spots. Customers provide photo proof and optional feedback.
5. **Maintenance**: Staff replace batteries for scooters and bikes and redistribute vehicles to ensure availability.

## Opportunities

By using smart data insights and predictive tools, MobilityCorp can:
* Forecast demand to make sure vehicles are in the right place at the right time.
* Optimize maintenance and charging schedules to reduce downtime.
* Summarize and learn from customer feedback to improve service.
* Encourage regular usage by understanding travel habits and offering helpful suggestions.

# AI Enhanced Solution Overview
To address MobilityCorp's challenges, we propose an AI-driven approach that makes fleet management smarter, more predictive, and customer-friendly. The goal is to ensure vehicles are where customers need them, reduce operational inefficiencies, and encourage regular usage.
## Key AI Capabilities
### a) Predictive Demand Forecasting:
* Anticipates where and when different vehicles will be needed.
* Helps staff pre-position vehicles to meet expected demand.
### b) Battery and Charging Optimization:
* Predicts which vehicles need charging or battery swaps.
* Prioritizes staff visits for maximum efficiency.
### c) Intelligent Vehicle Repositioning:
* Generates optimized routes for staff to redistribute vehicles.
Uses real-time data on vehicle locations, battery levels, and predicted demand.
### d) Return Verification & Compliance:
* Uses photos and GPS data to confirm vehicles are returned correctly.
* Checks that EVs are properly plugged in and identifies damages.
### e) Personalized User Engagement:
* Recommends routes, subscriptions, and promotions based on user habits.
* Encourages repeat usage and regular commuting patterns.
### f) Fraud & Safety Monitoring:
* Detects anomalies in GPS data, unlock attempts, or suspicious behavior.
* Ensures the system remains secure and trustworthy.

## Architecture Overview
The AI-enabled solution integrates with MobilityCorp’s existing systems and includes:
* **Edge Layer** : Vehicle sensors and app inputs (GPS, telemetry, NFC actions, photos).
* **Streaming and Storage**: Real-time data pipelines for telemetry, event logs, and images; hot storage for live queries and cold storage for historical data.
* **Machine Learning Platform**: Models for forecasting, RUL/battery predictions, routing optimization, vision-based verification, and recommendation systems.
* **Operations & Staff Tools**: Mobile apps for maintenance staff with optimized tasks, fleet dashboards for monitoring, and alerts.
* **Customer Apps**: Updated mobile apps offering personalized suggestions, instant verification of returns, and notifications.

## Expected Outcomes
* Vehicles are available where and when needed.
* Reduced downtime due to proactive battery management.
* Smarter routing for staff reduces operational costs.
* Improved customer satisfaction and higher regular usage.
* Secure, reliable, and scalable system ready for expansion to multiple locations.
  
## How is AI Enabled in our Architecture
Enter the content here
## Architecture characteristics
Enter the content here

## Roadmap
Approach: Phased Rollout Strategy
- **MVP:** Run AI and human grading in parallel to compare accuracy, refine AI models, and track grading consistency.
- **Growth:** AI handles primary grading, with human validation for low-confidence cases and structured feedback improvements.
- **Matured:** Achieve high-accuracy AI grading, with minimal human involvement focused on oversight.
