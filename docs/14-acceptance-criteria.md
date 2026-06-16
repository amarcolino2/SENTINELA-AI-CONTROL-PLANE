# Acceptance Criteria - Sentinela AI Control Plane

## 1. Capability 01 - Intent Analysis
AC-INTENT-01:
- Given a request arrives
- When intent analysis runs
- Then objective, task class, complexity score, and RAG probability are produced with trace ID.

AC-INTENT-02:
- Given ambiguous user prompt
- When confidence of classification is low
- Then request is marked for clarification or high-capability routing.

## 2. Capability 02 - Context Governance
AC-CONTEXT-01:
- Given oversized context input
- When context governance executes
- Then context is compressed within token budget while preserving key facts.

AC-CONTEXT-02:
- Given multiple context sources
- When bundle is prepared
- Then lineage is recorded for each included artifact.

## 3. Capability 03 - Cost Intelligence
AC-COST-01:
- Given candidate routes
- When cost estimation executes
- Then each route has pre-execution estimated cost range and ROI score.

AC-COST-02:
- Given hard budget limit
- When projected execution exceeds limit
- Then route is rejected or downgraded by policy.

## 4. Capability 04 - Model Routing
AC-ROUTING-01:
- Given simple low-risk task
- When routing decision is made
- Then a local model is selected when quality floor is satisfied.

AC-ROUTING-02:
- Given high-complexity legal task
- When routing decision is made
- Then premium model path and confidence gate are enforced.

## 5. Capability 05 - Multi-Agent Orchestration
AC-AGENT-01:
- Given architecture planning request
- When orchestration executes
- Then planner, architect, and documentation agents run with assigned models per policy.

AC-AGENT-02:
- Given code generation workflow
- When developer output completes
- Then reviewer, security, and testing gates execute before finalization.

## 6. Capability 06 - Fallback Intelligence
AC-FALLBACK-01:
- Given provider timeout
- When failure signal is detected
- Then fallback route is selected and resumed within policy SLA.

AC-FALLBACK-02:
- Given repeated low-confidence outputs
- When threshold is breached
- Then escalation fallback executes with reason code.

## 7. Capability 07 - Confidence Engine
AC-CONF-01:
- Given generated response
- When confidence scoring executes
- Then confidence score and calibration metadata are persisted.

AC-CONF-02:
- Given confidence below floor
- When gate policy evaluates
- Then second-opinion workflow is triggered.

## 8. Capability 08 - Observability
AC-OBS-01:
- Given any execution
- When it completes
- Then tokens, latency, cost, route, and quality signals are queryable.

AC-OBS-02:
- Given fallback event occurs
- When telemetry is ingested
- Then dashboards and alerts reflect event within observability SLA.

## 9. Capability 09 - Skills
AC-SKILL-01:
- Given new skill version candidate
- When harness evaluation runs
- Then promotion occurs only if release gates pass.

AC-SKILL-02:
- Given degraded skill performance over time
- When retirement policy threshold is met
- Then skill version is retired and replacement selected.
