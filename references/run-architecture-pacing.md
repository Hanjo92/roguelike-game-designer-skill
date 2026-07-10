# Run Architecture, Pacing, and Director Guide

Load this reference when designing the structure of a complete run, act, floor sequence, biome order, reward cadence, difficulty rhythm, recovery opportunities, or adaptive run director.

## 1. Define the Run Contract

Before arranging rooms or rewards, specify:

- Target run length and acceptable range
- Number and purpose of acts, floors, missions, waves, or days
- Expected restart cost and time to return to meaningful play
- Primary skill practiced throughout the run
- When a build first forms, specializes, and reaches its climax
- Required mastery at the beginning and end
- What the player knows about future routes and threats
- What failure should teach
- Which guarantees make every legal seed viable

A run contract is complete when a tester can distinguish a slow but healthy run from a run that is structurally behind.

## 2. Use a Run Arc

A general-purpose arc:

| Stage | Player state | Main decisions | Design obligation |
|---|---|---|---|
| Orientation | Basic kit, low information | Learn controls and local rules | Fast agency, low restart friction |
| Formation | Several viable directions | Choose tools, route, and risk | Offer real alternatives and repair variance |
| Commitment | Emerging build identity | Specialize or preserve flexibility | Make opportunity cost visible |
| Stress test | Functional but incomplete build | Spend resources and address weakness | Test without requiring one exact answer |
| Transformation | New biome, rule, or power tier | Re-evaluate learned strategy | Change decisions rather than only stats |
| Climax | Mature build under maximum pressure | Execute and adapt | Validate accumulated mastery fairly |
| Resolution | Win, loss, extraction, or transition | Interpret outcome and choose next goal | Explain consequence and restart cleanly |

Not every game needs all stages, but each stage that exists must create a distinct class of decisions.

## 3. Work at Three Pacing Scales

### Micro: seconds, turns, or actions

Control attack cadence, decision time, recovery windows, animation commitment, draw rhythm, and immediate feedback.

### Meso: room, encounter, wave, or mission

Control threat composition, objective pressure, resource expenditure, reward, and transition time.

### Macro: act, biome, chapter, or entire run

Control build formation, rule introduction, difficulty bands, route structure, economy, bosses, and narrative progression.

A pacing fix at one scale may damage another. Shorter combat can improve micro pacing while making a floor's reward cadence too dense. Always name the scale being changed.

## 4. Build a Beat Grammar

Tag run nodes with a functional beat:

- Teach
- Practice
- Test
- Escalate
- Choice
- Risk
- Tax
- Recovery
- Reward
- Transformation
- Spectacle
- Climax
- Resolution

Define legal sequences and spacing rules. Example:

```text
Teach → Practice → Choice → Test → Reward
Known Test + New Modifier → Recovery → Escalation → Climax
```

Avoid long unbroken chains of the same beat. “Combat” is content type; “test,” “tax,” or “recovery opportunity” describes its pacing function.

## 5. Reward Cadence and Build Formation

Record target windows for:

- First meaningful choice
- First build enabler
- First opportunity to reject or repair a direction
- First shop or conversion point
- First defensive or recovery tool
- Build identity threshold
- Specialization payoff
- Final upgrade or pre-climax preparation

A reward cadence must consider decision density. Frequent low-impact choices create menu fatigue; rare high-impact choices create excessive variance. Combine minor upgrades when they do not change behavior.

Use guarantees for continued agency, not for the exact optimal build. Bound droughts for healing, ammunition, card removal, traversal tools, or other resources required by the chosen subgenre.

## 6. Difficulty and Power Curves

Plot ranges, not single lines:

- Weak viable player power
- Median player power
- Strong realistic player power
- Base threat
- Encounter outlier limit
- Recovery capacity

The threat curve may cross the median power curve at intended stress tests, but weak viable runs need alternate solutions: route avoidance, consumables, objectives, conversion, retreat, or skillful play.

Escalate through:

- New threat roles
- Familiar role combinations
- Timing overlap
- Spatial restriction
- Objective or resource pressure
- Information burden
- Consequence severity
- Execution precision

Use health and damage scaling to preserve baseline relevance, not as the sole source of difficulty.

## 7. Acts, Biomes, and Transformations

Each act or biome should define:

- Mechanical identity
- New rule or interaction
- Returning rule viewed in a new context
- Enemy-role emphasis
- Spatial grammar
- Economy modifier
- Build families favored or challenged
- Landmark and boss test
- Transition and recovery policy

A biome is not complete if its identity disappears when art and music are removed.

Act transitions may reset pressure, alter resource conversion, introduce new pools, or change route topology. Explain these changes before they can invalidate a run.

## 8. Route Architecture

For each branch show:

- Information available before choosing
- Expected threat and uncertainty
- Reward class
- Opportunity cost
- Reconnection point
- Escape or recovery possibility

Routes should create different plans, not merely different room colors. Use branch length and reconnection to control commitment. Deep branches support specialization; frequent reconnection supports adaptation.

Prevent dominant routing by varying current-state utility rather than hiding all information. If one route is always optimal, alter costs, reward categories, future access, or run-state dependencies.

## 9. Recovery and Irrecoverable States

Define a **recovery budget** for each stage:

- How far below target power a run may fall
- Which tools repair health, economy, deck quality, equipment, or squad losses
- What skill or risk recovery demands
- Maximum time spent in a nearly doomed state

Detect practical irrecoverability using combinations of power deficit, resource stock, available route options, and mandatory future checks. Do not silently force the player through twenty minutes of predetermined loss.

Possible responses:

- Offer a costly stabilization route
- Convert surplus resources
- Reveal an extraction or partial-success option
- Reduce future reward ceiling in exchange for survival
- End the run promptly with clear feedback

Avoid invisible adaptive mercy that makes decisions meaningless.

## 10. Run Director Boundaries

A director may select or weight upcoming encounters, rewards, pacing beats, or recovery opportunities based on run history. Define what it can observe and modify.

### Safe inputs

- Recent room roles
- Damage and resource trajectory
- Reward drought length
- Build tags and missing solution classes
- Repetition history
- Run stage and elapsed time
- Performance budget

### Safe interventions

- Enforce minimum or maximum spacing
- Select among equivalent threat-budget encounters
- Bound reward droughts
- Avoid invalid counters to a build with no alternative response
- Insert authored recovery candidates
- Reduce repetition

### Dangerous interventions

- Secretly negate good play
- Always hand out the perfect synergy
- Scale every enemy directly to current player power
- Punish high skill until all runs feel identical
- Rewrite outcomes after commitment
- Create fake route choices

Log director decisions and expose enough regularity that the game remains learnable.

## 11. Director Model

A simple selection score:

```text
candidate_score = base_weight
                + pacing_fit
                + novelty_value
                + biome_fit
                + run_state_fit
                - repetition_penalty
                - invalid_counter_penalty
                - budget_violation
```

Hard constraints must be evaluated before weighted preferences. Never use scoring to permit unreachable, unfair, or progression-breaking content.

Keep separate random streams for topology, pacing roles, encounters, rewards, and decoration so debugging one layer does not perturb every other layer.

## 12. Run-Length Profiles

### Short run: 5–15 minutes

- First meaningful choice within moments
- Fast build identity
- Minimal downtime and shallow meta overhead
- Few but distinct transformations
- Failure feedback must be immediate

### Session run: 20–60 minutes

- Multiple build repair points
- Clear acts or difficulty bands
- At least one transformation before climax
- Recovery must preserve agency without erasing mistakes

### Long or multi-session run

- Stable save and deterministic resume
- Mid-run goals and recaps
- Attrition with recoverable setbacks
- Stronger protection against late hidden invalidation
- Failure rewards must respect time investment

## 13. Instrumentation

Track:

- Time to first decision, enabler, build identity, and specialization
- Time in room and transition states
- Beat sequence and repeated beat runs
- Threat and power estimates by stage
- Reward and recovery droughts
- Route choice and regret indicators
- Director interventions
- Point of practical irrecoverability
- Time played after irrecoverability
- Quit, death, restart, and extraction timing

## 14. Run Review

For representative seeds ask:

- Did the opening reach meaningful play quickly?
- When did the build become identifiable?
- Was there at least one repair opportunity?
- Did acts change decisions?
- Were difficulty spikes preceded by information and preparation?
- Did recovery require a trade-off?
- Did the director preserve uncertainty without feeling manipulative?
- Could a weak viable run finish through a different solution class?
- Did the climax test learned mastery rather than a hidden requirement?

## Completion Criteria

A run architecture is ready to prototype when it defines the run contract, stage arc, pacing grammar, reward and build milestones, power/threat bands, route information, recovery budget, biome transformations, director boundaries, hard invariants, instrumentation, and representative-seed tests.
