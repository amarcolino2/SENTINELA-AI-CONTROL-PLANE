# Agent Specifications - Sentinela AI Control Plane

## 1. Agent Catalog

### 1.1 Planner Agent
- Purpose: decompose complex objectives into executable plans.
- Inputs: intent profile, constraints, success criteria.
- Outputs: ordered task graph with dependencies and risk flags.
- Default Models: Claude Opus or GPT-5 for high complexity.
- Escalation: if ambiguity remains high, invoke Research Agent.

### 1.2 Research Agent
- Purpose: gather and synthesize external/internal evidence.
- Inputs: research questions, source policies.
- Outputs: evidence packets with citations and confidence.
- Default Models: Claude Sonnet, GPT-5 Mini, local for low risk.
- Escalation: invoke RAG Agent for retrieval-heavy workloads.

### 1.3 RAG Agent
- Purpose: retrieve, rank, and ground outputs in trusted corpora.
- Inputs: query intent, retrieval scope, filters.
- Outputs: ranked passages, evidence maps, source lineage.
- Default Models: local reranker + premium synthesizer for critical cases.
- Escalation: security-sensitive retrieval to Security Agent pre-check.

### 1.4 Architect Agent
- Purpose: design system architecture and trade-off analysis.
- Inputs: requirements, constraints, NFRs.
- Outputs: architecture options, ADR candidates, risk analysis.
- Default Models: GPT-5, Claude Opus for highest complexity.
- Escalation: second opinion if confidence < threshold.

### 1.5 Developer Agent
- Purpose: implement code-level changes from approved specs.
- Inputs: approved design, coding standards, test obligations.
- Outputs: code artifacts, implementation notes.
- Default Models: GPT-5 for production code generation.
- Escalation: security-critical changes trigger Security Agent.

### 1.6 Reviewer Agent
- Purpose: verify correctness, maintainability, and regression risk.
- Inputs: diff, tests, static analysis signals.
- Outputs: findings list, severity labels, remediation guidance.
- Default Models: GPT-5 Mini or Sonnet; escalate for critical systems.

### 1.7 Security Agent
- Purpose: detect vulnerabilities, prompt injection risk, data leakage.
- Inputs: code/output/context lineage, policy profile.
- Outputs: risk report, blocks, required mitigations.
- Default Models: premium for high assurance; local for triage.

### 1.8 Testing Agent
- Purpose: generate and validate test strategy and test assets.
- Inputs: behavior specs, code changes, risk classification.
- Outputs: test cases, coverage report, failure analysis.
- Default Models: GPT-5 Mini/local for broad suites; premium for critical paths.

### 1.9 Documentation Agent
- Purpose: produce concise, accurate technical documentation.
- Inputs: finalized outputs from planner/developer/reviewer.
- Outputs: docs, release notes, runbooks.
- Default Models: local models for low-complexity narrative generation.

## 2. Orchestration Patterns
- Sequential: planner -> architect -> developer -> reviewer -> security -> testing -> documentation.
- Parallel: research + rag retrieval in parallel before synthesis.
- Gated: human approval before production-impacting steps.

## 3. Agent Contracts
Each agent contract must define:
- input schema
- output schema
- quality criteria
- cost class (low/medium/high)
- retry/fallback policy
- telemetry obligations

## 4. Escalation Rules
- Low confidence or policy violation -> escalate model class and/or invoke specialist agent.
- High-risk domains (legal, medical, security) -> mandatory reviewer/security gates.
- Budget breach risk -> re-plan with cost-constrained strategy.
