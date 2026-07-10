# Meta-Progression, Unlocks, and Failure Economy Guide

Load this reference when designing persistent progression, currencies, unlocks, account power, difficulty ladders, death rewards, narrative progression, character rosters, collections, or long-term goals between runs.

## 1. Define the Purpose

Meta-progression may serve:

- Onboarding
- Long-term goals
- Strategic expression
- Content discovery
- Narrative pacing
- Accessibility
- Difficulty customization
- Collection and mastery
- Recovery from repeated failure

Do not add persistent progression solely because the game is called a roguelite. State which player problem it solves and what cost it introduces.

## 2. Separate Progression Types

| Type | Examples | Main benefit | Main risk |
|---|---|---|---|
| Permanent power | Health, damage, starting resources | Smoother onboarding | Early runs become intentionally weak |
| Option unlock | Weapons, cards, characters, routes | Expression and discovery | Pool dilution and complexity |
| Knowledge unlock | Bestiary, intent, recipes, odds | Supports mastery | Removes mystery or creates UI dependence |
| Difficulty unlock | Heat, ascension, mutators | Long-term mastery | Numeric inflation or fractured balance |
| Narrative unlock | Dialogue, memories, regions, endings | Motivation and context | Story requires repetitive failure |
| Cosmetic/status | Skins, badges, records | Goal without power | Weak motivation for some audiences |
| Convenience | Reroll presets, faster menus, practice | Respects returning players | Basic usability held hostage |

Keep usability and essential accessibility outside grind progression.

## 3. First-Run Viability

Define whether the first run can win. If not, explain the player-facing contract and avoid pretending all outcomes were equally possible.

Prefer:

- A genuinely viable first run
- Horizontal options unlocked gradually for comprehension
- Bounded assistance after repeated failure
- Tutorial protection that does not corrupt later rules

Measure performance by both player experience and account power. Permanent upgrades can hide onboarding problems rather than solve them.

## 4. Failure Economy

For each loss define:

- What is lost
- What is secured
- What knowledge is gained
- What persistent value is earned
- Whether value depends on depth, risk, objectives, or extraction
- How quickly the next meaningful attempt begins

A failure reward should respect effort without making intentional fast failure optimal.

Possible formula:

```text
failure_reward = base_participation
               + progress_value
               + optional_risk_value
               + first-time_learning_bonus
               - exploit_adjustments
```

Cap repetitive low-risk farming and reward varied mastery, but never secretly remove earned value without clear rules.

## 5. Persistent Currency

For every meta currency define:

- Sources and earning cadence
- Sinks and completion horizon
- Carry and cap
- Refund/respec policy
- Duplicate conversion
- Post-completion sink
- Catch-up policy
- Anti-farm and anti-exploit rules

Avoid multiple currencies that differ only by shop category. Use separate currencies when they represent different goals, risks, or time horizons.

Estimate time to meaningful purchase, time to a coherent build path, and time to functional completion—not only total completion.

## 6. Permanent Power Budget

If permanent power exists, specify:

- Maximum advantage versus a fresh account
- Which mechanics may scale
- Whether difficulty compensates
- Whether power applies to all modes
- How co-op or leaderboards segment account power
- How balance tests normalize power

Prefer diminishing returns and bounded totals. Avoid many small mandatory nodes that create the illusion of choice.

Test at:

- Fresh account
- Early progression
- Median progression
- Functional completion
- Maximum account power

Every state intended for normal play must have coherent difficulty and economy.

## 7. Unlock Graph

Represent dependencies explicitly. Each unlock node should contain:

- Requirement
- Cost
- Reward
- Player-facing preview
- Pool impact
- Complexity tier
- Dependencies
- Alternate acquisition or pity rule

Use branching when choices express play preference. Use linear gates only for teaching order, narrative order, or true dependencies.

Prevent dead-end spending and irreversible choices that require outside knowledge. Provide respec when experimentation is a core promise.

## 8. Content Pool Dilution

Unlocking more content can make desired tools rarer and the game less coherent.

Control dilution with:

- Pool partitions
- Character or biome affinities
- Tag-weighted but bounded offers
- Drafting and route information
- Banish, reroll, reserve, or wishlist systems
- Minimum independent-value rules
- Unlock bundles that include enabler, bridge, and payoff
- Duplicate protection

Evaluate assembly probability for representative builds before and after each unlock tier. An unlock should not silently reduce baseline viability.

## 9. Unlock Bundles

Do not unlock a narrow payoff without support. A bundle may include:

- One independently useful item
- One enabler
- One hybrid bridge
- One payoff
- One counter or enemy interaction
- One tutorial or codex entry

Stagger complexity: introduce one new grammar at a time, then allow combinations.

## 10. Narrative Progression

Define triggers independently from mandatory grind where possible:

- First encounter
- Specific choice
- Victory or defeat condition
- Character relationship
- Reaching a region
- Demonstrating mastery
- Repeated failure with bounded count

Use pity triggers for story content so poor luck does not block narrative. Distinguish canonical progression from repeated run variation. Do not require players to die intentionally to see essential story.

## 11. Difficulty Ladders

A difficulty ladder should name what changes:

- Threat roles and combinations
- Resource pressure
- Timing and execution windows
- Route uncertainty
- Consequence severity
- New rules or modifiers
- Numeric scaling

Unlock difficulty through demonstrated mastery, not only account level. Rewards should motivate without making lower difficulty economically irrational.

Track completion and abandonment per modifier combination. Avoid modifiers that disable whole build families unless clearly presented as optional challenge contracts.

## 12. Characters and Starting Loadouts

A character unlock should offer a distinct decision grammar, not a strictly better baseline.

Define:

- Starting strengths and liabilities
- Unique resource or rule
- Compatible and incompatible build tags
- Learning complexity
- Unlock timing
- Cross-character account power
- Shared versus separate progression

Do not hide the only accessible or beginner-friendly character behind difficult progression.

## 13. Catch-Up and Returning Players

Possible tools:

- Increased currency until a functional baseline
- Choice bundles instead of random unlocks
- Condensed tutorials and recaps
- Retroactive duplicate conversion
- Account migration grants
- Practice mode
- Build and rule summaries

Catch-up should reduce redundant time, not skip the mastery the game is about.

## 14. Completion and Post-Completion

Separate:

- Functional completion: all core strategies available
- Collection completion: all optional content acquired
- Mastery completion: challenges or difficulty ladder
- Prestige: cosmetics, records, seasonal goals

After functional completion, avoid adding compulsory power sinks that destabilize balance. Use expression, mastery, and optional prestige goals.

## 15. Telemetry

Track:

- Currency earned/spent by run and account age
- Time to first meaningful purchase
- Node purchase and refund rate
- Unlock usage and abandonment
- Pool size and build assembly probability
- Win rate by experience and account-power band
- Intentional farming or early-death patterns
- Functional-completion time
- Difficulty unlock, attempt, completion, and abandonment
- Narrative trigger droughts

Do not interpret account-power effects without separating player experience.

## 16. Exploit and Friction Audit

Check for:

- Fast intentional death as optimal currency farming
- Repeating low-risk content instead of engaging with progression
- Save rollback or duplicate reward collection
- Currency overflow and useless late-game stock
- Irreversible trap purchases
- Mandatory stat nodes
- Unlocks that reduce player power through dilution
- Story blocked by randomness
- Lower difficulty yielding better progression efficiency
- Accessibility or usability locked behind grind

## Completion Criteria

A meta-progression design is ready to prototype when its purpose, progression types, first-run viability, loss contract, currencies, permanent-power bound, unlock graph, pool impact, difficulty relation, catch-up rules, completion horizons, telemetry, and exploit safeguards are explicit.
