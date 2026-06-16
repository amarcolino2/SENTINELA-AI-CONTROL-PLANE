# ADR-002 - Local-First with Premium Escalation Thresholds

- Status: Accepted
- Date: 2026-06-15

## Context
Premium models improve quality in complex tasks but can significantly increase cost and vendor dependency.

## Decision
Use local-first routing where quality floor and risk policies are met. Escalate to premium only when:
- complexity threshold exceeded,
- confidence below threshold,
- high-risk domain policy requires premium,
- local capacity/availability constraints occur.

## Consequences
Positive:
- Significant cost savings for low/medium complexity tasks.
- Reduced external provider dependency.

Negative:
- Requires robust quality gating for local models.
- More calibration effort for confidence thresholds.

## Alternatives Considered
- Premium-first default routing.
- Strictly local-only operation.

## Rationale
Local-first with controlled escalation best aligns with Quality/Cost optimization objective.
