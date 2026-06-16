# Non-Functional Requirements - Sentinela AI Control Plane

## 1. Performance
NFR-PERF-01: P50 end-to-end latency for simple tasks <= 1.5s (local routes).
NFR-PERF-02: P95 end-to-end latency for simple tasks <= 3.0s.
NFR-PERF-03: P95 end-to-end latency for complex orchestrated tasks <= 18s.
NFR-PERF-04: Routing decision computation <= 120ms P95.

## 2. Availability and Reliability
NFR-REL-01: Routing control plane availability >= 99.5% monthly.
NFR-REL-02: Telemetry pipeline availability >= 99.9% monthly.
NFR-REL-03: Automatic fallback activation within <= 2s of failure detection.
NFR-REL-04: Idempotent event processing for all critical orchestration events.

## 3. Scalability
NFR-SCL-01: Support 500 requests/sec baseline with horizontal scaling.
NFR-SCL-02: Burst tolerance to 3x baseline for up to 15 minutes.
NFR-SCL-03: Skill evaluation pipeline must process 100k eval samples/day.

## 4. Security and Privacy
NFR-SEC-01: Encryption in transit (TLS 1.2+) and at rest (AES-256).
NFR-SEC-02: Fine-grained role/attribute-based access control by tenant and environment.
NFR-SEC-03: Secrets must be stored in managed secret vaults only.
NFR-SEC-04: PII data handling must enforce minimization and masking policies.
NFR-SEC-05: Prompt-injection and exfiltration checks on inbound context and outbound responses.

## 5. Compliance and Auditability
NFR-CMP-01: Immutable audit log for routing decisions and policy evaluations.
NFR-CMP-02: Full lineage for context artifacts used in execution.
NFR-CMP-03: Retention policy configurable by tenant and regulation profile.

## 6. Observability
NFR-OBS-01: 100% request trace IDs propagated through all orchestration stages.
NFR-OBS-02: Cost telemetry lag <= 60 seconds from execution completion.
NFR-OBS-03: Quality estimate + observed quality available for >= 95% of requests.

## 7. Operability
NFR-OPS-01: Blue/green policy deployment for routing and fallback rules.
NFR-OPS-02: Canary rollout support by tenant, workload class, and geography.
NFR-OPS-03: Feature flags for model/provider enablement and emergency kill switch.

## 8. Extensibility
NFR-EXT-01: Provider plugin contract for adding future models without core rewrite.
NFR-EXT-02: Agent plugin contract for adding/removing agents at runtime boundaries.
NFR-EXT-03: Policy language extensibility for new governance constraints.

## 9. Cost Efficiency
NFR-COST-01: Cost estimate error <= 15% P75 and <= 25% P95.
NFR-COST-02: At least 40% of low-complexity requests routed to local models when quality threshold met.
NFR-COST-03: Premium escalation requires explicit policy justification code.
