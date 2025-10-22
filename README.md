
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
  
# System Architecture Diagram & Components
This section provides a detailed view of the MobilityCorp system, showing how AI integrates with existing operations to improve vehicle availability, optimize maintenance, and enhance customer experience.

### a) Edge Layer:
* Vehicle telemetry (GPS, battery level, speed, usage).
* NFC unlock/lock logs.
* Customer-submitted photos for vehicle return verification.
* Lightweight edge AI for immediate anomaly detection.
### b) Data Ingestion & Streaming:
* Event streaming platform (Kafka or equivalent) to capture real-time telemetry and events.
* Preprocessing services to validate data and attach metadata.
### c) Storage Layer:
* Hot storage: Time-series DB (ClickHouse/TimescaleDB) for operational queries.
* Cold storage: Object storage (S3/GCS) for historical telemetry and images.
* Feature store (Feast) for ML models (both online and offline features).
* Relational DB (PostgreSQL) for user, vehicle, and booking metadata.
* Optional Graph DB for relationships (vehicle-user-staff).
### d) Machine Learning & AI Services:
* Demand forecasting models.
* RUL/Battery life prediction models.
* Optimization engine for staff routing and vehicle redistribution.
* Vision models for return verification and damage detection.
* Recommendation models for personalized user engagement.
* Fraud detection models for GPS, photo, and unlock anomalies.
### e) API & Applications Layer:
* REST/GraphQL APIs for customer apps, staff apps, and admin dashboards.
* Customer-facing mobile apps (booking, unlock/lock, feedback).
* Staff mobile apps for battery swaps and vehicle redistribution tasks.
* Fleet management dashboards and analytics tools.
### f) Operations & Monitoring:
* Logging and tracing (Prometheus, Grafana, OpenTelemetry, Jaeger).
* Alerting and incident management.
* Model monitoring: drift detection, performance metrics, and retraining triggers.
* RBAC and tenant-based isolation.

## AI Use Cases & Models
This section outlines the key AI-driven components and how they directly address MobilityCorp’s operational and customer challenges.

### Use Case 1: Predictive Demand Forecasting
* Objective: Predict vehicle demand by type and location to ensure availability.
* Inputs: Historical bookings, time-of-day, day-of-week, weather, events, nearby transit disruptions.
* Models: Time-series models (ARIMA, Prophet), Gradient Boosted Trees (LightGBM/CatBoost), Transformer-based models for longer horizons.
* Outputs: Probabilistic forecasts per zone with feature importances and scenario-based predictions.

### Use Case 2: Battery & Charge Prioritization
* Objective: Predict which vehicles need charging or battery swaps and prioritize staff tasks.
* Inputs: SOC, usage patterns, trip length estimates, charging availability, battery health, temperature.
* Models: RUL regression or survival analysis, combined with priority scoring function.
* Outputs: Prioritized task list for staff with urgency scores.

### Use Case 3: Staff Routing & Vehicle Redistribution
* Objective: Optimize routes for staff performing battery swaps and vehicle redistribution.
* Inputs: Forecasts, vehicle states, staff availability, traffic data, bay capacity.
* Models: VRPTW (Vehicle Routing Problem with Time Windows) solver using OR-Tools, hybrid heuristics, and reinforcement learning for long-term optimization.
* Outputs: Optimized staff routes and task assignments.

### Use Case 4: Return Verification & Compliance
* Objective: Verify that vehicles are returned correctly and EVs are charged.
* Inputs: Customer photos, GPS data, bay locations.
* Models: Computer vision models (YOLO/Detectron for object detection, Mask R-CNN for damage detection, classification for charger connection).
* Outputs: Verification result with confidence score, detected issues, and human review queue.

### Use Case 5: Personalized User Engagement
* Objective: Encourage regular usage and subscription adoption.
* Inputs: User trip history, saved locations, session context, travel patterns.
* Models: Session-based recommendation models (SASRec/Transformer), uplift models for personalized incentives.
* Outputs: Personalized suggestions, push notifications, targeted promotions.

### Use Case 6: Fraud Detection & Security
* Objective: Detect suspicious activities such as GPS spoofing, false photos, or account misuse.
* Inputs: Unlock logs, GPS consistency, photo forensics, device fingerprints.
* Models: Rule-based checks + anomaly detection (Isolation Forest, LSTM autoencoder), supervised classifiers for known fraud patterns.
* Outputs: Risk scores, automated mitigation actions, human review when needed.

## Architecture Decision Records (ADRs)

### 1. ADR-001: Feature Store Adoption
* **Decision**: Adopt Feast as the centralized feature store.
* **Rationale**: Provides a consistent source for online and offline features, reducing training-serving skew for ML models.
* **Trade-offs**: Adds operational overhead, but ensures reproducibility and real-time access to features for forecasting, battery prediction, and recommendation models.

### 2. ADR-002: Model Serving Architecture
* **Decision**: Use Seldon Core on Kubernetes for serving models with canary and A/B deployment support.
* **Rationale**: Vendor-neutral, supports multiple model frameworks, and integrates with service mesh for security and observability.
* **Trade-offs**: Higher infra management effort compared to fully managed cloud services, but provides flexibility and portability.

### 3. ADR-003: Vision Model Deployment (Edge vs Cloud)
* **Decision**: Implement a two-tier approach: lightweight edge model for immediate feedback and cloud models for high-accuracy verification.
* **Rationale**: Immediate UX feedback while leveraging cloud GPUs for complex inference.
* **Trade-offs**: Requires version synchronization and model monitoring across layers.

### 4. ADR-004: Optimization Solver Choice
* **Decision**: Use OR-Tools CP-SAT combined with heuristic/metaheuristic algorithms for routing and redistribution.
* **Rationale**: CP-SAT handles strict constraints efficiently; heuristics provide scalability for real-time updates.
* **Trade-offs**: Near-optimal solutions may occasionally be suboptimal, but real-time constraints are met.

### 5. ADR-005: Data Retention & Privacy
* **Decision**: Retain raw images for 30 days, telemetry for 12 months hot storage, then archive. Provide tenant-specific retention policies.
* **Rationale**: Balances dispute resolution, operational analysis, and privacy requirements.
* **Trade-offs**: Shorter retention may limit dispute resolution; longer retention increases storage costs.

### 6. ADR-006: AI Validation & Human-in-the-Loop
* **Decision**: All high-impact decisions (billing fines, return verification, fraud alerts) include human review for low-confidence cases.
* **Rationale**: Ensures fairness, reduces false positives, and builds trust in AI decisions.
* **Trade-offs**: Slightly slower response for edge cases but improves accuracy and customer satisfaction.

### 7. ADR-007: Model Retraining & Drift Detection
* **Decision**: Implement continuous monitoring for input distribution and model performance. Trigger retraining or rollback when drift is detected.
* **Rationale**: Maintains accuracy over time and ensures AI models adapt to changing user behavior and seasonal trends.
* **Trade-offs**: Additional monitoring and compute costs, but reduces risk of degraded performance impacting operations and customer experience.

## Validation, Governance & Monitoring
To ensure AI-driven operations are accurate, fair, and reliable, MobilityCorp implements validation processes, governance standards, and continuous monitoring across all models and operational systems.
Model Validation & Performance Monitoring

### 1. Forecasting Models: Evaluate using CRPS, MAE, and coverage of prediction intervals.
* RUL/Battery Models: Use RMSE, calibration metrics, and time-to-failure precision/recall.
* Vision Models: Measure precision/recall for return verification, FPR for false fines, and human review rates.
* Recommender Models: Monitor uplift, retention lift, conversion rates, and long-term behavior changes.
Processes:
* Shadow deployments of new models to gather performance data without affecting live decisions.
* Canary rollouts to a small user group before full deployment.
* Human-in-the-loop for low-confidence or high-impact cases.

### 2. Governance & Responsible AI
* Fairness: Regular audits to ensure recommendations and incentives do not introduce bias.
* Privacy: Explicit user consent for targeted notifications and calendar integrations. Data encryption at rest and in transit.
* Transparency: Explainability using SHAP values for predictions and visual overlays for vision-based verifications.
* Data Quality: Automated checks on incoming telemetry and images to ensure consistency and completeness.

### 3. Operational Monitoring
* Telemetry & Logging: All model inferences and API calls are logged for traceability.
* Alerting: Prometheus/Grafana alerting on anomalies, system failures, or model performance degradation.
* Drift Detection: Monitor input distributions and outputs to detect concept drift and trigger retraining.
* Dashboard & Analytics: Centralized dashboards for staff and management to view fleet status, AI recommendations, and alerts.

### 4. Risk Mitigation
* Fallback Mechanisms: Rule-based defaults if AI services fail.
* Human Oversight: Critical decisions (billing, return verification, fraud detection) reviewed by staff.
* Continuous Improvement: Feedback loops from staff and customer interactions feed back into training data.
* Security: Monitoring for unusual access patterns, GPS spoofing, and potential fraud attempts.

This framework ensures AI systems remain accurate, trustworthy, and aligned with business objectives while providing a safe and fair experience for customers and staff.

## Roadmap
Approach: Phased Rollout Strategy
This roadmap outlines the phased implementation plan to deploy MobilityCorp's AI-driven system, from initial MVP to full-scale production across multiple locations.

### 1. MVP Scope

Objective: Build a functional core system with AI support for key operations.
### Components:
* Telemetry ingestion pipeline & storage setup (hot and cold data).
* Booking and payment integration with per-minute billing.
* Basic vehicle return verification using edge AI for immediate feedback.
* Demand forecasting pilot for one city zone.
* Staff routing heuristics for battery swaps and vehicle redistribution.
* Basic recommendation engine for simple personalized notifications.
### KPIs:
* Availability of vehicles in pilot zone.
* Staff operational efficiency in battery swaps.
* Accuracy of return verification.
* Initial customer engagement and feedback.

### 2. Phase 2
Objective: Expand AI capabilities and improve operational efficiency.
### Components:
* Full feature store integration (online and offline features).
* RUL and battery prediction models for all vehicle types.
* Advanced optimization engine for routing and redistribution.
* Cloud-based vision models for damage detection and EV plug-in verification.
* Fraud detection pipeline and alerting systems.
* Enhanced personalized recommender with uplift modeling for incentives.
### KPIs:
* Reduced downtime and stranded vehicles.
* Improved staff route efficiency and reduced operational cost.
* Increase in repeat customer usage and subscriptions.
* Reduction in false fines and disputes.

### 3. Phase 3
Objective: Scale to multiple cities and enhance system robustness.
### Components:
* Multi-city deployment of AI models and infrastructure.
* Real-time re-optimization for dynamic fleet management.
* Continuous monitoring, drift detection, and automated retraining.
* Integration with external data sources (traffic, events, weather).
* Enhanced analytics dashboards for staff and management.
### KPIs:
* Fleet utilization rates across locations.
* Operational cost savings and staff efficiency improvements.
* Customer retention and growth metrics.
* Accuracy and reliability of AI predictions across locations.

### Risk Management
* Fallbacks: Rule-based systems if AI models fail.
* Human-in-the-loop: Critical tasks reviewed manually when needed.
* Monitoring: Continuous system health and model performance checks.
* Feedback loops: Customer and staff feedback incorporated into model retraining.

This phased roadmap ensures a controlled, scalable, and efficient rollout of MobilityCorp’s AI-driven solution, starting with a focused MVP and progressively expanding to full production capabilities.
