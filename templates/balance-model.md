# [System / Run] — Balance Model

## 1. Goal and Scope

- Design problem:
- Subgenre and run format:
- Player segment:
- Run stage(s):
- Systems included:
- Systems excluded:
- Evidence motivating the change:

## 2. Baseline Unit

- Unit: [turn / action / second / attack cycle / encounter / wave / day]
- Baseline player state:
- Weak viable state:
- Strong realistic state:
- Baseline enemy or challenge:

## 3. Target Bands

| Metric | Weak viable | Median | Strong realistic | Failure boundary |
|---|---:|---:|---:|---:|
| Damage / output per unit |  |  |  |  |
| Time or actions to kill |  |  |  |  |
| Damage taken per encounter |  |  |  |  |
| Resource spend per encounter |  |  |  |  |
| Reward value per encounter |  |  |  |  |
| Recovery time |  |  |  |  |

## 4. Formula and Order of Operations

```text
raw_output =
conditional_output =
expected_output =
effective_health =
time_or_actions_to_kill =
```

Order:

1. Base value
2. Additive modifiers within buckets
3. Multiplicative buckets
4. Resistance / mitigation
5. Caps, minimums, and rounding
6. Triggered or conditional effects

- Rounding rule:
- Tick / frame / turn timing:
- Overflow behavior:

## 5. Power Budget

| Property | Relative cost | Reason |
|---|---:|---|
| Raw output |  |  |
| Reliability |  |  |
| Area / target count |  |  |
| Range / safety |  |  |
| Mobility |  |  |
| Control |  |  |
| Defense / recovery |  |  |
| Flexibility |  |  |
| Low execution burden |  |  |

## 6. Economy Ledger

| Resource | Sources / stage | Sinks / stage | Typical stock | Drought bound | Surplus control | Decision purpose |
|---|---|---|---:|---:|---|---|
|  |  |  |  |  |  |  |

### Conversion Rates

| From | To | Rate / loss | Limits | Arbitrage check |
|---|---|---:|---|---|
|  |  |  |  |  |

## 7. Run Curve

| Stage | Player power band | Threat band | Resource state | Build state | Recovery | Primary test |
|---|---|---|---|---|---|---|
| Opening |  |  |  |  |  |  |
| Formation |  |  |  |  |  |  |
| Specialization |  |  |  |  |  |  |
| Stress test |  |  |  |  |  |  |
| Climax |  |  |  |  |  |  |

## 8. Variance and Guarantees

- Minimum required reward:
- Maximum drought length:
- Pity / history-aware rule:
- Recovery opportunity:
- Reroll / skip / convert options:
- Worst legal state:
- Practically unwinnable-state handling:

## 9. Scaling and Caps

| Parameter | Curve | Cap / diminishing return | Intended range | Exploit risk |
|---|---|---|---|---|
|  |  |  |  |  |

- Additive buckets:
- Multiplicative buckets:
- Recursive trigger cap:
- Infinite-loop prevention:

## 10. Sensitivity Test

| Variable | -20% result | Baseline | +20% result | Sensitivity | Decision |
|---|---:|---:|---:|---|---|
|  |  |  |  |  |  |

## 11. Invariants

- [ ] No legal starting state is immediately unwinnable
- [ ] Representative builds remain in target bands
- [ ] Required resource guarantees hold
- [ ] No infinite currency conversion or shop arbitrage
- [ ] Stack and trigger caps hold
- [ ] Permanent power remains within its declared bound
- [ ] The run does not demand prolonged play after becoming unrecoverable

## 12. Playtest and Analytics

- Hypothesis:
- Prototype:
- Metrics:
- Qualitative observations:
- Segmentation:
- Sample size / duration:
- Success range:
- Failure / revert threshold:

## 13. Change Log Entry

- Variable changed:
- Old and new value:
- Expected behavior change:
- Expected side effects:
- Most affected segments:
- Review date or observation window:
