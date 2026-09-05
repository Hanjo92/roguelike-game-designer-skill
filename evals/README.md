# Skill Evaluation Suite

Use these scenarios to compare the `roguelike-game-designer` skill across Codex, Claude Code, Antigravity, or another Agent Skills-compatible agent.

## Procedure

1. Start a fresh session with the skill installed.
2. Submit one scenario's **Prompt** exactly as written.
3. Do not provide extra clarification unless the scenario explicitly permits it.
4. Save the complete response and identify agent/model/version.
5. Score it using `rubric.md` and the scenario-specific checks.
6. Record critical failures separately from numeric score.

## Scenarios

- `concept-design.md` — coherent concept and production scope
- `subgenre-selection.md` — dimension-first genre recommendation
- `item-review.md` — content role, decision value, and recursion safety
- `boss-review.md` — telegraph, counterplay, and build robustness
- `economy-diagnosis.md` — root-cause diagnosis rather than arbitrary tuning
- `procedural-generation.md` — algorithm selection plus validation and repair
- `run-pacing.md` — run architecture, reward cadence, and director boundaries
- `bad-design-detection.md` — resistance to harmful or shallow genre assumptions
- `accessibility-difficulty.md` — modular access support that preserves the intended challenge contract

## Passing Standard

- No critical failure
- At least 70/100 overall
- At least half credit in every core dimension
- Scenario-specific mandatory checks satisfied

Compare agents on reasoning quality and actionable output, not prose length. A longer response should not score higher unless it resolves more of the design problem.
