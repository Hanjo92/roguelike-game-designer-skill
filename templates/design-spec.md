# [Feature or System Name] — Design Specification

## 1. Summary

**One-sentence goal:** [What player experience or design problem this feature addresses]

**Player fantasy:** [What the player feels or imagines they are doing]

**Status:** Draft

**Owners / dependencies:** [Design, engineering, art, audio, UI, narrative, QA]

## 2. Context and Constraints

- Genre and run format:
- Primary subgenre and secondary modifiers:
- Time, spatial, persistence, procedural-scope, and mastery profile:
- Host genre's primary skill:
- Roguelike adaptation layer:
- Platform and controls:
- Target audience:
- Session or floor length:
- Production constraints:
- Existing systems affected:
- Explicit non-goals:

## 3. Design Pillar Alignment

| Pillar | How this feature supports it | Evidence in playtest |
|---|---|---|
| [Pillar] | [Mechanism] | [Observable behavior] |

## 4. Player-Facing Rules

### Inputs and Preconditions

- [What must be true before the system activates]

### State

- [Persistent and temporary values]

### Rules

1. [Unambiguous rule]
2. [Unambiguous rule]

### Resolution Order

1. [First event]
2. [Second event]
3. [Cleanup]

### Information and Feedback

- Before choice:
- During resolution:
- After resolution:
- UI / VFX / SFX requirements:

## 5. Decision Design

| Choice | Known information | Uncertainty | Benefit | Cost / opportunity cost | Reversible? |
|---|---|---|---|---|---|
| [Choice] | [Known] | [Unknown] | [Benefit] | [Cost] | [Yes/No] |

## 6. Content Grammar

| Content | Role | Telegraph | Counterplay | Synergies | Anti-synergies |
|---|---|---|---|---|---|
| [Entry] | [Role] | [Signal] | [Response] | [Interactions] | [Conflicts] |

## 7. Level and Encounter Integration

- Room or topology requirements:
- Spawn constraints:
- Threat budget impact:
- Pacing role:
- Biome restrictions:
- Procedural-generation invariants:

## 8. Balance Model

**Baseline unit:** [turn, second, action, encounter, floor]

| Parameter | Initial hypothesis | Allowed range | Purpose / sensitivity |
|---|---:|---:|---|
| [Parameter] | [Value] | [Range] | [Why it matters] |

- Power budget:
- Resource sources and sinks:
- Scaling behavior:
- Diminishing returns or caps:
- Recovery and pity rules:

## 9. Edge Cases and Exploits

| Case | Expected behavior | Safeguard or test |
|---|---|---|
| Infinite or recursive trigger | [Behavior] | [Cap/order rule] |
| Save/load or disconnect | [Behavior] | [Persistence rule] |
| Missing required content | [Behavior] | [Fallback] |
| Dominant strategy | [Behavior] | [Trade-off/counter] |

## 10. Accessibility and Onboarding

- Tutorialization:
- Readability:
- Input accommodations:
- Color / audio alternatives:
- Difficulty assists and their boundaries:

## 11. Analytics and Playtest Plan

**Hypothesis:** [If the design works, players will…]

**Prototype:** [Cheapest testable version]

**Audience / sample:** [Who tests it]

**Metrics:**

- [Metric and expected range]

**Qualitative observations:**

- [Behavior or confusion to watch]

**Failure threshold:** [What result causes redesign]

## 12. Acceptance Criteria

- [ ] Core rule set is implemented and deterministic where specified
- [ ] Player can understand the decision before committing
- [ ] Major threats have telegraphs and counterplay
- [ ] Procedural invariants pass across representative seeds
- [ ] No known infinite, dominant, or progression-breaking interaction remains
- [ ] Initial balance falls within the declared test range
- [ ] Required UI, feedback, accessibility, and analytics hooks are present
- [ ] QA has reproducible seeds or scenarios for edge cases

## 13. Open Questions

- [Question, owner, and decision deadline]
