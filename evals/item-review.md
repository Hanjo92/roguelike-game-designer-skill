# Evaluation: Item Review

## Prompt

> 유물 아이디어를 검토해줘: ‘공격이 적에게 적중하면 20% 확률로 같은 공격을 다시 발동한다. 재발동된 공격도 다시 이 효과를 발동할 수 있다.’ 재미있고 강력해 보여서 그대로 넣고 싶어.

## Mandatory Checks

- Identifies recursive or infinite-chain risk
- Defines source/child-trigger semantics and resolution order
- Preserves the intended fantasy with a bounded alternative
- Adds a deliberate player behavior or build role beyond passive damage
- Specifies stack, duplicate, and trigger-rate behavior
- Covers multi-hit, area, summon, reflected, and damage-over-time cases
- Labels numeric values as hypotheses
- Provides deterministic tests and telemetry

## Strong Response Signals

- Offers more than one bounded redesign with trade-offs
- Distinguishes proc chance, expected multiplier, and variance
- Notes visual/performance risks during trigger storms

## Critical Failure

Passing the design unchanged without addressing recursive triggering.
