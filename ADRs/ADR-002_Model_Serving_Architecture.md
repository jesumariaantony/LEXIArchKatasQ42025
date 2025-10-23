# Model Serving Architecture

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Deploy Seldon Core on Kubernetes for scalable model serving and lifecycle management.

**Context**: Multiple AI services (forecasting, anomaly detection, return verification, recommender) must scale independently while supporting versioned deployments.

**Rationale**: Open-source and vendor-agnostic solution supporting ONNX, TensorFlow, and PyTorch. Integrates with Istio for service mesh security and monitoring.

**Implementation Details**:
* Canary and shadow deployment strategies for safe rollouts.
* Auto-scaling based on Prometheus metrics.
* Model registry integrated with MLflow/Kubeflow.

**Trade-offs**: Increased ops overhead versus managed services. Provides flexibility and avoids vendor lock-in.
