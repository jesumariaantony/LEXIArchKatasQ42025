# Model Retraining & Drift Detection

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Implement automated model drift detection and retraining pipeline using Evidently AI and Kubeflow Pipelines.

**Context**: User patterns, fleet utilization, and city conditions change frequently, risking model degradation.

**Rationale**: Continuous evaluation ensures predictive accuracy and operational reliability.

**Implementation Details**:
* Data drift and concept drift monitored daily.
* Retraining triggers when accuracy drops >5% or drift score >0.3.
* Automatic rollback if post-deployment metrics fall below threshold.

**Trade-offs**: Increased compute and storage costs, but ensures models remain adaptive and high-performing.
