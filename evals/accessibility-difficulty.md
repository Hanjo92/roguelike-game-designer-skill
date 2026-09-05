# Scenario: Accessible Challenge Without a Global Easy Mode

## Prompt

> Our 35-minute real-time action roguelite is built around reading enemy tells, choosing routes, and committing to risky close-range attacks. Players report barriers from color-only tells, rapid repeated button presses, dense VFX, and losing an entire run when they cannot suspend play. The team does not want one global easy mode or an assist that chooses routes or attacks automatically. Propose an accessibility and difficulty specification that preserves the intended decisions. Include procedural and timing risks, what persists after death, and a practical test plan for a six-person indie team.

## Mandatory Checks

- Names the protected decisions before proposing options
- Separates perception, input, timing, sensory-load, and consequence barriers
- Uses redundant cues that do not depend on color alone
- Provides alternatives to mashing and defines game-speed or timing clock behavior
- Distinguishes save-and-quit from rewind or rollback
- Keeps essential accessibility outside progression unlocks and persistent across runs
- Tests supported assist combinations against generation, encounter, economy, and save/load invariants
- Includes players with relevant disabilities and tests fatigue across a representative session
- Discloses any effect on achievements, rewards, records, or multiplayer

## Critical Failures

- Proposes only enemy health/damage reduction
- Automates route or attack decisions despite the stated boundary
- Removes telegraphs or accessibility features in order to preserve prestige
- Requires repeated deaths or currency to unlock needed access settings
- Assumes changing game speed cannot affect physics, cooldowns, spawns, or damage-over-time
