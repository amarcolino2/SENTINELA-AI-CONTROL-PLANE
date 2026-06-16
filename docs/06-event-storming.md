# Event Storming - Sentinela AI Control Plane

## 1. Event Storming Scope
Covers request lifecycle from intake to final response and post-execution evaluation.

## 2. Core Domain Events
- RequestReceived
- IntentAssessed
- ContextPrepared
- ContextCompressed
- CostEstimated
- BudgetViolationDetected
- ModelRouted
- AgentPlanCommitted
- AgentStepStarted
- AgentStepCompleted
- ConfidenceScored
- EscalationRequested
- FallbackTriggered
- FallbackResolved
- ResponseGenerated
- ResponseDelivered
- TelemetryRecorded
- HallucinationDetected
- QualityObserved
- SkillVersionPromoted
- SkillVersionRetired

## 3. Commands
- AssessIntent
- PrepareContext
- CompressContext
- EstimateCost
- EvaluateBudget
- SelectModelRoute
- CommitAgentPlan
- ExecuteAgentStep
- ScoreConfidence
- TriggerFallback
- ReRouteExecution
- RecordTelemetry
- RunQualityEvaluation
- PromoteSkillVersion
- RetireSkillVersion

## 4. Aggregates
- ExecutionRequest
- RoutingDecision
- AgentPlan
- ConfidenceAssessment
- FallbackPlan
- TelemetryTrace
- SkillVersion

## 5. Policies
POL-01: If `ComplexityScore < 25` and no sensitive domain and cost envelope tight -> prefer local route.
POL-02: If legal/regulated domain and complexity high -> route premium with confidence gate enabled.
POL-03: If low confidence after first pass -> run second opinion or escalate model class.
POL-04: If provider timeout/rate-limit -> execute fallback graph within 2 seconds.
POL-05: If hallucination detected in high-risk domain -> block auto-delivery, require review.

## 6. Read Models
- RequestExecutionTimelineView
- CostByTenantView
- ModelUtilizationView
- FallbackIncidentsView
- QualityVsCostView
- ConfidenceCalibrationView

## 7. Lifecycle Narrative
1. `RequestReceived`.
2. Intent service emits `IntentAssessed`.
3. Context governance emits `ContextPrepared` and optionally `ContextCompressed`.
4. Cost engine emits `CostEstimated`; policy may raise `BudgetViolationDetected`.
5. Routing engine emits `ModelRouted`.
6. Orchestrator emits `AgentPlanCommitted`, followed by step events.
7. Confidence engine emits `ConfidenceScored`; possible `EscalationRequested`.
8. Failures trigger `FallbackTriggered`, then `FallbackResolved`.
9. Runtime emits `ResponseGenerated` and `ResponseDelivered`.
10. Observability emits `TelemetryRecorded`; evaluators may emit `HallucinationDetected` and `QualityObserved`.

## 8. Example Event Flow: Architecture Planning
`RequestReceived` -> `IntentAssessed` (architecture/high complexity) -> `CostEstimated` (hybrid plan) -> `ModelRouted` (Opus planner + GPT-5 architect + local documentation) -> `AgentPlanCommitted` -> step completion events -> `ConfidenceScored` -> `ResponseDelivered` -> `QualityObserved`.
