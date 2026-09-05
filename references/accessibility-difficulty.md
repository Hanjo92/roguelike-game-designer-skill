# Accessibility and Difficulty in Run-Based Games

Load this reference when designing difficulty, assists, controls, telegraphs, time pressure, save/quit behavior, onboarding, accessibility settings, or tests with players who have disabilities.

## 1. Preserve the Challenge Contract, Remove Access Barriers

Accessibility is not one global “easy mode.” First state the experience the game protects, then separate the demands used to produce it:

| Demand | Roguelike-family examples | Independent controls to consider |
|---|---|---|
| Perception | Telegraphs, enemy intent, hidden interactables, damage direction | Redundant visual/audio/haptic cues, contrast, text size, effect-opacity controls |
| Cognition | Rule recall, card text, route planning, objective memory | Glossary, intent history, reminders, preview, pause-to-read, simplified presentation |
| Motor/input | Aiming, dodging, holds, mashing, simultaneous inputs | Action remapping, toggles, sensitivity, timing windows, game speed, alternate inputs |
| Execution | Reaction windows, platforming precision, dense projectile navigation | Speed, aim/steering assists, extra retries, checkpoint or practice options |
| Strategy | Resource planning, build adaptation, threat prioritization | Better information and rehearsal before changing strategic rules |
| Attrition | Healing droughts, inventory pressure, squad loss | Resource abundance, loss severity, recovery guarantees |
| Consequence | Permadeath, carried-value loss, restart distance | Save-and-quit, recovery mode, partial loss, faster restart, practice without rewards |
| Sensory load | Flashing, shake, hit-stop, particles, crowd density | Flash/shake/motion/effect-density settings that preserve threat state |

Do not lower every axis when one axis is the barrier. Preserve the host genre's primary skill where possible: a deckbuilder may expose intent without solving deck construction; an action roguelite may widen dodge timing without choosing when to dodge; a traditional roguelike may improve screen-reader output without removing systemic uncertainty.

## 2. Define the Protected Core

For each major mechanic, record:

- **Player promise:** the feeling or mastery being protected
- **Required decision:** what the player should notice, choose, or plan
- **Access demands:** perception, cognition, input, timing, endurance, or sensory load not inherently required by that decision
- **Failure consequence:** time, progress, resources, or carried value lost
- **Adaptation boundary:** what can change without automating the protected decision

If a demand does not create the intended decision, treat it as a candidate barrier rather than difficulty worth preserving. Do not use genre tradition or competitive prestige as the only justification.

## 3. Build Modular Difficulty

Use named presets for fast setup, but expose important axes independently. Relevant axes include:

- Enemy count, role combinations, health, damage, and aggression
- Telegraph duration, contrast, persistence, and overlap
- Game speed, reaction windows, platforming forgiveness, and aim assistance
- Resource income, drought bounds, shop guarantees, and recovery availability
- Information disclosure, objective reminders, map detail, and enemy intent
- Permadeath severity, extraction loss, checkpointing, and restart distance
- Build-offer repair such as rerolls, skips, conversions, or duplicate protection
- Visual effects, screen shake, camera motion, flashing, and audio mix

For every option specify its exact effect, range, default, availability, persistence, and interactions. Avoid labels such as “casual” or “coward.” Describe behavior directly. Let players revise options after starting unless a competitive or challenge mode has a clearly disclosed reason not to.

Keep three contracts distinct:

1. **Accessibility option:** reduces an access barrier and should normally remain available without reward penalty.
2. **Difficulty option:** changes the demanded mastery or consequence and may define a separately tracked ruleset.
3. **Challenge modifier:** voluntarily adds a known constraint and may carry explicit rewards or records.

Do not assume these categories are interchangeable. If achievements, leaderboards, matchmaking, or rewards change, disclose that before selection.

## 4. Run-Specific Requirements

Run-based games amplify small barriers through repetition and accumulated loss.

### Before the first run

- Make settings reachable and operable with supported alternative inputs.
- Preview control, subtitle, cue, motion, photosensitivity, and difficulty options.
- Do not require progression currency to unlock essential accessibility or basic usability.
- Save settings by profile and retain them across death, prestige, and new runs.

### During a run

- Permit safe pause and settings changes where the game mode allows it.
- Keep critical information available long enough to perceive and interpret; do not auto-dismiss build or route choices during safety states.
- Preserve deterministic rule resolution when game speed changes.
- Separate **save-and-quit** from **rewind or rollback**. Suspending a long run need not invalidate permadeath.
- Make optional assistance discoverable without repeatedly interrupting or shaming the player.

### After failure

- Minimize menu and traversal time before meaningful play resumes.
- Offer practice or replay for a newly encountered boss, pattern, seed, or tutorial when it supports learning; explicitly state whether practice affects run rewards or records.
- Do not make repeated failure the only way to earn access to a needed assist.
- Report the loss state and retained state through more than one sensory channel.

## 5. Procedural and Systemic Compatibility

An assist profile can change the legal state space. Re-run generation and balance validation under representative profiles:

- Slower game speed can change cooldown, spawn, damage-over-time, animation, music, and physics timing.
- Aim or target lock can alter target priority and effective range.
- Mobility assists can invalidate jump, gap, hazard, key, or route assumptions.
- Additional information can alter the value of scouting, identification, and risk pricing.
- Resource assists can create shop arbitrage, cap overflow, or guaranteed-build loops.
- Reduced effects can hide gameplay-relevant hazards if cues are not separated from decoration.

Tag rules as **simulation time**, **real time**, **input time**, or **UI time**. Define which clock each timer uses. Validate connectivity, encounter budgets, boss phases, reward guarantees, and economy invariants for every officially supported assist combination, not only the default preset.

## 6. Telegraphs and Information

Critical state should not depend on one sensory channel. For lethal threats communicate enough of source, target or area, timing, severity, and response class through a suitable combination of:

- Shape, icon, text, pattern, outline, contrast, or directional marker
- Distinct sound, spatial audio, speech, or caption
- Distinct haptic pattern where supported

Color alone is not a sufficient distinction. Effects-reduction settings must remove decoration independently from gameplay cues. Information assistance should improve access before it silently changes hidden odds or outcomes.

## 7. Testing with Players

Accessibility review is not complete through a checklist or automated scan alone.

1. Name the player group and barrier being investigated; do not treat disability as one segment.
2. Include people with relevant lived experience early enough to alter the design, compensate them, and use an accessible consent and test setup.
3. Record the assist profile, input device, game speed, seed, account state, build, and run stage.
4. Test configuration and recovery as well as combat: can the player find settings, start, pause, save/quit, interpret death, and restart?
5. Separate “could not perceive,” “could not execute,” “did not understand,” and “chose poorly.”
6. Test combinations and fatigue over representative session lengths; one mechanic in isolation can pass while a full run does not.
7. Treat expert consultation and player tests as evidence, not permission to generalize one person's preference to everyone.

Use `templates/accessibility-matrix.md` to specify and verify the supported profiles. Link findings to `templates/playtest-plan.md` for controlled tests.

## 8. Acceptance Criteria

An accessibility and difficulty design is ready to prototype when:

- The protected fantasy and primary skill are explicit.
- Barriers are separated from intended decisions.
- Presets expose inspectable, independently adjustable rules.
- Essential accessibility is not progression-gated.
- Settings persist across the full failure/restart loop.
- Cue redundancy and effects-reduction behavior are defined.
- Every supported assist combination has systemic and procedural invariants.
- Reward, leaderboard, achievement, and multiplayer effects are disclosed.
- Tests include affected players and cover full-session fatigue and recovery.

## 9. Source Basis

These sources support the durable practices above; individual game examples are patterns to evaluate, not universal prescriptions.

- **Microsoft, Xbox Accessibility Guidelines v3.2** — platform-holder guidance developed with industry experts and the Gaming & Disability Community. Version published 2023-06-08; index updated 2026-08-14. Especially XAG 103 (redundant sensory cues), 107 (input), 108 (separable difficulty variables), 116 (non-gameplay time limits), 117 (motion and visual distractions), and 121 (feature documentation): <https://learn.microsoft.com/en-us/xbox/accessibility/guidelines>
- **Game Accessibility Guidelines, Full List** — collaborative practitioner, specialist, and academic checklist; page had no publication date displayed when reviewed 2026-09-05. Used as supporting guidance for remapping, game-speed controls, practice, difficulty changes, and including players with disabilities in tests: <https://gameaccessibilityguidelines.com/full-list/>
- **Supergiant Games, Hades FAQ** — first-party implementation example, reviewed 2026-09-05. Documents always-available God Mode, increasing resilience after deaths, Hell Mode, and the Pact of Punishment; used only to demonstrate that assistance and opt-in challenge can coexist in a run-based game: <https://www.supergiantgames.com/blog/hades-faq/>
