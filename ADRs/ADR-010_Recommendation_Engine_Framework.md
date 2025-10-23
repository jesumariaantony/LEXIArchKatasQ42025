# Recommendation Engine Framework

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Use LightFM for hybrid recommendation engine.

**Context**: Using recommendation to give insights and help customer decide better

**Rationale**: Combines collaborative and content-based filtering, suitable for frequent but dynamic rental use cases.

**Implementation Details**:
* Model trained nightly using booking and telemetry data.
* Integrates with feature store and customer profiles.
* Deployed via Seldon Core endpoint.

**Trade-offs**: Limited scalability compared to deep learning recommenders but interpretable and fast to deploy.
