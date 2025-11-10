
# O'Reilly Architectural Katas Q4 2025: AI-Enabled Architecture
**Team LEXI** - from **Tata Elxsi** - Home to Billion Possibilities

![Team](/assets/lexi.png "team")

A structured approach to the Mobility Corp Problem **O'Reilly Architectural Katas Q4 2025: AI-Enabled Architecture**.

## Table of Contents

- Overview & Problem Statement
- AI-Enhanced Solution Overview
- System Architecture View
- AI Use Cases & Models
- Agentic AI Implementation with Multi-Agent System
- Architecture Decision Records (ADRs)
- Validation, Governance & Monitoring
- Implementation Roadmap
  
## Team
  ![Team](/assets/lexiOriellyTeam.png "team")
  
- [**Jesu Maria Antony sebastian**](https://www.linkedin.com/in/jesumariaantony/) , Senior Solution Architect
- [**Karthick G**](https://www.linkedin.com/in/karthick-gurumoorthy-11775a199/) , Senior AI Engineer
- [**Bhuvaneswari**](https://www.linkedin.com/in/bhuvaneshwari-s-26b2a71a2/) , Senior AI Engineer
- [**Sariga**](https://www.linkedin.com/in/sariga-k-473b63227/) , Senior AI Engineer

# Overview & Problem Statement

## Problem Statement

MobilityCorp needs an AI-driven architecture that dynamically aligns fleet availability, charging logistics, and user demand forecasts to improve service reliability, customer satisfaction, and operational efficiency while ensuring scalability across cities.

## Challenges with MobilityCorp

**Customer Experience**:
1. Customers often find the vehicles they need aren’t available where or when they want them.
2. Inconsistent availability discourages regular use.
3. Low Battery (SoC) vehicles and sometimes dead battery

**Operations**:
1. It’s hard to predict when and where vehicles will be needed.
2. Prioritizing battery swaps and rebalancing the fleet is challenging.
   
**Usage & Retention**:
1. Most customers use the service sporadically rather than for regular commutes.
2. Low Customer repeat / Weak conversion
   
**Energy Management**:
1. Vehicles sometimes run low on charge before staff can reach them.

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

![Architecture Overview](/assets/Architecture_Overview.png "Architecture Overview")

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
  
# System Architecture View
This section provides a detailed view of the MobilityCorp system, showing how AI integrates with existing operations to improve vehicle availability, optimize maintenance, and enhance customer experience.

### a) Edge Layer:
**Components**: IoT-enabled vehicles with GPS, accelerometers, and CAN bus data integration.

**Functions**:
* Capture live telemetry (speed, charge level, usage duration).
* Edge AI modules for anomaly detection (sudden stops, battery drain, misuse).
* NFC-based authentication for vehicle lock/unlock.
* Local caching for offline data resilience.
  
**Tools/Tech**: TensorRT models, MQTT communication, and mobile SDK integration.

### b) Data Ingestion & Streaming [Bridge]:
**Components**: Kafka or Pulsar clusters with stream processors.

**Functions**:
* Real-time ingestion of telemetry, booking, and customer activity.
* Data validation, enrichment, and schema evolution.
* Stream partitioning by city and vehicle type.

**Tools/Tech**: Kafka Connect, Debezium, Flink/Spark Streaming.

### c) Storage Layer:
* **Hot storage**: Time-series DB (ClickHouse/TimescaleDB) for operational queries.
* **Cold storage**: Object storage (S3/GCS) for historical telemetry and images.
* **Feature store** (Feast) for ML models (both online and offline features).
* **Transactional DB** (PostgreSQL) for user, vehicle, and booking metadata.
* **Optional Graph DB** for relationships (vehicle-user-staff).
  
### d) Machine Learning & AI Services:
**Components**: ML models, inference services, and retraining pipelines.

**Core AI Services**:

* **Demand Forecasting**: Predict vehicle demand per zone per hour.
* **Battery/RUL Prediction**: Estimate remaining charge and plan proactive swaps.
* **Optimization Engine**: Route planning for staff and vehicle redistribution.
* **Vision AI**: Damage and return verification using photo submissions.
* **Recommender Engine**: Personalized trip and promotion suggestions.

* **Fraud Detection**: Identify anomalies in GPS trails, booking patterns, or unlock behavior.

**Tools/Tech**: Kubeflow, MLflow, Seldon Core, TensorFlow, PyTorch, ONNX Runtime.

### e) API & Applications Layer:
* REST/GraphQL APIs for customer apps, staff apps, and admin dashboards.
* Customer-facing mobile apps (booking, unlock/lock, feedback).
* Staff mobile apps for battery swaps and vehicle redistribution tasks.
* Fleet management dashboards and analytics tools.
### f) Operations & Monitoring:
* Logging and tracing (Prometheus, Grafana, OpenTelemetry, Jaeger).
* Alerting and incident management.
* CI/CD for ML: Automated retraining and deployment using Kubeflow Pipelines.
* Model monitoring: drift detection, performance metrics, and retraining triggers.
* RBAC and tenant-based isolation.
* Audit & Compliance: Event logs stored in ELK stack; periodic AI fairness audits.
* Drift Detection: Model monitoring for performance and data consistency.

## AI Use Cases & Models
This section outlines the key AI-driven components and how they directly address MobilityCorp’s operational and customer challenges.

### Use Case 1: Predictive Demand Forecasting
* **Objective**: Predict vehicle demand by type and location to ensure availability.
* **Inputs**: Historical bookings, time-of-day, day-of-week, weather, events, nearby transit disruptions.
* **Models**: Time-series models (ARIMA, Prophet), Gradient Boosted Trees (LightGBM/CatBoost), Transformer-based models for longer horizons.
* **Outputs**: Probabilistic forecasts per zone with feature importances and scenario-based predictions.
* **Diagram**:
  
  ![Predictive Demand Forecasting](/assets/predictive_demand_forecasting.png "Predictive Demand Forecasting")

### Use Case 2: Battery & Charge Prioritization
* **Objective**: Predict which vehicles need charging or battery swaps and prioritize staff tasks.
* **Inputs**: SOC, usage patterns, trip length estimates, charging availability, battery health, temperature.
* **Models**: RUL regression or survival analysis, combined with priority scoring function.
* **Outputs**: Prioritized task list for staff with urgency scores.
* **Diagram**:
  
  ![Battery & Charge Prioritization](/assets/Battery_Charge_Prioritization.png "Battery & Charge Prioritization")
  
### Use Case 3: Staff Routing & Vehicle Redistribution
* **Objective**: Optimize routes for staff performing battery swaps and vehicle redistribution.
* **Inputs**: Forecasts, vehicle states, staff availability, traffic data, bay capacity.
* **Models**: VRPTW (Vehicle Routing Problem with Time Windows) solver using OR-Tools, hybrid heuristics, and reinforcement learning for long-term optimization.
* **Outputs**: Optimized staff routes and task assignments.
* **Diagram**:
  
  ![Staff Routing & Vehicle Redistribution](/assets/Staff_Routing_Vehicle_Redistribution.png "Staff Routing & Vehicle Redistribution")
  
### Use Case 4: Return Verification & Compliance
* **Objective**: Verify that vehicles are returned correctly and EVs are charged.
* **Inputs**: Customer photos, GPS data, bay locations.
* **Models**: Computer vision models (YOLO/Detectron for object detection, Mask R-CNN for damage detection, classification for charger connection).
* **Outputs**: Verification result with confidence score, detected issues, and human review queue.
* **Diagram**:
  
  ![Return Verification & Compliance](/assets/Return_Verification_Compliance.png "Return Verification & Compliance")
  
### Use Case 5: Personalized User Engagement
* **Objective**: Encourage regular usage and subscription adoption.
* **Inputs**: User trip history, saved locations, session context, travel patterns.
* **Models**: Session-based recommendation models (SASRec/Transformer), uplift models for personalized incentives.
* **Outputs**: Personalized suggestions, push notifications, targeted promotions.
* **Diagram**:
  
  ![Personalized User Engagement](/assets/Personalized_User_Engagement.png "Personalized User Engagement")
  
### Use Case 6: Fraud Detection & Security
* **Objective**: Detect suspicious activities such as GPS spoofing, false photos, or account misuse.
* **Inputs**: Unlock logs, GPS consistency, photo forensics, device fingerprints.
* **Models**: Rule-based checks + anomaly detection (Isolation Forest, LSTM autoencoder), supervised classifiers for known fraud patterns.
* **Outputs**: Risk scores, automated mitigation actions, human review when needed.
* **Diagram**:
  
  ![Fraud Detection & Security](/assets/Fraud_Detection_Security.png "Fraud Detection & Security")

# Agentic AI Implementation with Multi-Agent System

Integrating a multi-agent, agentic AI approach enhances MobilityCorp’s ability to manage complex operations dynamically, supports real-time adaptive decision-making, and allows the system to scale as new agents are introduced for additional services or geographic locations. MobilityCorp has complex, dynamic operational requirements involving real-time decision making for multiple vehicle types, staff routing, and customer interactions.

Implement an agent-based AI architecture where multiple specialized agents operate collaboratively to manage fleet operations, demand forecasting, battery swaps, and customer engagement.
*Each agent is responsible for a specific domain (e.g., Demand Agent, Battery Agent, Routing Agent, Recommender Agent, Fraud Detection Agent).
*Agents communicate via a message bus (Kafka) and share state through a centralized feature store.
*Decentralized decision-making allows for faster response, robustness, and modular scalability.

**Implementation Details**:

Agent Types:

* **Demand Agent**: Predicts short-term and long-term vehicle demand by location.
* **Battery Agent**: Monitors charge levels, predicts battery depletion, and schedules swaps.
* **Routing Agent**: Computes optimal paths for staff and vehicle redistribution.
* **Recommender Agent**: Suggests personalized trips and promotions to customers.
* **Vision Agent**: Verifies vehicle returns and detects damages.
* **Fraud Agent**: Monitors anomalies in GPS, unlocks, and payments.

  ![Agentic / GenAI Feature](/assets/agentic_ai_view.png "Agentic / GenAI Feature")
  
**Communication**: Agents communicate asynchronously using event streams and publish-subscribe patterns.

**Coordination**: A central orchestrator monitors agent performance, resolves conflicts, and triggers retraining or fallback mechanisms.

**Learning**: Agents can adapt policies via reinforcement learning and continuously improve via feedback from operations and customer interactions.

**Trade-offs**:

* Increased system complexity and need for careful orchestration.
* Requires robust monitoring to detect agent conflicts or miscoordination.
* Higher initial development cost, offset by improved scalability, modularity, and responsiveness.

# Architecture Decision Records (ADRs)

These detailed ADRs establish a foundation for MobilityCorp’s AI architecture, ensuring scalability, resilience, and responsible deployment of AI across forecasting, optimization, and customer engagement systems.

[Click on each of the links to read in detail]

1. [**ADR-001: Feature Store Adoption**](ADRs/ADR-001_Feature_Store_Adoption.md)
2. [**ADR-002: Model Serving Architecture**](ADRs/ADR-002_Model_Serving_Architecture.md)
3. [**ADR-003: Vision Model Deployment (Edge vs Cloud)**](ADRs/ADR-003_Vision_Model_Deployment.md)
4. [**ADR-004: Optimization Solver Choice**](ADRs/ADR-004_Optimization_Solver_Choice.md)
5. [**ADR-005: Data Retention & Privacy**](ADRs/ADR-005_Data_Retention_Privacy.md)
6. [**ADR-006: AI Validation & Human-in-the-Loop**](ADRs/ADR-006_AI_Validation_Human-in-the-Loop.md)
7. [**ADR-007: Model Retraining & Drift Detection**](ADRs/ADR-007_Model_Retraining_Drift_Detection.md)
8. [**ADR-008: Observability & Monitoring Stack**](ADRs/ADR-008_Observability_Monitoring_Stack.md)
9. [**ADR-009: Security & Access Control**](ADRs/ADR-009_Security_Access_Control.md)
10. [**ADR-010: Recommendation Engine Framework**](ADRs/ADR-010_Recommendation_Engine_Framework.md)

# AI Cost Governance Framework

To ensure MobilityCorp’s AI ecosystem remains efficient, predictable, and value-focused, a dedicated AI Cost Governance Framework is embedded across the entire lifecycle — from data ingestion to model deployment. This framework aligns technical excellence with financial accountability through five core principles:

**1. FinOps-Driven Design**

AI workloads are architected using a FinOps-first mindset, where cost visibility and efficiency are built into every stage.
Each AI service is tagged with cost centers, allowing precise tracking of expenses per model, per environment, and per team.
Forecasting dashboards visualize compute, storage, and inference costs in real time, helping teams balance accuracy against affordability.

**2. Tiered Workload Strategy**

AI processes are classified as real-time, near-real-time, or batch, and allocated infrastructure accordingly.
- Real-time inferences (e.g., battery health alerts, fraud detection) run on lightweight, autoscaling APIs with CPU/GPU quotas.
- Batch training and simulations are executed on spot or preemptible instances, scheduled during low-demand windows.
- Exploratory research and large experiments are sandboxed and governed by strict cost ceilings.
This structured approach prevents overprovisioning and ensures every compute cycle adds business value.

**3. Data Lifecycle Optimization**

Data storage follows a “hot–warm–cold” model.
- Recent and frequently queried data stays in fast-access, high-performance storage (e.g., time-series or cache layers).
- Mid-term data moves to optimized data lakes for model retraining.
- Older telemetry and logs are archived automatically to low-cost object storage.
- This not only reduces storage costs but also shortens data processing pipelines and improves query efficiency.

**4. Model Efficiency and Reuse**

Model optimization is continuous.
- Techniques like quantization, pruning, distillation, and transfer learning are applied to shrink model size and lower inference latency.
- A central model registry tracks reuse across cities, vehicle types, and scenarios, avoiding duplicate development.
- Idle or underperforming models are retired promptly, ensuring compute and storage resources are only allocated to active, value-creating AI assets.

**5. Continuous Monitoring and Cost–Value Feedback Loop**

Each AI service is linked to measurable KPIs — such as cost per inference, model ROI, utilization rate, and cost avoidance achieved through automation.
FinOps and data engineering teams review these insights periodically, fine-tuning budgets and model strategies.
By coupling performance metrics with financial indicators, MobilityCorp ensures AI remains both impactful and economically sustainable.

This governance model transforms AI spending from a black box into a transparent, measurable investment portfolio.
It creates a culture where data scientists, engineers, and business teams share accountability for both innovation and efficiency — ensuring every AI insight delivers not just intelligence, but also tangible return on spend.

# Validation, Governance & Monitoring
To ensure AI-driven operations are accurate, fair, and reliable, MobilityCorp implements validation processes, governance standards, and continuous monitoring across all models and operational systems.

## 1. **Model Validation & Performance Monitoring**

* **Forecasting Models**: Evaluate using CRPS, MAE, and coverage of prediction intervals.
* **RUL/Battery Models**: Use RMSE, calibration metrics, and time-to-failure precision/recall.
* **Vision Models**: Measure precision/recall for return verification, FPR for false fines, and human review rates.
* **Recommender Models**: Monitor uplift, retention lift, conversion rates, and long-term behavior changes.
**Processes**:
* Shadow deployments of new models to gather performance data without affecting live decisions.
* Canary rollouts to a small user group before full deployment.
* Human-in-the-loop for low-confidence or high-impact cases.

## 2. *Governance & Responsible AI*
* **Fairness**: Regular audits to ensure recommendations and incentives do not introduce bias.
* **Privacy**: Explicit user consent for targeted notifications and calendar integrations. Data encryption at rest and in transit.
* **Transparency**: Explainability using SHAP values for predictions and visual overlays for vision-based verifications.
* **Data Quality**: Automated checks on incoming telemetry and images to ensure consistency and completeness.

## 3. *Operational Monitoring*

* **Telemetry & Logging**: All model inferences and API calls are logged for traceability.
* **Alerting**: Prometheus/Grafana alerting on anomalies, system failures, or model performance degradation.
* **Drift Detection**: Monitor input distributions and outputs to detect concept drift and trigger retraining.
* **Dashboard & Analytics**: Centralized dashboards for staff and management to view fleet status, AI recommendations, and alerts.

## Risk Management
* **Fallbacks**: Rule-based systems if AI models fail.
* **Human-in-the-loop**: Critical tasks reviewed manually when needed.
* **Monitoring**: Continuous system health and model performance checks.
* **Feedback loops**: Customer and staff feedback incorporated into model retraining.

# Implementation Roadmap
**Approach**: Phased Rollout Strategy
This roadmap outlines the phased implementation plan to deploy MobilityCorp's AI-driven system, from initial MVP to full-scale production across multiple locations.

## 1. Phase 1

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

## 2. Phase 2
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

## 3. Phase 3
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

This phased roadmap ensures a controlled, scalable, and efficient rollout of MobilityCorp’s AI-driven solution, starting with a focused MVP and progressively expanding to full production capabilities.
