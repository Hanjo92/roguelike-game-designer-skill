# [Enemy / Boss / Encounter Name] — Specification

## Purpose

- Content type:
- Player question:
- Primary role:
- Secondary role, if any:
- Difficulty and run-stage band:
- Intended emotional beat:
- Explicit non-goals:

## Required Player Information

- Threat source cue:
- Target / danger-area cue:
- Timing cue:
- Severity cue:
- Expected response classes:
- Accessibility alternatives:

## Enemy State Model

| State | Entry condition | Behavior | Exit condition | Interruptible? |
|---|---|---|---|---|
| Idle / patrol |  |  |  |  |
| Detect / prepare |  |  |  |  |
| Attack |  |  |  |  |
| Recovery |  |  |  |  |
| Stagger / disabled |  |  |  |  |
| Retreat / reposition |  |  |  |  |
| Death / phase change |  |  |  |  |

## Attack Specification

| Attack | Tell | Commitment | Active threat | Recovery | Range / area | Counterplay |
|---|---:|---:|---:|---:|---|---|
|  |  |  |  |  |  |  |

- Target selection:
- Tracking behavior:
- Line-of-sight rule:
- Damage / status:
- Cooldown and repeat prevention:
- Animation cancellation rule:

## Movement and Navigation

- Preferred distance:
- Speed / turn rate:
- Pathing and obstacle handling:
- Leash / pursuit:
- Formation behavior:
- Terrain interactions:
- Behavior when no valid path exists:

## Defense and Control

- Health / effective health target:
- Armor / resistance:
- Stagger / poise:
- Interrupt rules:
- Immunities and alternatives:
- Recovery opportunities granted to player:

## Encounter Composition

- Spatial question:
- Primary and secondary threats:
- Terrain modifier:
- Objective pressure:
- Escape or recovery option:
- Invalid enemy combinations:
- Invalid room tags:

## Threat Budget

| Component | Relative threat | Notes |
|---|---:|---|
| Base unit |  |  |
| Role synergy |  |  |
| Terrain pressure |  |  |
| Timing overlap |  |  |
| Objective pressure |  |  |
| Total target band |  |  |

## Spawn Rules

- Minimum player distance:
- Line-of-sight requirement:
- Entry cue and delay:
- Simultaneous cap:
- Role / elite quota:
- Spawn cadence:
- Invalid-position fallback:
- Performance budget:

## Boss Phases, if applicable

| Phase | Mastery test | New decision | Transition | Resource support |
|---|---|---|---|---|
| Teach |  |  |  |  |
| Test |  |  |  |  |
| Transform |  |  |  |  |
| Climax |  |  |  |  |

- Arena topology:
- Anti-stall rule:
- Build-family alternatives:
- Checkpoint / restart cost:
- Post-boss reward and recovery:

## Tuning Knobs

| Parameter | Initial hypothesis | Allowed range | Sensitivity |
|---|---:|---:|---|
|  |  |  |  |

## Production Dependencies

- AI / engineering:
- Animation:
- VFX / audio:
- Environment:
- UI / localization:
- Analytics:
- QA:

## Acceptance Tests

- [ ] Threat can be recognized, decided on, and answered inside the intended window
- [ ] Spawn never creates unavoidable immediate damage
- [ ] Counterplay works in representative rooms
- [ ] Invalid role and room combinations are excluded
- [ ] Weak but viable builds can make progress
- [ ] Strong builds do not skip every intended decision
- [ ] Overlapping telegraphs remain readable
- [ ] State transitions and interruption rules are deterministic
- [ ] Boss phases support all intended build families
- [ ] Metrics distinguish misunderstanding, execution failure, and missing counterplay
