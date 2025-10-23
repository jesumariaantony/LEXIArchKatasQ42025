# Optimization Solver Choice

**Status:** Accepted

**Date:** [2025-10-22]

**Decision**: Use Google OR-Tools CP-SAT solver enhanced with metaheuristic optimization for staff routing and fleet balancing.

**Context**: Battery swap and redistribution tasks must be dynamically optimized based on real-time demand and fleet location.

**Rationale**: CP-SAT efficiently handles constraint satisfaction (time windows, capacity), while heuristic layers enable near-optimal real-time results.

**Implementation Details**:
* Periodic optimization every 15 minutes.
* Data fed from Kafka telemetry streams.
* Solver results stored in Redis for fast dispatching.

**Trade-offs**: May yield suboptimal results under extreme data volatility but achieves practical performance for real-time operations.
