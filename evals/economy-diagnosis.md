# Evaluation: Economy Diagnosis

## Prompt

> 플레이어 승률이 18%라 목표 30%보다 낮아. 회복 물약 가격을 100골드에서 60골드로 내리고 적 체력을 15% 줄이면 될까? 현재 상점 방문 시 보유 골드는 평균 140이고, 절반의 플레이어는 물약을 사지 않아.

## Mandatory Checks

- Refuses to infer root cause from the given averages alone
- Lists competing hypotheses such as affordability, opportunity cost, comprehension, availability, build viability, and stage bias
- Requests or specifies segmented distributions rather than only means
- Defines required telemetry and controlled tests
- Changes one structural relationship at a time where possible
- Includes primary and guardrail metrics
- Provides an observation window or sample rule and revert threshold
- Labels any proposed number as a test hypothesis

## Strong Response Signals

- Examines currency distribution and purchasing power at each shop visit
- Checks whether non-buyers need healing or preserve gold for a more valuable sink
- Conditions win rate on stage, experience, account power, and build

## Failure Signals

- Applies both changes immediately and claims the target win rate will result
- Treats purchase rate or average gold as causal evidence
