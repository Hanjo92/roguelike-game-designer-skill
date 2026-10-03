# Evaluation: Dense Combat Without Hardware-Dependent Nerfs

## Prompt

> Our 30-minute survivors-like runs well early on, but a legal summon/projectile/proc build causes late-wave hitches on minimum-spec hardware. Some player attacks disappear, enemies occasionally skip their tells, and a boss never spawns when its object pool is full. The team proposes dropping damage events and enemy warning effects until the frame rate recovers. We are a four-person team targeting PC and handheld devices. Review the proposal and produce a scoped runtime-load contract, overflow policy, and test plan without removing the strong-build fantasy.

## Mandatory Checks

- Separates authoritative gameplay, essential information, and decoration before proposing reductions
- Rejects silently dropping damage, mandatory enemies, rewards, or critical cues
- Specifies measured frame-time tails, hitch, input-delay, memory, and simulation-backlog targets as hypotheses
- Budgets enemies, summons, projectiles, proc fan-out, pickups, and presentation independently
- Defines pool exhaustion/reset, bounded queues, and a bounded catch-up or overload-recovery policy
- Accounts for simulation, real, input, and UI clocks under hitches and supported assists
- Tests peak-load legal builds, transitions, minimum supported devices, and sustained sessions
- Compares damage/resource/completion invariants with matched actions or checkpoints, not just the same seed
- Separates technical failures from balance conclusions and prioritizes a small profiling/graybox test
- Explains any authoritative cap or substitution as a stable rule with a tested gameplay trade-off

## Critical Failures

- Accepts dropping player damage or lethal warnings as an invisible performance optimization
- Allows pool exhaustion to skip the mandatory boss or its reward
- Claims average FPS alone establishes responsiveness or fairness
- Recommends unbounded catch-up, queues, or effect allocation
- Claims a fixed timestep or common seed alone guarantees identical cross-platform runs

## Strong Response Signals

- Reserves capacity for boss/objective entities and essential cues instead of sharing an unbounded decorative pool
- Identifies collision fan-out and proc combinations as potential bottlenecks without asserting a cause before profiling
- Distinguishes reducing rendering work from repairing CPU-bound simulation overload
- Specifies bounded development traces, numerical reconciliation, and human readability tests
