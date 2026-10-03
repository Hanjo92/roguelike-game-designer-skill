# Runtime Performance and Combat Fairness

Load this reference for survivors-likes, projectile-heavy action games, summon or proc engines, dense procedural encounters, or failures that appear only under load. Performance is a design constraint when it changes what players can perceive, execute, earn, or reproduce—not merely a graphics target.

## 1. Define the Supported Load Contract

Record minimum supported hardware/platform, input device, render target, simulation clock, supported assist profiles, and representative run duration. Define measured frame-time percentiles, maximum tolerated hitch, input-response limits, memory headroom, and simulation backlog limits. Initial numeric limits are hypotheses to validate on target devices, not universal genre standards.

Budget independent sources of work:

| Source | Bound and evidence to specify | Protected behavior |
|---|---|---|
| Enemies and summons | Active count, AI/pathfinding cadence, spawn burst | Role mix, target priority, objective completion |
| Projectiles and hazards | Live count, lifetime, collision work | Hit registration, danger area, escape windows |
| Proc chains | Root-action fan-out, recursion depth, queued work | Declared trigger, stack, and attribution rules |
| Rewards and pickups | Live count, spawn/collection burst | Resource totals, access, acquisition order |
| Presentation | Particles, damage text, audio voices, animation work | Lethal tells and relevant feedback |
| Generation and transitions | Work per update, loading boundary, memory peak | Valid geometry, safe entry, no hidden lost input |

A count cap is not a cost model. A few area effects hitting a dense crowd can cost more than many isolated enemies. Profile combinations and simultaneous transitions, not only each system separately. Test legal high-power builds; do not make them functionally weaker only on slower hardware.

## 2. Separate Rules from Presentation

Classify each component as authoritative gameplay, essential information, or decoration. A projectile sprite may be simplified while its gameplay trajectory remains unchanged; a lethal area marker is essential information even if implemented as a visual effect.

- Reduce decoration first: particles, redundant damage numbers, secondary trails, or nonessential sounds.
- Reserve presentation capacity for critical tells, damage direction, objectives, and the selected accessibility cue channels.
- Pooling or batching is an engineering option, not permission to lose effects. Specify pool exhaustion, complete state reset, ownership, and stale-reference prevention.
- Never silently drop player damage, mandatory enemies, rewards, pickups, or lethal warnings because a pool or queue is full.
- If an authoritative cap is necessary, make it a stable rule across supported hardware and disclose it where it affects build or encounter choices. Validate its effect on damage, resources, role composition, and completion.
- Any spawn deferral, aggregation, or substitution needs a bounded queue and an explicit equivalence or trade-off test. Cosmetic degradation alone cannot repair CPU-bound simulation overload.

Do not prescribe pooling, fixed entity counts, or one frame-rate target for every engine. First measure the limiting work, then choose the smallest intervention that preserves the design contract.

## 3. Time and Overload Behavior

Define simulation, real, input, and UI clocks using `accessibility-difficulty.md`. Specify update cadence, collision handling, pause/resume, and bounded catch-up. A fixed or bounded timestep can reduce frame-dependent behavior, but is not by itself a guarantee of cross-platform determinism.

For overload, explicitly choose what happens to accumulated time: bounded catch-up with headroom, controlled slowdown, a safe pause/loading boundary, or another tested policy. State its limit and recovery behavior. Avoid an unbounded catch-up spiral; do not let real-time spawns or damage continue while the simulation or player input is stalled.

Check that low render rates and hitches do not cause projectile tunneling, repeated/missing procs, compressed tells, lost buffered input, or timers advancing under different clocks. Compare rule outcomes at matched simulation checkpoints using identical recorded actions—not only the same seed. Record starting state, RNG state where needed, versions, and assist settings. Scope deterministic comparison to the platforms and systems that actually support it; otherwise define tolerances and inspect causal event traces.

## 4. Stress-Test Matrix

Use `templates/encounter-spec.md` for budgets and `templates/playtest-plan.md` for evidence and stopping rules.

Test at least:

- Opening, peak-density late run, and boss or wave transition
- Weak viable, typical, and legal maximum-fan-out builds
- Summons, multi-hit area attacks, proc chains, and simultaneous pickups
- Minimum supported device, sustained-session thermal/load conditions, and supported cue-reduction or speed settings
- Artificial hitches and exhausted pools/queues in development builds
- Pause, suspend, save/load, and restart near an overloaded transition

Record frame-time tails, hitch duration, simulation backlog, input delay, live entities, queued effects, pool high-water marks, rejected/deferred work, and resource/damage reconciliation. Use bounded development traces or sampled aggregates rather than logging every frame to production telemetry.

Acceptance requires both technical targets and gameplay invariants: no hidden loss of damage or rewards, no skipped mandatory encounter, critical cues remain perceivable, no unbounded backlog, and recovery follows the declared policy. Human tests still decide whether dense combat is readable and exciting. Separate technical failures from balance evidence before changing prices, damage, or enemy health.

## 5. Source Basis and Limits

Reviewed 2026-10-03. These sources justify treating load, clocks, and overflow as explicit contracts; the worksheet above is a design synthesis, not a claim that every cited game uses this implementation.

- **poncle, Vampire Survivors, “Legacy of the Bloodmoon is out now!” (2026-08-28)** — first-party Steam announcement. Describes CPU/memory framework improvements, low-FPS damage-number fixes, minute-transition stutter, and interactable visibility work. Concrete evidence that dense-run tests must cover transitions and presentation as well as average frame rate: <https://steamcommunity.com/games/1794680/announcements/detail/717913919982667417>
- **poncle, Vampire Survivors, “1.16.107 - hotfixes” (2026-08-30)** — first-party report of mixed-projectile failures, VFX texture problems, boss positioning, accessibility-effect settings, and online banish desynchronization. Supports combination and lifecycle regression tests; not evidence that any particular count cap is correct: <https://steamcommunity.com/games/1794680/announcements/detail/689767056035283485>
- **Mega Crit, Slay the Spire 2, “Beta Patch Notes - v0.111.0” (2026-08-14 UTC)** — first-party beta notes cover chained-card duplicate triggering, combat-ending/shuffling edge cases, save separation, and event/UI hitch reduction. A deckbuilder example of resolution and transition risks; beta changes are not universal balance recommendations: <https://steamcommunity.com/games/2868840/announcements/detail/671751488532383387>
- **Glenn Fiedler, “Fix Your Timestep!” (2004-06-10)** — named game-networking/physics practitioner's technical explanation of frame-dependent integration, bounded steps, catch-up overload, and separating simulation from rendering. Old but relevant foundational guidance; does not establish fun, accessibility, or a specific game's balance: <https://gafferongames.com/post/fix_your_timestep/>
- **Robert Nystrom, Game Programming Patterns, “Object Pool”** — publicly available practitioner book chapter. Page displays no chapter publication date (site copyright 2009–2021). Documents pool trade-offs, exhaustion policies, and reset hazards; use it conditionally after profiling rather than as a universal optimization: <https://gameprogrammingpatterns.com/object-pool.html>
