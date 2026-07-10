# [Item / Weapon / Relic Name] — Content Specification

## Identity

- Content type:
- Player-facing fantasy:
- Gameplay role:
- Rarity / acquisition band:
- Tags:
- Intended build families:
- Explicit non-goals:

## Player Decision

**Behavior this content should create:**

**Benefit:**

**Cost or opportunity cost:**

**When it is a strong choice:**

**When it is a weak choice:**

## Rules

### Preconditions and Input

- Acquisition prerequisites:
- Activation input or trigger:
- Resource cost:
- Cooldown / cadence:

### Effect

1. [Exact rule]
2. [Exact rule]

### Resolution Order

1. Validate trigger and ownership
2. Pay or reserve cost
3. Select targets
4. Apply primary effect
5. Apply secondary effects
6. Emit trigger events
7. Enforce caps and cleanup state

### Stacking and Recursion

- Duplicate behavior:
- Additive buckets:
- Multiplicative buckets:
- Stack cap:
- Trigger-per-action/frame/turn cap:
- Recursive-trigger rule:

## Weapon Profile, if applicable

| Parameter | Initial hypothesis | Tuning range |
|---|---:|---:|
| Damage |  |  |
| Startup |  |  |
| Active time |  |  |
| Recovery |  |  |
| Range |  |  |
| Area / target count |  |  |
| Resource cost |  |  |
| Movement during use |  |  |
| Stagger / control |  |  |

## Interaction Matrix

| System or tag | Expected interaction | Priority / edge case |
|---|---|---|
| Critical hits |  |  |
| Damage over time |  |  |
| Summons |  |  |
| Reflected / copied effects |  |  |
| Bosses |  |  |
| Zero-cost actions |  |  |

## Synergies and Counterweights

- Independent value:
- Soft synergies:
- Hard synergies:
- Hybrid bridges:
- Anti-synergies:
- Counterweight:
- Degenerate combination safeguards:

## Acquisition and Pool Rules

- Eligible pools:
- Earliest and latest appearance:
- Weight:
- Duplicate policy:
- Reroll / banish / salvage value:
- Drought or guarantee rules:

## Feedback and Accessibility

- UI text:
- Icon and color language:
- Animation / VFX:
- SFX / haptics:
- Activation feedback:
- Accessibility alternative:

## Production Dependencies

- Design:
- Engineering:
- Art / animation:
- VFX / audio:
- UI / localization:
- Analytics:
- QA interaction surface:

## Test Cases

- [ ] Base activation
- [ ] Early- and late-run acquisition
- [ ] Minimum and maximum stacks
- [ ] Multiple copies
- [ ] Boss and immune target
- [ ] Summon / reflected / copied source
- [ ] Save and load during active state
- [ ] Trigger storm and recursion cap
- [ ] Representative weak, median, and strong builds
- [ ] Feedback remains readable under heavy combat load

## Balance Hypothesis

- Baseline unit:
- Expected value or DPS band:
- Parameters with highest sensitivity:
- Success metrics:
- Failure / revert threshold:
