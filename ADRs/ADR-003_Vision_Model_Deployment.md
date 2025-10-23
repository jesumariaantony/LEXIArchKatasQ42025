# Vision Model Deployment (Edge vs Cloud)

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Hybrid inference approach — edge models for instant feedback and cloud models for final validation.

**Context**: Customers must upload vehicle return photos for proof; low-latency feedback enhances user experience.

**Rationale**: Edge inference enables fast visual checks (e.g., photo clarity, presence validation), while cloud GPUs perform deeper verification (damage detection, charger plug-in confirmation).

**Implementation Details**:
* TensorRT-optimized edge models deployed via mobile SDK.
* Cloud inference via AWS Sagemaker or Azure ML endpoint with GPU acceleration.

**Trade-offs**: Requires synchronization of model versions and latency management between edge and cloud.
