# Roguelike Subgenre Guide

Load this reference when identifying a subgenre, adapting a design to one, comparing genre directions, or combining roguelike structure with another genre.

## 1. Classify by Dimensions First

Genre labels are shorthand, not complete specifications. Describe the project on these dimensions before assigning labels:

| Dimension | Example spectrum |
|---|---|
| Time model | Turn-based → simultaneous turns → pausable real time → real time |
| Spatial model | Grid → nodes/lanes → rooms/arenas → continuous world |
| Run loss | Full reset → selected retention → loadout retention → low-cost retry |
| Persistent progression | None → option unlocks → bounded power → major permanent power |
| Procedural scope | Items only → encounters → topology → rules/world simulation |
| Primary mastery | Knowledge → planning → execution → build optimization → economy management |
| Player control | Direct avatar → squad → deck → automated units → settlement/system |
| Run length | Minutes → session-length → multi-session campaign |
| Randomness | Mostly input → mixed → high output variance |
| Failure recovery | Learn and restart → branch/recover → extract → rebuild persistent state |

Use labels only after this profile is clear. If a project sits between categories, name a primary genre and one or two modifiers rather than inventing an opaque label.

Treat adjacent labels such as **Soulslike**, **Metroidvania**, **immersive sim**, **tower defense**, **shooter**, or **sandbox** as modifiers unless their host-genre loop is actually dominant. Do not assume that procedural generation, permadeath, meta-progression, or run-based play follows automatically from any one of these labels.

## 2. Subgenre Design Profiles

### Traditional Roguelike

**Core promise:** deep, systemic problem solving in a dangerous procedural world.

**Prioritize:**

- Turn economy and grid positioning
- Interactions between terrain, creatures, inventory, statuses, and environment
- Identification, information gathering, and knowledge mastery
- Procedural topology with exploration and route consequences
- Consumables as tactical escape valves

**Watch for:** opaque rules, unavoidable deaths, repetitive opening floors, inventory burden, and dominant safe tactics.

**Useful metrics:** depth reached, cause of death, unused consumables, repeated-action frequency, escape-option availability, and win rate by knowledge band.

### Roguelite

**Core promise:** repeated runs that remain rewarding through evolving options, story, mastery, or bounded persistence.

**Prioritize:**

- A satisfying run even before permanent upgrades
- Meta-progression that opens expression rather than charging a grind tax
- Clear separation between run power and account power
- Fast restart and changing goals across attempts
- Catch-up or anti-grind rules for late adopters

**Watch for:** intentionally unwinnable early runs, upgrade trees full of mandatory stats, content dilution from unlocks, and repetition disguised as progression.

**Useful metrics:** power gained per hour, first-win timing, unlock usage, run variety before and after progression, and win rate normalized by account power.

### Action Roguelite

**Core promise:** expressive real-time combat plus adaptive build formation.

**Prioritize:**

- Input responsiveness, movement identity, hit feedback, and threat telegraphs
- Combat spaces matched to mobility and attack ranges
- Builds that alter tactics, not only damage output
- Pauses or safe moments for high-information decisions
- Difficulty split between execution, threat reading, and build planning

**Watch for:** visual noise, unavoidable overlapping attacks, animation locks without warning, builds that erase action mastery, and reflex checks that exclude the target audience.

**Useful metrics:** damage by source, reaction window, input-to-action latency, hit readability, build concentration, and encounter clear-time distribution.

### Roguelike Deckbuilder

**Core promise:** construct a probabilistic action engine while navigating run-scale risk.

**Prioritize:**

- Draw consistency versus flexibility
- Card removal, transformation, and skip decisions
- Energy/action economy and turn sequencing
- Enemy intent or another planning signal
- Route rewards that create deck-shaping trade-offs

**Watch for:** deck bloat, infinite loops, mandatory scaling, excessive card text, low-impact rewards, and encounters that invalidate an archetype without warning.

**Useful metrics:** pick/skip/remove rates, deck size, dead-draw rate, turns to engine setup, archetype win rates, and card performance conditional on deck context.

### Survivors-like / Bullet Heaven

**Core promise:** transform from vulnerable to spectacular while steering through escalating crowds and rapid upgrade decisions.

**Prioritize:**

- Movement and positioning as the main continuous decisions
- Frequent, low-friction upgrade cadence
- Distinct weapon coverage patterns and evolution routes
- Spawn pacing, crowd composition, density readability, and elite timing
- Technical budgets for entities, projectiles, particles, and damage events

**Watch for:** upgrades with fake choices, idle optimal play, screen-obscuring effects, exponential performance collapse, first-minutes repetition, and late-game invulnerability without new decisions.

**Useful metrics:** movement heatmaps, time between upgrades, reroll/banish usage, damage share, enemy density, frame time, and time at which meaningful danger disappears.

### Tactical or Squad Roguelike

**Core promise:** solve changing battlefield problems while managing squad capability and attrition across a run.

**Prioritize:**

- Positioning, action economy, initiative, and objective play
- Unit roles with overlapping solutions
- Injury, casualty, replacement, and recovery rules
- Mission choice and campaign resource pressure
- Readable enemy plans and terrain consequences

**Watch for:** one lost unit causing an unrecoverable campaign spiral, alpha-strike dominance, excessive restart incentives, long missions invalidated by one hidden roll, and irreplaceable specialists.

**Useful metrics:** casualty recovery time, mission restart rate, action efficiency, objective completion methods, squad composition diversity, and when campaigns become mathematically doomed.

### Platform Roguelite

**Core promise:** expressive traversal and combat through remixed spaces.

**Prioritize:**

- Stable movement physics and learnable timing
- Geometry assembled from validated traversal chunks
- Safe spawning and camera-aware hazard placement
- Movement upgrades that change routing without breaking generation
- Fast recovery after mechanically demanding failures

**Watch for:** impossible procedural jumps, blind landings, momentum-dependent traps, incompatible upgrades and chunks, and long repetition before a difficult platforming check.

**Useful metrics:** failure location, traversal time, missed-input reports, chunk compatibility failures, recovery time, and completion rate by movement loadout.

### Strategy, Colony, or Management Roguelike

**Core promise:** steer a growing system through uncertain crises and compounding consequences.

**Prioritize:**

- Economy loops, reserves, opportunity cost, and time horizons
- Controlled cascades with warning and intervention windows
- Procedural events that respond to state
- Multiple viable development paths
- Run narratives emerging from systemic pressure

**Watch for:** invisible death spirals, dominant build orders, excessive early randomness, solved openings, runaway positive feedback, and late failures determined hours earlier without warning.

**Useful metrics:** resource reserves before failure, build-order concentration, recovery frequency, crisis response diversity, snowball timing, and percentage of runs still strategically recoverable.

### Extraction Roguelite Hybrid

**Core promise:** continually decide whether to risk accumulated value for a larger payoff or secure it by leaving.

**Prioritize:**

- Clear extraction access, timing, and interruption rules
- Legible distinction between carried, secured, and permanently unlocked value
- Optional greed paths and changing risk zones
- Partial-loss rules that preserve tension without deleting all motivation
- Anti-snowball matchmaking or PvE difficulty controls when relevant

**Watch for:** mandatory-feeling greed, spawn ambushes, unclear loss rules, veteran gear oppression, extraction camping, and risk-free farming routes.

**Useful metrics:** extraction timing, value carried versus secured, death location, loss recovery time, route profitability, and player wealth distribution.

### Puzzle, Rhythm, Stealth, Autobattler, and Other Hybrids

**Core promise:** the host genre remains satisfying while run variation changes the problems it presents.

**Rule:** identify the host genre's irreducible skill and protect it.

- **Puzzle:** preserve solvability and deduction; randomness should vary premises, not secretly invalidate logic.
- **Rhythm:** preserve timing readability and musical coherence; build effects must not obscure cues.
- **Stealth:** preserve information, route planning, detection rules, and recovery states; procedural layouts need readable patrol logic.
- **Autobattler:** preserve composition, positioning, scouting, and economy decisions; automation should resolve choices rather than replace them.

Watch for roguelike progression overpowering the host skill or procedural variation violating the host genre's fairness requirements.

## 3. Hybridization Method

When combining genres:

1. Name the **primary skill** the player practices continuously.
2. Name the **run adaptation layer** that changes the problem between attempts.
3. Assign each system to one of those roles; remove systems that serve neither.
4. Resolve pacing conflicts—for example, real-time action should not demand dense reading during danger.
5. Resolve failure-cost conflicts—for example, a long strategy campaign needs different loss recovery from a ten-minute action run.
6. Define which genre wins when conventions conflict.

Completion criterion: the hybrid can be explained as “The player repeatedly **[primary skill]**, while each run changes **[adaptation layer]**,” and its systems support that sentence.

## 4. Subgenre Selection Matrix

Use this matrix to compare candidate directions. Score each from 1–5 based on evidence, not preference.

| Criterion | Candidate A | Candidate B | Candidate C |
|---|---:|---:|---:|
| Fits the player fantasy |  |  |  |
| Makes the core mechanic recur often |  |  |  |
| Supports meaningful run variation |  |  |  |
| Matches target session length |  |  |  |
| Matches team and content budget |  |  |  |
| Technically feasible |  |  |  |
| Easy to communicate to players |  |  |  |
| Offers a distinct market position |  |  |  |
| Supports accessible onboarding |  |  |  |

Do not select by total score alone. Identify any criterion that is a hard constraint and reject candidates that fail it.

## 5. Cross-Subgenre Diagnostic

When a design feels wrong, check for convention mismatch:

- Is action-game execution being interrupted by excessive menus?
- Is a strategy-scale failure too costly for the amount of hidden information?
- Is permanent power replacing skill growth rather than supporting it?
- Is procedural generation breaking platforming, puzzle, rhythm, or stealth guarantees?
- Is automatic combat leaving enough planning and positioning decisions?
- Is deck or build variance too high for the player's ability to repair it?
- Does run length justify the severity of loss?
- Does the level structure create the decisions the chosen subgenre promises?

State the mismatch, its player impact, and whether to change the mechanic, the run structure, or the genre positioning.

## 6. Required Subgenre Output

When the user requests a new concept or major redesign, include:

- Primary label and optional secondary labels
- Dimension profile
- Host genre's primary skill
- Roguelike adaptation layer
- Run length and failure cost
- Procedural scope
- Persistent progression model
- Subgenre-specific level or encounter structure
- Most important balance metrics
- Two convention-mismatch risks
- Cheapest prototype that validates the genre fit
