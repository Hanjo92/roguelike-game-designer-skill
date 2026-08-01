# Roguelike Balance and Economy Guide

Load this reference when balancing combat numbers, progression, rewards, shops, currencies, rarity, scaling, run economy, meta-progression, or difficulty curves.

## 1. Balance Is a Relationship

Do not assign isolated values. Define a baseline unit appropriate to the subgenre:

- Turn or action for traditional and tactical games
- Second, attack cycle, or dodge window for action games
- Draw, energy, or combat turn for deckbuilders
- Upgrade interval or wave minute for survivors-likes
- Day, mission, or production cycle for strategy hybrids

Then define target relationships among player output, enemy threat, resource income, costs, and recovery.

Use `templates/balance-model.md` to record assumptions and formulas.

### 1.1 Define the Balance Contract

“Balanced” is not a complete target. Before tuning, state what kind of balance the game promises:

- **Target population and context:** which experience bands, account-power states, difficulty tiers, modes, and run stages the decision concerns
- **Protected experience:** the fantasy, primary skill, risky strategy, accessibility option, or subgenre asymmetry that tuning must preserve
- **Intended asymmetry:** which choices may be easier, safer, rarer, more complex, or higher ceiling without being equal in every metric
- **Mastery gradient:** how novice, median, and expert outcomes should differ, and where execution or knowledge should matter
- **Acceptable variance:** target distribution and tail limits for weak rolls, strong rolls, matchup extremes, and procedural outliers
- **Dominance boundary:** how much advantage, usage concentration, or solution coverage becomes unacceptable, and over what observation window
- **Evidence rule:** which behavioral measures and player-reported perceptions can trigger, block, or revert a change

Do not substitute aggregate parity for this contract. Equal global win or pick rates can still hide an onboarding failure, one invalidated build family, inaccessible execution demands, or opposite problems in novice and expert play. Conversely, unequal rates can be intentional when choices differ in complexity, risk, acquisition timing, or audience.

Use player reports to identify perceived fairness, clarity, and satisfaction, then connect those reports to matched behavioral context. Neither telemetry nor opinion alone identifies the cause. State whether evidence is observational, controlled, or causal, and keep stakeholder preference distinct from measured player behavior.

## 2. Core Combat Model

Track at least:

```text
raw_dps = damage_per_hit × attacks_per_second × hit_probability × target_uptime
expected_dps = raw_dps × crit_factor × resistance_factor × condition_uptime

effective_health = health / expected_damage_multiplier

time_to_kill = enemy_effective_health / expected_dps

damage_taken_per_encounter = incoming_threat × exposure_time × failure_probability
```

For turn-based systems replace time with actions. Include overkill, area coverage, reload or setup time, range, safety, and control as power—not only raw damage.

Define target bands rather than exact universal values. Compare weak, median, and strong viable builds.

## 3. Power Budget

Price advantages in a common relative budget:

- Damage and scaling
- Reliability and target uptime
- Area and target count
- Range and safety
- Mobility during use
- Control and interruption
- Defense and recovery
- Resource generation
- Flexibility across encounters
- Low execution or cognitive burden

A flexible item should usually have lower peak efficiency than a narrow specialist. A risky or conditional effect may have higher ceiling only if the condition is meaningful in real play.

## 4. Growth Curves

Common curves:

| Curve | Formula shape | Good use | Risk |
|---|---|---|---|
| Linear | `a + bx` | Predictable baseline growth | Becomes flat against multiplicative systems |
| Diminishing | `a + b√x` or capped ratio | Defense, cooldown, rerolls | Can make upgrades feel weak |
| Exponential | `a × r^x` | Short controlled escalation | Rapid runaway |
| Logistic | bounded S-curve | Accuracy, resistance, account catch-up | Less intuitive |
| Piecewise | authored bands | Floors, acts, rarity tiers | Discontinuities and exploits |

Avoid multiplying many unrestricted growth axes. Decide which modifiers are additive within a bucket and multiplicative across buckets. Document order of operations.

Use caps, diminishing returns, opportunity costs, encounter counters, and run-length limits intentionally—not as unexplained emergency patches.

## 5. Economy Model

For each resource define:

| Field | Meaning |
|---|---|
| Sources | Where and how often it enters |
| Sinks | What removes it |
| Stock | Typical amount held by run stage |
| Flow | Income and spend per baseline unit |
| Carry limit | Hard, soft, or none |
| Conversion | Exchange rates and loss |
| Decision purpose | What trade-off it creates |
| Failure state | What happens at zero or surplus |
| Recovery | How droughts can be repaired |

Merge resources that create the same decision. Separate resources only when their timing, risk, ownership, or strategic purpose differs.

### Flow Equation

```text
net_flow(stage) = guaranteed_income
                + expected_optional_income
                - required_spend
                - expected_discretionary_spend
```

Model variance and drought length, not only average flow. Averages can hide runs where a required resource never appears.

## 6. Rewards and Shops

Reward value includes:

- Immediate power
- Future scaling
- Flexibility and option value
- Information
- Recovery
- Currency or conversion value
- Opportunity cost of skipped alternatives

For shops define:

- Visit timing and frequency
- Offer count and pool
- Price curve by stage and rarity
- Sell, salvage, reroll, lock, reserve, or debt rules
- Guaranteed utility or recovery slots
- Anti-arbitrage rules
- Context sensitivity and its limits

A good shop does not merely test whether the player saved enough. It creates competing uses for scarce value.

## 7. Loot and Rarity

Control expected value:

```text
expected_reward_value = Σ(probability_i × utility_i_given_state)
```

Utility depends on the current build. Track both global and conditional value.

Use guarantees and pity systems for:

- Critical build enablers
- Healing or repair
- Ammunition or deck maintenance
- Minimum shop purchasing power
- Required keys or traversal tools

Do not guarantee the exact optimal build. Guarantee continued agency.

## 8. Run and Difficulty Curve

Segment a run into authored bands such as opening, formation, specialization, stress test, and climax.

For each band record:

- Expected player power range
- Enemy threat range
- Resource stock and flow
- Build completeness
- Decision complexity
- Recovery availability
- Required mastery

Difficulty can rise through threat combinations, tempo, spatial restriction, resource pressure, consequence, information burden, or execution precision. Avoid relying solely on health and damage inflation.

Track when a run becomes practically unwinnable. Provide recovery paths or end the run promptly rather than demanding prolonged doomed play.

## 9. Meta-Progression Economy

Separate:

- Account currency
- Permanent power
- Option unlocks
- Difficulty modifiers
- Cosmetics and narrative rewards

Measure baseline viability before upgrades. A first run should demonstrate the real game rather than function as a mandatory grind tutorial.

Useful controls:

- Bounded permanent power
- Horizontal unlocks
- Catch-up multipliers
- Duplicate protection
- Refund or respec
- Difficulty systems that compensate for account power
- Separate prestige sinks after functional progression

## 10. Simulation and Sensitivity

Before content-scale playtesting:

1. Build a spreadsheet or small simulation.
2. Run weak, median, and strong assumptions.
3. Vary one input at a time.
4. Inspect distributions and worst cases.
5. Identify parameters with disproportionate effect.
6. Add automated invariant checks.

Useful invariants:

- No legal starting state is immediately unwinnable
- Required resources meet minimum guarantees
- No upgrade exceeds declared stack or recursion caps
- Shop arbitrage cannot create infinite currency
- Representative builds fall within target TTK bands
- Permanent power stays within the intended account-power bound

Simulation validates arithmetic and distributions, not fun, comprehension, or emotional pacing.

## 11. Metrics and Interpretation

Track:

- Win rate by experience and account-power band
- TTK and damage taken distributions
- Pick, skip, replacement, and sell rates
- Currency earned, held, and unspent at death
- Shop purchase and reroll behavior
- Resource drought length
- Build concentration and conditional performance
- Death source and stage
- Recovery frequency after falling below target power
- Player-reported fairness, clarity, and satisfaction joined to the relevant encounter, build, run stage, and experience band

Avoid common false conclusions:

- High pick rate does not alone prove overpowered
- High win rate after acquisition may reflect late acquisition
- Average currency does not reveal starvation tails
- Global item performance hides archetype dependence
- Expert balance does not imply accessible onboarding

## 12. Change Discipline

For each balance change record:

- Problem and evidence
- Target behavior
- Changed variable
- Expected side effects
- Segments most affected
- Metric and observation window
- Revert threshold

Change one structural relationship at a time when possible. Do not simultaneously alter player power, enemy threat, reward rate, and shop price if the goal is to identify a cause.

## Completion Criteria

A balance proposal is ready to test when its balance contract, affected segments, baseline unit, formulas, target bands, power budget, economy sources and sinks, variance guarantees, scaling order, difficulty stages, sensitive parameters, exploit checks, behavioral and perception evidence, and success metrics are explicit. All initial numbers must be labeled as hypotheses until validated.
