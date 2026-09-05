# [Game / Mode] — Accessibility and Difficulty Matrix

## 1. Challenge Contract

- Player promise:
- Host genre's primary skill:
- Required decisions to preserve:
- Target audiences and platforms:
- Competitive / cooperative / solo context:
- Explicit non-goals:

## 2. Barrier Audit

| Mechanic / state | Intended decision | Access demand | Affected players / contexts | Failure consequence | Barrier or protected challenge? |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

Consider perception, cognition, input, timing, precision, endurance, sensory load, attrition, and loss severity.

## 3. Presets and Independent Axes

| Option / axis | Category | Exact effect | Range / presets | Default | Changeable when? | Persists where? |
|---|---|---|---|---|---|---|
|  | Accessibility / difficulty / challenge |  |  |  | Before run / safe room / pause / always | Profile / save / run |

- Preset composition:
- Custom preset behavior:
- Reset-to-default behavior:
- Discovery / recommendation rule:
- Non-shaming player-facing description:

## 4. Input and Timing

- Action-level remapping:
- Alternate input methods:
- Hold / mash / simultaneous-input alternatives:
- Sensitivity and dead-zone ranges:
- Aim / steering / target assistance:
- Game-speed range:
- Pause behavior:
- Clock contract:

| System | Simulation time | Real time | Input time | UI time | Behavior when speed or pause changes |
|---|---:|---:|---:|---:|---|
|  |  |  |  |  |  |

## 5. Information and Sensory Channels

| Critical state / cue | Visual | Audio / caption | Haptic | Timing / persistence | Reduced-effects behavior |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

- Color-independent distinctions:
- Text size / contrast / background:
- Screen narration scope:
- Subtitle and caption controls:
- Camera motion / shake / blur controls:
- Flashing and photosensitivity controls:
- Effect-density and crowd-readability controls:

## 6. Run Lifecycle

### Before first run

- Settings access and supported input:
- Feature preview / documentation:
- Tutorial and practice access:

### During run

- Safe settings-change points:
- Save-and-quit / resume contract:
- Route, reward, and build-choice reading time:
- Assist recommendation behavior:

### Failure and restart

- Lost and retained state:
- Death explanation channels:
- Practice / replay behavior:
- Time to meaningful retry:
- Settings retained across death / prestige / new save:

## 7. Systemic and Procedural Compatibility

| Assist combination / profile | Changed state space | Invariants | Exploit / invalid-state risk | Batch or scenario test |
|---|---|---|---|---|
|  |  |  |  |  |

Check topology, traversal, cooldowns, damage-over-time, spawns, physics, boss phases, economy conversions, reward guarantees, target selection, save/load, and deterministic replay.

## 8. Rewards and Online Rules

| Feature / mode | Achievement impact | Reward impact | Record / leaderboard handling | Matchmaking / disclosure |
|---|---|---|---|---|
|  |  |  |  |  |

- Rationale for any restriction:
- Information shown before opt-in:
- Mid-run change handling:

## 9. Player Test Plan

- Decision this test informs:
- Participant group and relevant lived experience:
- Recruitment, compensation, consent, and accessible setup:
- Input device / assist profile:
- Seed / build / account state / run stage:
- Representative session duration and fatigue check:
- Configuration, play, failure, save/quit, and restart tasks:
- Observation categories: [perception / comprehension / decision / execution / fatigue / technical]
- Success criteria:
- Guardrails:
- Follow-up and revert threshold:

## 10. Acceptance Criteria

- [ ] Protected decisions and removable barriers are distinguished
- [ ] Settings are available before the first run and persist through the failure loop
- [ ] Essential accessibility and usability are not progression-gated
- [ ] Important difficulty axes can be adjusted without changing unrelated skills
- [ ] Critical cues use redundant channels and survive reduced-effects settings
- [ ] Input alternatives address speed, complexity, duration, and precision—not remapping alone
- [ ] Every timer has a clock contract
- [ ] Supported assist combinations pass procedural, balance, and save/load invariants
- [ ] Achievement, reward, leaderboard, and multiplayer effects are disclosed before selection
- [ ] Players with relevant disabilities test the complete configuration-to-restart journey
