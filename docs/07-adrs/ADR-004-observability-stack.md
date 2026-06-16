# ADR-004 - Unified Observability with Cost and Quality Telemetry

- Status: Accepted
- Date: 2026-06-15

## Context
AI systems fail silently without unified operational and semantic telemetry.

## Decision
Implement unified observability schema capturing:
- request trace metadata
- tokens in/out/cache
- latency by stage
- estimated and realized cost
- model and route transitions
- confidence and quality outcomes
- hallucination detection outcomes

## Consequences
Positive:
- End-to-end visibility and accountability.
- Enables quality-cost optimization loops.

Negative:
- Additional storage and processing overhead.
- Requires governance over telemetry PII exposure.

## Alternatives Considered
- Basic infra metrics only.
- Provider-native logging only.

## Rationale
Quality/Cost optimization is impossible without integrated runtime, financial, and quality observability.
