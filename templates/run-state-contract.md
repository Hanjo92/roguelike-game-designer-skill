# [Game / Mode] — Run State and Reproduction Contract

Use `references/run-state-reproducibility.md`. Fill applicable fields; mark exclusions with a reason rather than claiming unsupported replay guarantees.

## Promises and Scope

- Suspend, crash recovery, seeded generation, replay, and diagnosis promises:
- Supported platforms / modes / versions / mods:
- Exact authoritative comparison versus tolerance-based comparison:
- Practice / seeded / assisted / verified-record disclosure:
- Explicit non-goals:

## Save Boundary and Ownership

- Safe save point and pending-action policy:
- Run ID / checkpoint revision:
- Maximum crash rollback window and player-facing explanation:
- Storage failure behavior / last valid checkpoint:

| State | Authoritative owner | Saved or reconstructed how? | Restoration invariant |
|---|---|---|---|
| World / run changes / player and enemy state |  |  |  |
| Inventory / deck / resources / statuses / clocks |  |  |  |
| RNG algorithm, stream states, and stable ordering |  |  |  |
| Director / pity / banish / anti-repeat history |  |  |  |
| Offered choices / claim status / pending effects |  |  |  |
| Account unlocks / run-eligible pool / settings |  |  |  |
| Committed grant IDs / unsettled outcomes |  |  |  |

## Settlement and Recovery

| Transaction | Preconditions / cost / grant | Stable ID | Commit boundary | Retry / interrupted recovery |
|---|---|---|---|---|
| Purchase |  |  |  |  |
| Boss reward / extraction / run-end unlock |  |  |  |  |

- Run/account cross-store reconciliation:
- Presentation versus committed state:
- Offered-choice preservation / explicit reroll cost:
- Cloud conflict / ownership / recoverable histories:
- Offline integrity limits (if records matter):

## Versions and Migration

- Ruleset manifest (game/content/generator/RNG, pools, loadout, difficulty, settings):
- In-flight run policy: [pinned / migrated / unsupported with recovery]
- Removed content, mods, downgrade, and changed pool behavior:
- Original-save preservation:
- Idempotent migration / compensation:
- Leaderboard and analysis branch segmentation:

## Failure Packet and Test Controls

- Seed / checkpoint / account-state context:
- Ordered actions with simulation tick or turn:
- Expected / actual result and earliest divergent event:
- Normalized state fields / excluded transient fields / tolerance:
- A/B RNG divergence and player-learning controls:
- Supported worker-count and platform comparisons:
- Trace size bound / consent / redaction / retention:

## Regression Matrix

| Checkpoint / version / scenario | Fault or action sequence | Expected invariant | Actual evidence | Pass / fail |
|---|---|---|---|---|
| Save → load → save |  |  |  |  |
| Uninterrupted versus resumed continuation |  |  |  |  |
| Before / after cost and grant commit |  |  |  |  |
| Offered reward / history restoration |  |  |  |  |
| Interrupted write / cloud conflict |  |  |  |  |
| Migration twice / removed ID / unsupported version |  |  |  |  |

## Acceptance Criteria

- [ ] Seed reproducibility is distinguished from replay and resume
- [ ] Authoritative state, RNG streams, and selection history survive resume
- [ ] Identical actions match uninterrupted outcomes within the promised scope
- [ ] Repeated settlement causes neither a second grant nor a second charge
- [ ] Interrupted writes and conflicts retain a recoverable valid state
- [ ] Migration preserves the original and is safe to retry
- [ ] No silent reroll, world regeneration, or progression reset occurs
- [ ] Failure packets are sufficient, bounded, and privacy-safe
- [ ] Actual implementation evidence is recorded separately from design acceptance
