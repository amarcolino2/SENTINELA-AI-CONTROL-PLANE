# ADR-001 - Policy-Driven Dynamic Model Routing

- Status: Accepted
- Date: 2026-06-15

## Context
Static model selection causes poor quality-cost outcomes under variable workloads and provider conditions.

## Decision
Adopt policy-driven dynamic model routing using multi-factor scoring:
- intent category
- complexity
- budget envelope
- latency SLO
- confidence history
- model availability

## Consequences
Positive:
- Better quality/cost optimization.
- Improved resiliency through route recalculation.
- Explainable decisions via reason codes.

Negative:
- Increased control-plane complexity.
- Requires rigorous policy testing and simulation.

## Alternatives Considered
- Static model per workload class.
- User-selected model only.

## Rationale
Only dynamic policy routing can satisfy mixed constraints of quality, latency, and spend at runtime.
