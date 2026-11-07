# Run State, Resume, and Reproducible Failures

Load this reference when specifying suspend/resume, crash recovery, reward settlement, seeded challenges, deterministic replay, patch compatibility, or reproducible playtest reports. Use `templates/run-state-contract.md` for the contract. Keep implementation proportional to the game: a solo prototype does not automatically need a network service or cross-platform lockstep.

## 1. Distinguish the Promises

| Promise | Required context | What it does not guarantee |
|---|---|---|
| Seeded generation | Seed, generator/content versions, parameters, eligible pools, stable selection order | Same run after different choices or account unlocks |
| Suspend/resume | Authoritative checkpoint, RNG states, pending decisions, committed progression | Rewind, reroll, or recovery from every possible crash |
| Deterministic replay | Initial state, ordered actions with simulation timing, rules/content versions, RNG contract | Bit-identical results on untested platforms or after patches |
| Reproducible diagnosis | Versions, checkpoint or seed plus actions, settings, first-divergence trace | Proof that a balance complaint is a rules bug |

State the supported platforms, modes, versions, and comparison scope. Compare normalized authoritative state at the same simulation tick/turn; exclude wall-clock timestamps, presentation caches, and other intentionally non-authoritative data. If exact replay is unsupported, define observable invariants and tolerances instead of promising determinism.

## 2. Define Save Boundaries and State Ownership

Choose explicit safe boundaries: after a completed turn, resolved reward, room transition, or another coherent checkpoint. For mid-action saves, either serialize the pending resolution queue and its ownership/order or defer saving until resolution completes. Do not restore half of an action as if it had never happened.

Inventory at least:

- Run ID, checkpoint revision, stage, generated world state and player modifications
- Health, inventory/deck, resources, statuses, cooldowns, enemy state, and pending effects where relevant
- RNG algorithm/version and current state or reconstructible counters for each authoritative stream
- Director history, pity/drought counters, banishes, exhausted pools, and anti-repeat history
- Already offered choices, their eligibility context, and selected/claimed state
- Account unlock/power state used by this run, plus profile settings and their scope
- Earned but unsettled rewards and the identifiers of already committed grants

A seed is not a substitute for current RNG state. Use stable IDs and ordering rather than locale-dependent names or unordered-container iteration. Separate cosmetic randomness from authoritative streams. For parallel generation, define stable task/result ordering; worker count and completion order must not silently change legal outcomes within the supported determinism scope.

## 3. Preserve Failure and Economy Contracts

Suspend is not death, and loading is not a new reward roll. Preserve an offered choice and its relevant history unless reroll is an explicit player-facing action with its declared cost. Define crash recovery's maximum rollback window honestly; do not punish ordinary interruption to protect a single-player prestige claim.

For a boss reward, extraction, currency purchase, or run-end unlock, specify one logical transaction:

1. Validate its preconditions and stable transaction ID.
2. Record the authoritative outcome, including cost and grant, at a recoverable commit boundary.
3. On retry or resume, recognize that transaction and complete recovery without a second charge or grant.
4. Show completion only when the committed state supports it; retrying a UI animation must not execute the transaction again.

Choose atomic snapshot replacement, a journal, a server transaction, or another tested mechanism appropriate to the platform. Preserve the last valid checkpoint during interrupted writes and validate before replacing it. The contract is **one logical settlement despite repeated delivery**, not a claim that storage or networking delivers exactly once. When run and account state are stored separately, specify how an interrupted cross-store settlement is reconciled.

For cloud conflict, define revision/ownership and recovery behavior; never blindly add balances or union claimed rewards from competing histories. Keep a recoverable copy and disclose which history is resumed. Offline single-player saves cannot guarantee tamper-proof competitive records; separate practice, seeded, assisted, modded, and verified-record policies only where the mode needs it, without penalizing essential access settings.

## 4. Patch and Content Compatibility

Specify whether an in-flight run uses pinned rules/content, a tested migration, or an explicit unsupported-version recovery path. Define policies for removed content IDs, changed effects, pool eligibility, RNG changes, mods, and downgrade attempts. Preserve the original save before migration and prevent repeated migration from granting compensation twice. Never silently regenerate a saved world or reset earned progression because an old ID is missing.

Seed sharing and daily challenges need a ruleset manifest: game/content/generator versions, character/loadout, unlock pool, difficulty, and supported settings. A patch may legitimately change a seed; version the claim rather than calling different outcomes identical. Separate live-balance analysis by ruleset and branch.

## 5. Regression and Playtest Matrix

| Test | Compare or inject | Acceptance |
|---|---|---|
| Save round-trip | Save → load → save at a stable boundary | Normalized authoritative state unchanged |
| Continuation | Uninterrupted run versus checkpoint/resume with identical subsequent actions | Same authoritative outcomes within declared scope |
| Reward boundary | Interrupt before/after cost, outcome commit, account grant, and presentation | No partial purchase, duplicated grant, lost committed value, or free reroll |
| History restoration | Resume after pity, banish, director intervention, or an offered reward | Histories and choices preserved |
| Write failure/conflict | Truncated write, unavailable storage, competing cloud revisions | Last valid state recoverable; no silent overwrite or balance merge |
| Patch/mod transition | Supported migration twice; unsupported version; removed ID | Idempotent migration or clear recovery path; original preserved |
| Determinism scope | Supported platforms, worker counts, render rates, assist profiles | Exact comparison only where promised; causal trace otherwise |

Keep a small fixed regression corpus of troublesome seeds/checkpoints plus exploratory seed batches. For A/B balance tests, the same seed is not sufficient control when changed rules consume RNG differently. Restore matched checkpoints where valid, record stream divergence, counterbalance player learning, and use population-level comparisons when action paths necessarily differ.

A failure packet should include versions/branch/mod manifest, seed and checkpoint revision, relevant account/unlock state, settings/input, ordered reproduction actions, expected/actual result, and the first divergent tick/event. Store a bounded development trace and compare the earliest mismatch before downstream effects obscure it. Obtain consent for uploaded saves, strip identifiers and secrets, and define retention; do not attach entire personal profiles to public bug reports.

## 6. Source Basis and Limits

Reviewed 2026-11-07. These first-party reports support explicit state and reproduction contracts. The transaction, migration, and worksheet rules above are design synthesis, not claims about the cited games' private save implementations.

- **Wube / kovarex, Friday Facts #158 (2016-09-30)** — explains cross-platform state checks and save-load-save stability comparisons used to isolate desync causes. Older but directly relevant engineering evidence: <https://www.factorio.com/blog/post/fff-158>
- **Wube / Rseding, Friday Facts #415 (2024-06-14)** — documents a chunk-generation desync requiring different CPU core counts plus mod actions. Supports testing task ordering and declared determinism scope, not assuming a seed is sufficient: <https://www.factorio.com/blog/post/fff-415>
- **Mega Crit, Slay the Spire 2, Beta Patch Notes v0.111.0 (2026-08-14 UTC)** — first-party notes include modded/unmodded save-copy errors, end-of-run badges lost on early exit, and chained-effect/transition failures. Evidence for settlement and lifecycle regression coverage, not universal card tuning: <https://steamstore-a.akamaihd.net/news/externalpost/steam_community_announcements/1840944183778277> (content/date verified through Steam's public GetNewsForApp API)
- **Mega Crit, The Neowsletter — October 2026 (2026-10-30 UTC)** — first-party Q&A endorses categorized in-game feedback and discusses co-op resource-pooling snowballs; distinguishes current beta from the next planned update. Supports contextual feedback and branch-aware review; planned content is not shipped evidence: <https://steamcommunity.com/app/2868840/announcements/>
- **poncle, Vampire Survivors, 1.16.111 hotfixes / next patch preview (2026-10-16 UTC)** — first-party notes fix late-save QuickStart repetition and unlock/achievement failures, and explicitly discuss public-beta save compatibility during an engine update. Supports testing progressed accounts and branch transitions; a developer's compatibility statement is not proof for another game: <https://steamcommunity.com/app/1794680/announcements/> (content/date verified through Steam's public GetNewsForApp API)

## Completion Criteria

A run-state contract is ready when save boundaries, authoritative state, RNG/history restoration, reward settlement, crash/conflict recovery, version policy, privacy-safe failure packets, and scoped regression acceptance criteria are explicit. Passing document review is not proof that an actual game's saves or replay work; exercise its implementation separately.
