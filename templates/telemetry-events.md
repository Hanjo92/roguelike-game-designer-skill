# Telemetry Event Catalog

## Global Envelope

Every event should include:

| Field | Type | Required | Meaning |
|---|---|---:|---|
| event_name | string | yes | Stable snake_case identifier |
| schema_version | integer | yes | Event payload version |
| event_id | UUID/string | yes | Deduplication identifier |
| sequence | integer | yes | Order within session or run |
| timestamp | ISO-8601 / epoch | yes | Event time |
| anonymous_player_id | string | yes | Privacy-safe identifier |
| session_id | string | yes | Application session |
| run_id | string | when in run | Run instance |
| game_version | string | yes | Executable version |
| content_version | string | yes | Content database version |
| seed | string/integer | when relevant | Reproduction seed |
| generation_version | string | when relevant | Generator behavior version |
| stage_id | string | when relevant | Act/floor/wave/day |
| location_id | string | when relevant | Room/node/mission |
| difficulty_id | string | yes | Difficulty configuration |
| account_power_band | string | yes | Persistent progression segment |
| build_tags | array<string> | when relevant | Current strategy context |

Do not place personal text, names, chat, or unnecessary device identifiers in payloads.

## Event Definition Template

### `event_name`

- **Decision supported:**
- **Fire condition:**
- **Before/after semantics:**
- **Deduplication:**
- **Save/load behavior:**
- **Required context:**

| Payload field | Type | Required | Meaning / allowed values |
|---|---|---:|---|
|  |  |  |  |

- Validation rules:
- Known biases:
- Retention requirement:

## Minimum Events

### `run_started`

Payload: starting character/loadout, difficulty modifiers, initial account band, seed, selected mode.

### `node_offered`

Payload: all node choices, visible threat/reward categories, route depth, weights in development builds only.

### `node_selected`

Payload: selected node, offered alternatives, current resources and build tags.

### `encounter_started`

Payload: encounter ID, room ID, enemy roles, threat estimate, player power estimate, entry resources.

### `reward_offered`

Payload: all rewards, rarity, tags, source, reroll count, current build context.

### `reward_resolved`

Payload: selected/skipped/salvaged reward, alternatives, reason if explicitly provided, resulting build tags.

### `resource_changed`

Payload:

| Field | Meaning |
|---|---|
| resource_id | Stable resource identifier |
| delta | Signed change |
| balance_after | Resulting amount |
| source_id | Origin system or content |
| sink_category | Purchase, ability, repair, loss, conversion, etc. |
| reason | Stable enum, not free text |

### `shop_action`

Payload: shop ID, offers, prices, action type, purchased/sold/rerolled/locked item, balance before and after.

### `build_state_changed`

Payload: added/removed tags, power estimate before/after, triggering content, archetype classifier confidence if used.

### `player_damaged`

Payload: amount before/after mitigation, source, attack, damage tags, player state, position bucket, avoidability classification only if rule-based.

### `boss_phase_reached`

Payload: boss/phase ID, elapsed fight time, resources, build tags, damage taken, retries.

### `run_ended`

Payload: outcome, cause, stage, elapsed active time, final build, resources, practical-irrecoverability estimate, extracted/secured value.

### `restart_or_exit`

Payload: action, time since run end, mode destination. Do not infer emotional reason without explicit research data.

## Schema Rules

- Events are append-only; change meaning only through a new schema version.
- Enumerations use stable IDs, not localized display strings.
- Monetary and resource deltas state units and rounding.
- Chained effects preserve root and immediate source IDs.
- Offline buffering preserves event ID and sequence.
- Duplicate delivery is expected and deduplicated by event ID.
- Development-only fields are marked and removed from production if sensitive or costly.

## Validation Checklist

- [ ] Every event supports a named design decision
- [ ] Fire condition is unambiguous
- [ ] Before/after value semantics are explicit
- [ ] Save/load and retry duplication behavior is defined
- [ ] Stable content IDs are used
- [ ] Seed and generation version support reproduction
- [ ] Segmentation context is sufficient
- [ ] No unnecessary personal data is collected
- [ ] Schema evolution and retention are defined
- [ ] Sample event can be reconstructed into the intended funnel
