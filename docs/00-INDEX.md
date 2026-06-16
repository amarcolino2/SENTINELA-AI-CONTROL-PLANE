# Sentinela AI Control Plane - SDD Index

## Purpose
This repository contains the Specification Driven Development (SDD) baseline for Sentinela AI Control Plane, an AI runtime governance platform that optimizes quality-to-cost outcomes across local and premium model ecosystems.

## Guiding Principle
Maximize:

$$
\text{Execution Value} = \frac{\text{Quality}}{\text{Cost}}
$$

Subject to latency, safety, and availability constraints.

## Document Map
1. [Vision](01-vision.md)
2. [Business Requirements](02-business-requirements.md)
3. [Functional Requirements](03-functional-requirements.md)
4. [Non-Functional Requirements](04-non-functional-requirements.md)
5. [Bounded Contexts](05-bounded-contexts.md)
6. [Event Storming](06-event-storming.md)
7. [Architecture Decision Records](07-adrs/)
8. [Agent Specifications](08-agent-specifications.md)
9. [Model Routing Rules](09-model-routing-rules.md)
10. [Cost Governance Rules](10-cost-governance-rules.md)
11. [Observability Specifications](11-observability-specifications.md)
12. [Security Specifications](12-security-specifications.md)
13. [AI Evaluation Harness](13-ai-evaluation-harness.md)
14. [Acceptance Criteria](14-acceptance-criteria.md)
15. [Roadmap](15-roadmap.md)

## Requirement Traceability Matrix (High-Level)
- Intent Analysis -> FR-C01, BC-Intent, EV-IntentAssessed, AC-INTENT-*.
- Context Governance -> FR-C02, BC-Context, EV-ContextCompressed, AC-CONTEXT-*.
- Cost Intelligence -> FR-C03, BC-Cost, EV-CostEstimated, AC-COST-*.
- Model Routing -> FR-C04, BC-Routing, EV-ModelRouted, AC-ROUTING-*.
- Multi-Agent Orchestration -> FR-C05, BC-Orchestration, EV-AgentPlanCommitted, AC-AGENT-*.
- Fallback Intelligence -> FR-C06, BC-Fallback, EV-FallbackTriggered, AC-FALLBACK-*.
- Confidence Engine -> FR-C07, BC-Confidence, EV-ConfidenceScored, AC-CONF-*.
- Observability -> FR-C08, BC-Observability, EV-TelemetryRecorded, AC-OBS-*.
- Core/Meta Skills -> FR-C09, BC-Skills, EV-SkillVersionPromoted, AC-SKILL-*.

## Scope Constraints
- Specification only. No runtime implementation in this phase.
- Architecture and operations aligned with modern AI engineering practices (2025-2026).
