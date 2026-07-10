# Enemy, Boss, and Encounter Design Guide

Load this reference when designing or reviewing enemies, elite variants, bosses, encounter groups, spawn systems, threat budgets, combat rooms, waves, or mission objectives.

## 1. Begin with the Player Decision

An enemy exists to ask a question, not merely to absorb damage. Define:

- What should the player notice?
- What action or positioning decision should follow?
- What obvious response does the enemy punish?
- What alternative responses remain viable?
- How does terrain alter the answer?
- How does the enemy combine with other roles?

If the answer is only “deal enough damage,” the design needs another behavioral layer.

## 2. Enemy Role Grammar

| Role | Function | Common counterplay |
|---|---|---|
| Pressure | Forces movement or rapid resolution | Reposition, burst, control |
| Area denial | Makes zones unsafe | Route planning, displacement, patience |
| Control | Restricts movement, actions, or resources | Interrupt, cleanse, line of sight |
| Support | Buffs, heals, shields, or coordinates others | Target priority, separation |
| Disruption | Breaks established rhythm or targeting | Adapt timing, reserve resources |
| Punisher | Exploits a repeated behavior | Vary actions, bait and respond |
| Artillery | Projects delayed long-range danger | Close distance, cover, movement |
| Defender | Protects space or another unit | Flank, break guard, isolate |
| Summoner | Converts time into additional threats | Priority damage, interrupt, crowd control |
| Resource threat | Attacks currency, deck, light, oxygen, or another run resource | Prevention, fast objective, accept trade |
| Information threat | Hides, deceives, or changes prediction | Scouting, tells, environmental clues |

Individual enemies may combine two roles, but their primary question should remain readable.

## 3. Anatomy of an Enemy

Specify:

- Role and intended difficulty band
- Detection, awareness, and target selection
- Movement, navigation, preferred distance, and retreat behavior
- Attack phases: tell, commitment, active threat, recovery
- Damage, control, and status application
- Interrupt, stagger, armor, invulnerability, and resistance rules
- Counterplay and escape windows
- Terrain interactions
- Ally interactions and formation behavior
- Spawn restrictions
- Rewards and resource consequences
- Tuning knobs and AI state transitions
- Accessibility cues across visual, audio, and haptic channels

Use `templates/encounter-spec.md` for implementation-ready enemies and encounters.

## 4. Telegraph Budget

A telegraph must communicate enough of:

- Source
- Target or danger area
- Timing
- Severity
- Required response class

Reaction time should account for input latency, animation commitment, camera framing, visual clutter, target audience, and whether the attack is new. Harder versions may reduce margins or combine familiar patterns; they should not simply remove information.

Distinguish:

- **Recognition time:** identify the threat
- **Decision time:** choose a response
- **Execution time:** perform the response
- **Safety margin:** absorb normal variance

An attack is only fair if the available window covers the intended total under representative conditions.

## 5. Encounter Composition

Compose with a primary question and one modifier:

1. Select the spatial or tactical question.
2. Choose a primary role that forces action.
3. Add a secondary role that complicates—but does not invalidate—the obvious response.
4. Place terrain that changes routes or timing.
5. Provide counterplay, escape, or a spendable recovery option.
6. Add rewards or objectives that influence commitment.

Avoid combinations where one enemy requires constant movement while another requires standing still unless a third option is deliberately provided.

## 6. Threat Budget

Create a relative threat unit rather than relying only on health and damage. Price:

- Immediate lethality
- Area and duration
- Range and line-of-sight independence
- Mobility and pursuit
- Control severity
- Support multiplier
- Summoning potential
- Information burden
- Required target priority
- Synergy with terrain and allies

Encounter threat is not always additive. Apply a synergy multiplier to role combinations, constrained spaces, overlapping tells, or simultaneous timing.

A practical starting model:

```text
encounter_threat = sum(unit_threat × count)
                 × role_synergy
                 × terrain_pressure
                 × timing_overlap
                 × objective_pressure
```

Treat all coefficients as hypotheses. Calibrate against observed damage, resource spend, failure rate, and recovery time.

## 7. Spawn and Wave Rules

Define:

- Minimum player distance
- Allowed line of sight
- Entry telegraph and invulnerability behavior
- Maximum simultaneous active threat
- Spawn cadence and burst limits
- Replacement rules after kills
- Elite and support quotas
- Anti-repeat history
- Performance entity limits
- Behavior if no valid spawn point exists

Do not spawn a lethal threat where the player cannot perceive or respond to it. Waves should change the tactical question, not only increase count.

## 8. Elite Variants

An elite should remix a learned enemy with one clear modifier:

- New spatial constraint
- New timing
- Ally interaction
- Resource pressure
- Phase change
- Conditional defense

Preserve the base enemy's readable identity. Avoid stacking multiple affixes whose visual language conflicts. Define invalid affix-role and affix-room combinations.

## 9. Boss Design

A boss tests accumulated mastery and creates a memorable run climax.

### Boss Contract

Define:

- Mastery being tested
- Build checks and alternate solution classes
- Arena topology
- Phase transition conditions
- Checkpoints or restart cost
- Adds, hazards, and resource drops
- Enrage or anti-stall behavior
- Reward and post-boss pacing

### Phase Structure

Use phases to change decisions, not only stats:

1. **Teach:** expose the pattern with generous margins.
2. **Test:** combine familiar patterns and arena use.
3. **Transform:** introduce one rule change or positional reversal.
4. **Climax:** compress timing or increase overlap while preserving legibility.

Avoid immunity that invalidates a viable build. Use resistance, alternate targets, objective routes, consumable support, or conversion mechanics instead.

### Build Robustness

Test bosses against:

- Melee and ranged
- Burst and damage-over-time
- Fast fragile and slow durable builds
- Summons, control, status, and resource engines
- Low-roll but viable runs
- Accessibility assists

Every intended build family needs a way to make progress, survive, or convert its strength.

## 10. Encounter Progression

Use a sequence:

```text
Introduce one role → practice it → pair with a known role →
change terrain → add time/resource pressure → climax → recovery
```

Track role frequency, pair frequency, room recurrence, and time since last exposure. Procedural selection should preserve teaching order and prevent hostile combinations before players have seen their components.

## 11. Playtest and Analytics

Useful observations and metrics:

- Damage and deaths by source
- Recognition-to-response timing
- Avoidance rate after first exposure
- Target priority and time-to-priority-kill
- Resource spend by encounter
- Encounter duration distribution
- Failure rate conditional on build family
- Room position heatmaps
- Hits received during overlapping telegraphs
- Boss phase reached and phase-specific deaths
- Percentage of seeds containing the same role pair

Separate “did not understand” from “understood but failed execution” and “had no viable response.” They require different fixes.

## 12. Completion Criteria

An enemy or encounter is ready for implementation when its player question, role, states, telegraphs, counterplay, terrain and ally interactions, spawn constraints, threat budget, tuning knobs, accessibility cues, and test cases are explicit. A boss additionally needs phase contracts and representative-build validation.
