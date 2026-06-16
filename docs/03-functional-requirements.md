# Functional Requirements - Sentinela AI Control Plane

## 1. Capability 01 - Intent Analysis
FR-C01-01: System shall detect task objective and domain category.
FR-C01-02: System shall classify request type (Q&A, analysis, architecture, code, legal, security, documentation, etc.).
FR-C01-03: System shall estimate complexity score on a normalized 0-100 scale.
FR-C01-04: System shall estimate RAG necessity probability.
FR-C01-05: System shall emit `IntentAssessed` event with confidence and rationale.

## 2. Capability 02 - Context Governance
FR-C02-01: System shall apply relevance ranking over provided context artifacts.
FR-C02-02: System shall perform context compression with token budget constraints.
FR-C02-03: System shall support progressive summarization across long sessions.
FR-C02-04: System shall maintain context lineage (source, transform, inclusion reason).
FR-C02-05: System shall emit `ContextPrepared` and `ContextCompressed` telemetry.

## 3. Capability 03 - Cost Intelligence
FR-C03-01: System shall estimate pre-execution token and cost ranges per candidate model.
FR-C03-02: System shall calculate expected ROI of candidate execution plans.
FR-C03-03: System shall enforce per-request, per-tenant, and per-product budgets.
FR-C03-04: System shall support policy-based hard stops and soft warnings.
FR-C03-05: System shall emit `CostEstimated` with uncertainty band.

## 4. Capability 04 - Model Routing
FR-C04-01: System shall select model/provider based on complexity, budget, latency SLO, and availability.
FR-C04-02: System shall select runtime params (temperature, max tokens, context mode).
FR-C04-03: System shall support local model routing (Gemma 3, Qwen 3, DeepSeek, Llama via Ollama/vLLM).
FR-C04-04: System shall support premium model routing (Claude Opus/Sonnet, GPT-5/GPT-5 Mini, Gemini, extensible providers).
FR-C04-05: System shall persist route decision and reason codes for auditability.

## 5. Capability 05 - Multi-Agent Orchestration
FR-C05-01: System shall compose agent plans from a catalog:
- Planner Agent
- Research Agent
- RAG Agent
- Architect Agent
- Developer Agent
- Reviewer Agent
- Security Agent
- Testing Agent
- Documentation Agent
FR-C05-02: System shall support sequential, parallel, and gated orchestration patterns.
FR-C05-03: System shall support role-specific model assignment per agent stage.
FR-C05-04: System shall support human approval checkpoints for high-risk workflows.
FR-C05-05: System shall emit `AgentPlanCommitted` and per-step lifecycle events.

## 6. Capability 06 - Fallback Intelligence
FR-C06-01: System shall detect timeout, quota exceeded, rate limit, unavailability, and low confidence failures.
FR-C06-02: System shall recompute strategy via fallback policy graph.
FR-C06-03: System shall support downgrade, lateral, and escalation fallback modes.
FR-C06-04: System shall preserve partial outputs when safe and useful.
FR-C06-05: System shall emit `FallbackTriggered` and `FallbackResolved` events.

## 7. Capability 07 - Confidence Engine
FR-C07-01: System shall generate confidence score for response and plan quality.
FR-C07-02: System shall trigger second-opinion workflow below threshold.
FR-C07-03: System shall escalate to higher-tier model where required by policy.
FR-C07-04: System shall track confidence calibration drift over time.
FR-C07-05: System shall emit `ConfidenceScored` and `EscalationRequested` events.

## 8. Capability 08 - Observability
FR-C08-01: System shall record tokens, latency, cost, chosen model, model switches, and fallbacks.
FR-C08-02: System shall capture estimated quality vs observed quality.
FR-C08-03: System shall record hallucination detection outcomes and review results.
FR-C08-04: System shall expose near-real-time dashboards and API query interfaces.
FR-C08-05: System shall support end-to-end trace correlation by request and workflow IDs.

## 9. Capability 09 - Core and Meta Skills
FR-C09-01: System shall support core skills lifecycle (versioning, benchmark, rollout, rollback).
FR-C09-02: System shall support meta-skills for skill selection and optimization.
FR-C09-03: System shall support skill retirement policies based on quality/cost decay.
FR-C09-04: System shall support skill cost governance with per-skill budget policies.
FR-C09-05: System shall emit `SkillVersionPromoted`, `SkillVersionRetired`, and governance events.

## 10. Canonical Execution Examples
EX-01 Simple question -> route to Gemma 3 local when quality and latency thresholds pass.
EX-02 Complex legal analysis -> route to Claude Sonnet with confidence gating.
EX-03 Architecture planning -> Planner on Claude Opus, Architect on GPT-5, Documentation on local model.
EX-04 Code generation pipeline -> GPT-5 Developer, Reviewer Agent, Security Agent, Testing Agent before finalize.
