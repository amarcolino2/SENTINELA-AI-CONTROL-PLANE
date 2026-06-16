# Observability Specifications - Sentinela AI Control Plane

## 1. Telemetry Model
Observability uses a unified schema for metrics, traces, logs, and evaluation outcomes.

## 2. Required Telemetry Dimensions
- request_id, workflow_id, tenant_id, product_id
- intent_class, complexity_bucket, risk_class
- model_id, provider, route_class
- agent_name, agent_step, skill_version
- fallback_type, escalation_reason

## 3. Metrics
### Cost Metrics
- tokens_input, tokens_output, cache_tokens
- estimated_cost, actual_cost
- cost_variance_pct

### Performance Metrics
- routing_latency_ms
- agent_step_latency_ms
- end_to_end_latency_ms
- fallback_recovery_ms

### Quality Metrics
- estimated_quality_score
- observed_quality_score
- confidence_score
- hallucination_flag_rate
- task_success_rate

### Reliability Metrics
- model_error_rate
- rate_limit_frequency
- timeout_frequency
- fallback_trigger_rate

## 4. Distributed Tracing
- Every request must propagate a trace context across all contexts and agents.
- Trace spans required for: intent, context prep, cost estimate, routing, each agent step, fallback, response synthesis.
- Mandatory span attributes: model, token counts, policy IDs, decision reason codes.

## 5. Logging
- Structured JSON logs only.
- Decision logs must include candidate model set and disqualification reasons.
- Security-sensitive fields must be masked or hashed.

## 6. Dashboards
- Executive Dashboard: quality/cost trend, ROI, premium ratio.
- SRE Dashboard: latency, errors, fallback health, provider status.
- FinOps Dashboard: spend by tenant/product/model/task.
- Quality Dashboard: confidence calibration, hallucination rates, reviewer outcomes.

## 7. Alerts
- P95 latency breach for 5-minute window.
- Cost anomaly detection above historical baseline.
- Confidence degradation drift.
- Hallucination spike in high-risk domains.

## 8. Data Retention
- Hot telemetry: 30 days.
- Warm analytics: 180 days.
- Cold audit archive: 1-3 years configurable by policy.
