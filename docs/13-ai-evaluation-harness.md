# AI Evaluation Harness - Sentinela AI Control Plane

## 1. Purpose
Provide continuous, automated validation of routing quality, cost efficiency, confidence calibration, and safety outcomes.

## 2. Harness Architecture
- Dataset Registry: versioned benchmark sets by domain/task/risk.
- Scenario Runner: executes fixed and stochastic test scenarios.
- Evaluator Suite: quality, factuality, safety, cost, latency evaluators.
- Comparator: baseline vs candidate policy/model/agent strategy.
- Report Generator: release gate and drift analysis outputs.

## 3. Evaluation Dimensions
- Quality: relevance, correctness, completeness, structure.
- Cost: actual vs expected spend, utility score.
- Latency: stage-level and end-to-end SLO compliance.
- Confidence: calibration (Brier score, reliability curves).
- Safety: policy violations, injection susceptibility, leakage risk.

## 4. Benchmark Suites
- Intent classification suite.
- Context compression quality suite.
- Routing optimality suite (quality/cost frontier).
- Multi-agent workflow consistency suite.
- Hallucination detection and mitigation suite.
- Security red-team suite.

## 5. Test Types
- Offline deterministic regression tests.
- Shadow traffic replay tests.
- Online A/B routing policy experiments.
- Chaos/failure injection tests for fallback behavior.

## 6. Release Gates
A policy/model/agent update can be promoted only if:
- no critical safety regressions,
- quality score non-inferiority or improvement,
- cost increase justified by measured quality lift,
- latency SLO adherence within thresholds.

## 7. Scoring Framework
Composite score example:

$$
Score = 0.35Q + 0.20S + 0.15C_f + 0.15L + 0.15Conf
$$

Where:
- $Q$ = quality
- $S$ = safety
- $C_f$ = cost fitness
- $L$ = latency fitness
- $Conf$ = confidence calibration

## 8. Outputs
- Promotion recommendation (approve/reject).
- Regression report by capability.
- Drift report by tenant/task/model.
- Actionable tuning suggestions (thresholds, routing weights, fallback graph).
