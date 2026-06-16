# Cost Governance Rules - Sentinela AI Control Plane

## 1. Governance Objective
Ensure AI execution maximizes quality-per-cost while honoring budget, risk, and SLA constraints.

## 2. Budget Model
- Budget scopes: organization, tenant, product, environment, workflow, request.
- Budget types:
  - Hard limit: execution must not exceed threshold.
  - Soft limit: execution allowed with alert and reason code.
- Reset windows: hourly, daily, monthly configurable.

## 3. Pre-Execution Cost Controls
CG-01: Every candidate execution plan must include estimated token and dollar ranges.
CG-02: Plans must compute expected utility score:

$$
Utility = \frac{ExpectedQuality \times CriticalityWeight}{ExpectedCost}
$$

CG-03: Router must choose highest-utility plan that satisfies policy constraints.
CG-04: Premium execution requires policy tag and reason code.

## 4. Runtime Cost Controls
CG-05: Enforce max token caps per step and per workflow.
CG-06: Abort or re-route when projected cost exceeds hard limit.
CG-07: Trigger downgrade strategy when remaining budget cannot support current route.
CG-08: Reserve budget envelopes for critical workflows to avoid starvation.

## 5. Post-Execution Cost Intelligence
CG-09: Record estimate vs actual variance by model and task class.
CG-10: Update calibration factors weekly or when drift exceeds threshold.
CG-11: Produce ROI reports by route class (local/premium/hybrid).

## 6. Cost Policy Tiers
- Tier A (Cost-Sensitive): local-first, strict token caps, premium by exception.
- Tier B (Balanced): hybrid routing with confidence gating.
- Tier C (Quality-Critical): premium-first with guardrails and auditing.

## 7. Alerts and Controls
- Alert on 80%, 90%, 100% budget utilization.
- Alert on cost estimate error > 25% P95.
- Alert when premium usage ratio exceeds policy band.

## 8. Governance Review Cadence
- Daily operational review: spikes, anomalies, incidents.
- Weekly optimization review: routing thresholds and policy tuning.
- Monthly business review: ROI, quality trends, budget resets.
