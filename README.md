# Roguelike Game Designer Skill

A portable agent skill for designing and reviewing the wider roguelike family: traditional roguelikes, roguelites, action roguelites, deckbuilders, survivors-likes, tactical and platform roguelites, strategy hybrids, extraction hybrids, and experimental combinations. It covers core loops, procedural generation, combat, builds, progression, economy, difficulty, level design, documentation, and playtesting.

## Files

- `SKILL.md` — main agent instructions
- `references/subgenre-guide.md` — subgenre taxonomy, design priorities, hybrid rules, and diagnostics
- `references/level-design-checklist.md` — detailed procedural and handcrafted level review
- `templates/design-spec.md` — implementation-ready feature/system specification

## Installation

### Claude Code

Copy this directory into a project-level or user-level skills directory supported by your Claude Code setup, keeping `SKILL.md` at the skill root.

### Codex

Copy or symlink this directory into the Codex skills directory used by your environment, then restart the session so skills are rediscovered.

### Antigravity and other agents

If the agent supports the Agent Skills convention, register this directory as a skill root. Otherwise, attach `SKILL.md` as project instructions or reusable context. The file uses standard YAML frontmatter and has no Hermes-specific runtime dependency.

## Example prompts

- “Design a 30-minute turn-based dungeon-crawler run around sound propagation.”
- “Review this relic system for dominant strategies and dead picks.”
- “Create a procedural floor graph with locks, keys, loops, and validation rules.”
- “Turn this boss idea into an implementation-ready design spec.”
- “Why does my roguelite feel repetitive after five runs?”
- “Should this concept be a traditional roguelike, action roguelite, or extraction hybrid?”
- “Adapt this deckbuilder idea into a survivors-like without losing meaningful decisions.”

## License

MIT
