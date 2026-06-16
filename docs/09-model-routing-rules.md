# Model Routing Rules - Sentinela AI Control Plane

## 1. Routing Inputs
- Intent class
- Complexity score (0-100)
- Risk class (low/medium/high/critical)
- RAG necessity probability
- Latency SLO
- Budget envelope
- Provider health and quota state
- Historical confidence calibration

## 2. Route Classes
- Local: Gemma 3, Qwen 3, DeepSeek, Llama (Ollama/vLLM)
- Premium: Claude Opus, Claude Sonnet, GPT-5, GPT-5 Mini, Gemini
- Hybrid: mixed models across agent stages

## 3. Decision Matrix (Baseline)
1. Complexity 0-24 and low risk:
- Prefer local model with low temperature (0.1-0.3).
2. Complexity 25-49 and medium risk:
- Local-first; premium fallback on low confidence.
3. Complexity 50-74 or high business impact:
- Premium default (Sonnet/GPT-5 Mini), with confidence checks.
4. Complexity 75-100 or critical domain:
- Premium high-capability path (Claude Opus/GPT-5) + second opinion.

## 4. RAG Activation Rules
- Enable RAG when retrieval probability >= configured threshold (default 0.55).
- Force RAG for policy-marked grounded-answer domains.
- Skip RAG for purely generative/creative tasks unless explicitly requested.

## 5. Parameter Policies
- Deterministic tasks (compliance, code fixes): temperature 0.0-0.2.
- Analytical tasks: temperature 0.2-0.5.
- Creative drafting: temperature 0.6-0.9 subject to safety policies.
- Max tokens capped by budget and context utility score.

## 6. Canonical Scenarios
- Example 1 simple question -> Gemma 3 local.
- Example 2 complex legal analysis -> Claude Sonnet.
- Example 3 architecture planning -> Claude Opus (Planner), GPT-5 (Architect), Gemma local (Documentation).
- Example 4 code generation -> GPT-5 (Developer) -> Reviewer Agent -> Security Agent -> Testing Agent.

## 7. Fallback Graph
1. Same class lateral switch (e.g., Sonnet -> GPT-5 Mini).
2. Cross-provider equivalent class.
3. Escalation class for confidence recovery.
4. Cost-guard downgrade route if budget hard limit reached.

## 8. Explainability Requirements
Each routing decision must store:
- selected model and provider
- disqualified candidates
- reason codes
- policy IDs evaluated
- expected vs actual cost and latency
