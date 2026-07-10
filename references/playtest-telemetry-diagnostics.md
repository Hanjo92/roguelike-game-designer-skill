# Playtesting, Telemetry, and Design Diagnosis Guide

Load this reference when planning tests, defining telemetry, diagnosing balance or fairness problems, interpreting player behavior, comparing builds, or deciding whether a change worked.

## 1. Start with a Decision, Not Data Collection

Before logging an event or running a test, state:

- Design question
- Current evidence
- Competing explanations
- Decision that will change based on the result
- Minimum data needed
- Player segment and run context
- Success, failure, and inconclusive thresholds

Do not collect data merely because it is available. Every metric should support a decision or validate an invariant.

## 2. Diagnosis Funnel

Use this sequence:

```text
Symptom
→ affected segment and run stage
→ first divergence from healthy play
→ local cause
→ upstream structural cause
→ smallest intervention
→ predicted side effects
→ validation window and revert threshold
```

Example: “Boss win rate is low” is a symptom. Possible causes include unreadable telegraphs, insufficient build repair, one invalidated archetype, resource starvation before the boss, excessive restart cost, or a numeric outlier.

## 3. Separate Failure Classes

| Failure class | Evidence | Typical response |
|---|---|---|
| Comprehension | Player cannot state rule or danger | Improve teaching, cues, terminology |
| Recognition | Player knows rule but misses cue | Improve contrast, timing, camera, audio |
| Decision | Player sees threat but chooses poorly | Clarify trade-offs or accept skill test |
| Execution | Correct choice, failed input/timing | Tune window, controls, assist, or difficulty |
| Resource | No viable response due to prior economy | Add guarantees, repair, route options |
| Build viability | Archetype cannot pass required check | Add alternate solution or revise check |
| Procedural invalidity | Seed creates impossible/unfair state | Add invariant, repair, or exclusion |
| Pacing | Fatigue, boredom, or abrupt spike | Change beat sequence or duration |
| Motivation | Player understands but does not care | Improve reward, fantasy, goal, consequence |
| Technical | Bug, latency, frame time, save issue | Fix implementation before design inference |

Never solve a comprehension failure with a stat nerf or an economy failure with a longer dodge window.

## 4. Test Ladder

Use the cheapest test that can answer the question:

1. **Paper or table test:** rules, economy, card flow, route choices
2. **Graybox:** movement, geometry, encounter timing, telegraphs
3. **Controlled scenario:** fixed build, seed, room, and player task
4. **Seed batch or simulation:** distributions, invariants, economy tails
5. **Internal exploratory test:** unexpected interactions and usability
6. **Targeted external test:** comprehension and audience fit
7. **Broad telemetry test:** real distributions and retention behavior

Do not use broad A/B testing to avoid understanding a broken rule.

## 5. Playtest Protocol

Define:

- Hypothesis and competing hypotheses
- Participant segment and experience
- Build, seed, account state, and difficulty
- Tasks and allowed help
- Think-aloud policy
- Observer prompts that avoid leading
- Quantitative events
- Qualitative observations
- Stop conditions
- Debrief questions

Separate observation from interpretation. “Player opened inventory six times” is observation; “inventory is confusing” is a hypothesis.

Use `templates/playtest-plan.md`.

## 6. Telemetry Event Design

An event should include:

- Stable event name and schema version
- Anonymous player/session/run identifiers
- Sequence number and timestamp
- Game/content/build version
- Seed and generation version when relevant
- Run stage, room, biome, and difficulty
- Account progression band
- Current build tags and important resources
- Event-specific payload
- Cause/source identifiers

Use `templates/telemetry-events.md` to define the event catalog.

### Minimum Run Funnel

```text
run_started
node_offered
node_selected
room_entered
encounter_started
reward_offered
reward_selected_or_skipped
resource_changed
shop_action
build_state_changed
player_damaged
encounter_ended
boss_phase_reached
run_ended
restart_or_exit
```

Log enough context to reconstruct decisions without logging sensitive personal information or every frame.

## 7. Required Event Semantics

Define precisely:

- When the event fires
- Whether retries can duplicate it
- Whether values are before or after the change
- Source and target ownership
- How chained events are attributed
- How save/load and resume affect sequence
- Whether offline events are buffered
- Schema migration behavior

For resource changes, log delta, resulting balance, source, sink category, and reason. For rewards, log all offered choices, weights if permissible for development data, selection, skip, reroll, and current build context.

## 8. Segmentation

Always inspect metrics by relevant segments:

- First-time, learning, experienced, and expert players
- Account-power or unlock band
- Difficulty modifier
- Input method and platform
- Build family and hybrid tags
- Character, weapon, or starting loadout
- Run stage and seed-generation version
- Accessibility options when consent and policy permit

Global averages can hide a broken onboarding experience or one dominant expert build.

## 9. Survival and Timing Bias

Avoid common analytical errors:

- Items acquired late appear to have high win rate because only strong runs reach them
- Boss metrics exclude players who quit before the boss
- Long runs contribute more events than short runs
- Expert players select difficult content, reversing apparent difficulty effects
- New content benefits from novelty and expert experimentation
- Account power correlates with both strength and experience

Use acquisition-floor conditioning, stage-matched comparisons, player fixed effects where appropriate, and controlled scenarios before claiming causality.

## 10. Build and Item Analysis

Track:

- Offer, pick, skip, reroll, sell, and replacement rates
- Acquisition stage
- Activation frequency and wasted triggers
- Damage, defense, control, economy, and utility contribution
- Win rate conditioned on acquisition stage and prior run strength
- Build tag co-occurrence
- Pair and trio performance with minimum sample thresholds
- Archetype concentration and entropy
- Dead reward frequency

Do not rank items using win rate alone. Combine power, availability, flexibility, clarity, and fun observations.

## 11. Encounter and Boss Analysis

Track:

- Entry state and resource stock
- Damage/death by source
- Recognition-to-response time
- Target priority
- Encounter duration
- Resource spend
- Position heatmaps
- Phase reached
- Build-family result
- Seed, room, and modifier combination

Distinguish “understood but failed” from “no viable response.” Review video or controlled replay for high-impact failures.

## 12. Economy and Run Analysis

Track distributions of:

- Currency earned, spent, held, and lost
- Shop purchasing power at each visit
- Reward and healing drought length
- Build identity and specialization timing
- Power/threat estimates by stage
- Recovery events after falling below target
- Practical irrecoverability and time played afterward
- Route selection and reward realization

Tail behavior matters. A healthy mean can coexist with unacceptable starvation seeds.

## 13. Procedural Generation Analysis

Join run outcomes with:

- Master seed and generation version
- Topology metrics
- Room-role sequence
- Threat and reward spacing
- Repair and retry logs
- Content repetition
- Performance cost

First determine whether a result is a design issue, content issue, generator constraint issue, or rare invalid seed.

## 14. Qualitative Coding

Tag observations consistently:

- Confusion
- Surprise
- Frustration
- Boredom
- Delight
- Perceived unfairness
- Strategic regret
- Interface friction
- Missing feedback
- Desired behavior achieved

Record evidence and context, not only sentiment. A frustrated player may still value a fair high-stakes decision.

## 15. Prioritization

Score findings by:

```text
priority = severity × frequency × confidence × affected_population
           ÷ estimated_fix_cost
```

Do not let this formula override critical progression blockers, accessibility failures, data loss, or severe unfairness. Use it to structure judgment.

## 16. Change Validation

For each change define:

- Target behavior
- Primary metric
- Guardrail metrics
- Most affected segments
- Expected time to signal
- Minimum sample or qualitative evidence
- Side effects
- Revert threshold

Prefer controlled scenario comparison for local mechanics and broader telemetry for ecosystem effects. A change can improve the primary metric while harming build diversity, run duration, comprehension, or difficulty identity.

## 17. Reporting

A useful report contains:

1. Decision and hypothesis
2. Test context and limitations
3. Key evidence with segment and stage
4. Root-cause chain
5. Confidence level
6. Recommended smallest intervention
7. Expected side effects
8. Follow-up test and revert threshold

Label correlation, controlled evidence, and causal claims distinctly.

## Completion Criteria

A test or telemetry plan is ready when it names the decision, hypotheses, segments, controlled context, event semantics, success and guardrail metrics, qualitative observations, bias risks, sample or confidence rule, diagnosis path, and action threshold. A finding is not complete until it identifies the smallest useful intervention and how to verify it.
