# Item, Weapon, and Relic Design Guide

Load this reference when creating or reviewing weapons, cards, skills, relics, artifacts, consumables, equipment, blessings, upgrades, or other run-build content.

## 1. Start with the Build Grammar

Do not begin with a list of themed effects. Define how content participates in a shared grammar:

| Role | Function | Typical question |
|---|---|---|
| Enabler | Makes a strategy possible | What new behavior becomes viable? |
| Trigger | Defines when an effect occurs | Can the player deliberately activate it? |
| Generator | Produces a resource, stack, unit, card, or state | What limits its output? |
| Converter | Exchanges one resource or property for another | What is sacrificed? |
| Modifier | Changes targeting, timing, shape, cost, or delivery | Does this alter play or only numbers? |
| Scaler | Grows with a readable variable | Is scaling bounded and reachable? |
| Payoff | Rewards commitment to a pattern | Is it useful before the perfect build? |
| Stabilizer | Repairs weakness or variance | Does it erase the weakness entirely? |
| Utility | Adds movement, control, information, economy, or defense | What opportunity cost keeps it meaningful? |
| Risk amplifier | Raises both danger and reward | Can the player evaluate and opt into the risk? |

A healthy pool contains independent tools, soft synergies, build enablers, and a limited number of high-commitment payoffs.

## 2. Specify Every Content Entry

For each item, weapon, or relic define:

- **Player promise:** the fantasy and behavior it creates
- **Role and tags:** standardized semantic labels used by systems and content
- **Acquisition context:** where, when, and how often it appears
- **Inputs and trigger:** events, state, costs, cooldowns, and prerequisites
- **Effect and resolution order:** exact behavior, including multi-target and repeated triggers
- **Feedback:** UI, animation, sound, controller response, and combat readability
- **Counterweight:** cost, condition, exposure, opportunity cost, or weakness
- **Synergies:** intended interactions that deepen the behavior
- **Anti-synergies:** conflicts that create adaptation rather than dead rewards
- **Tuning knobs:** values designers may change without rewriting the rule
- **Caps and recursion:** stack limits, trigger limits, and infinite-loop protection
- **Edge cases:** bosses, summons, environmental damage, zero-cost actions, save/load, and multiplayer if relevant
- **Production dependencies:** art, VFX, SFX, UI, localization, analytics, and QA burden

Use `templates/item-spec.md` for implementation-ready entries.

## 3. Design Weapons as Decision Packages

A weapon should express more than damage per second. Define its profile across:

- Range and coverage shape
- Startup, active time, recovery, and cadence
- Aim or targeting burden
- Movement allowed during use
- Resource and reload model
- Hit confirmation and stagger/control
- Safety, reliability, and overkill loss
- Single-target versus crowd performance
- Scaling hooks and status interactions
- Skill floor and skill ceiling

Price hidden power. Range, reliability, area, mobility, invulnerability, automation, and low cognitive load all consume power budget even when raw damage is unchanged.

A weapon variant is justified when it changes positioning, timing, target priority, resource rhythm, or build direction. A stat-only variant should usually be an upgrade tier, affix, or tuning change instead of a separate content entry.

## 4. Design Relics and Passive Effects

Strong passive design changes future decisions. Prefer effects such as:

- “After moving through an enemy, the next attack…”
- “Unused energy converts into…”
- “Taking the dangerous route causes…”
- “Critical hits mark targets; marked targets…”

Be cautious with unconditional `+X% damage`, `+X health`, or `+X currency`. These can support a simple baseline but should not dominate the pool.

For every passive ask:

1. Can the player notice it without consulting a damage log?
2. Can the player change behavior to exploit it?
3. Does it connect to at least two existing systems?
4. Is it still acceptable when found early, late, or outside its ideal build?
5. Can multiple copies stack safely?

## 5. Tags and Interaction Contracts

Use a controlled tag vocabulary. Example categories:

- **Delivery:** melee, projectile, beam, area, summon, trap
- **Damage:** physical, fire, poison, lightning, true
- **Timing:** on-hit, on-kill, on-dodge, periodic, charged, delayed
- **Resource:** mana, heat, ammo, health, gold, discard
- **State:** airborne, marked, burning, shielded, low-health
- **Target:** self, nearest, aimed, random, all, boss

Define whether tags describe source, resulting effect, or both. Document inheritance through summons, reflected projectiles, chain effects, and damage-over-time. Ambiguous tag semantics create exponential QA cost.

## 6. Rarity and Reward Pools

Rarity should represent a content role, not automatically raw strength.

Possible uses:

- Complexity budget
- Build commitment
- Novelty or rule-changing scope
- Acquisition timing
- Reliability or flexibility
- Upgrade ceiling

Control pool health with:

- Minimum independent-value rules
- Duplicate and copy policies
- History-aware drought prevention
- Context-sensitive offers with bounded generosity
- Skip, reroll, banish, salvage, or transform options
- Unlock rules that do not dilute early pools with niche content

Track the probability of seeing enabler-plus-payoff combinations within realistic run length. A theoretical synergy is not valid if its assembly probability is negligible.

## 7. Synergy Matrix

Audit new content against existing tags and roles:

| Interaction | Meaning | Desired share |
|---|---|---|
| Independent | Useful without support | High |
| Soft synergy | Better together but not required | High |
| Hard synergy | Requires a specific engine/tag | Limited |
| Anti-synergy | Forces a trade-off | Intentional |
| Invalid | Does nothing or breaks rules | Zero unless clearly communicated |
| Degenerate | Infinite, exponential, or dominant | Zero |

For large pools, test pairwise interactions automatically and manually test high-risk three-part chains: generator → repeated trigger → payoff.

## 8. Content Set Planning

Plan a release set by coverage before writing names:

- Core archetypes and hybrid bridges
- Early-run stabilizers
- Late-run scaling options
- Defensive and recovery tools
- Economy and route tools
- Skill-expression options
- Accessibility-friendly options
- Weird rule-changing content

Set a maximum percentage for narrow archetype-only rewards. Ensure each major build has multiple enablers, payoffs, and fallback routes.

## 9. Balance and Evaluation

Compare content under several states:

- Found early versus late
- Weak, average, and strong current build
- Single target, crowd, mobile target, and armored target
- Resource-rich and resource-starved
- Novice and expert execution
- Base form and maximum realistic scaling

Useful metrics include pick rate, skip rate, win rate conditional on acquisition floor, damage or value share, time held, activation frequency, overkill, wasted triggers, build concentration, and replacement rate.

Do not balance by equalizing pick rate. A clear or exciting item may be popular without being overpowered.

## 10. Failure Checks

Reject or revise content when:

- The best use requires no behavioral change
- The effect is unreadable during actual play
- It is dead outside one rare combination
- It solves every encounter type with the same action
- It removes the host genre's primary skill
- It scales recursively without a hard bound
- It increases pool dilution more than run variety
- Its QA interaction surface exceeds its player-facing value

## Completion Criteria

A content entry is ready for implementation when its role, rules, tags, resolution order, feedback, counterweight, tuning knobs, stacking behavior, edge cases, production dependencies, and test scenarios are explicit—and when it adds a new decision rather than only another number.
