# Data Retention & Privacy

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Define structured data retention policies with lifecycle management across data types.

**Context**: Balancing operational analytics, compliance (GDPR), and cost efficiency.

**Rationale**: Ensures legal compliance while maintaining enough historical data for retraining and root cause analysis.

**Implementation Details**:
* Raw images retained for 30 days; telemetry retained 12 months in hot storage, then archived to cold blob storage.
* Personally identifiable information (PII) encrypted using AES-256.
* Role-based access via Keycloak or similar
* 
**Trade-offs**: Storage cost vs data accessibility for analysis.
