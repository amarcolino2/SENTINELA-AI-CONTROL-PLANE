# ADR-005 - Deterministic Multi-Level Fallback Strategy

- Status: Accepted
- Date: 2026-06-15

## Context
AI provider instability, quota failures, and low-confidence outputs can break user workflows.

## Decision
Adopt deterministic fallback graph with three modes:
- Lateral fallback: switch equivalent model/provider.
- Downgrade fallback: cheaper/faster model with reduced scope.
- Escalation fallback: higher-capability model for quality recovery.

Fallback triggers include timeout, quota exceeded, rate limit, unavailability, low confidence, and policy violations.

## Consequences
Positive:
- Higher availability and graceful degradation.
- Predictable behavior under failure modes.

Negative:
- Requires continuous policy maintenance.
- Potential transient cost spikes during escalation.

## Alternatives Considered
- Retry-only policy.
- Manual intervention only.

## Rationale
Deterministic fallback logic minimizes disruption while preserving governance and auditability.
