# Feature Store Adoption

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Adopt Feast as the centralized feature store for both real-time and batch features.
**Context**: Multiple ML models (forecasting, RUL prediction, recommendations) require consistent feature engineering pipelines. Data originates from heterogeneous sources such as GPS, IoT sensors, and booking systems.
**Rationale**: Provides a single source of truth for features, minimizing data leakage, training-serving skew, and redundant computation. Enables consistent offline training and online inference.

**Implementation Details**:
* Store metadata in PostgreSQL.
* Use Redis as the online feature store for low-latency lookups.
* Integrated with Kafka for event-driven feature updates.

**Trade-offs**: Added complexity in managing data lineage and consistency. Requires CI/CD integration for feature versioning.
