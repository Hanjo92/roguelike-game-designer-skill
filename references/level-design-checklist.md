# Roguelike Level Design Checklist

Load this reference when creating or reviewing a dungeon, biome, floor generator, room set, encounter sequence, or procedural level pipeline.

## 1. Experience Target

- What should the player feel: hunted, clever, lost, powerful, greedy, cautious, or curious?
- Which spatial verbs matter: flank, funnel, retreat, kite, hide, split, hold, jump, or traverse?
- What is the intended floor duration and room count range?
- How does tension rise and fall?
- What distinguishes this biome mechanically, not only visually?

## 2. Progression Graph

- Start and goal nodes are defined
- Critical path length has a target range
- Optional branch count and depth have bounds
- Loops provide navigation or tactical value
- Locks, keys, gates, and one-way transitions are ordered correctly
- Required content remains reachable after irreversible choices
- Secrets have clues and worthwhile but non-mandatory rewards
- Backtracking cost is deliberate

## 3. Geometry

- Traversable space supports the game's movement and attack ranges
- Chokepoints, cover, sightlines, hazards, and elevation have clear purposes
- Entry tiles do not expose players to unavoidable immediate damage
- Exits remain readable during combat
- Camera, UI, and input constraints are respected
- Large rooms and narrow spaces alternate intentionally
- Landmarks support orientation

## 4. Encounter Grammar

For each room, define:

| Field | Question |
|---|---|
| Spatial question | What positioning problem must the player solve? |
| Primary threat | What forces the player to act? |
| Secondary interaction | What complicates the obvious solution? |
| Terrain modifier | How does space change timing or routes? |
| Counterplay | What readable responses are available? |
| Resource consequence | What may be spent, gained, or preserved? |
| Exit condition | When and how does the room end? |

Avoid enemy combinations whose counters are mutually exclusive unless the room provides a third response such as escape, terrain manipulation, or resource expenditure.

## 5. Pacing

Tag rooms by role:

- Teach
- Practice
- Test
- Escalate
- Choice
- Tax
- Recovery
- Reward
- Set piece
- Climax

Validate that:

- New mechanics appear alone before difficult combinations
- High-intensity rooms are separated by decisions or recovery when appropriate
- Rewards arrive close enough to the risks that earned them
- The floor has at least one memorable structural beat
- Optional danger is visibly optional

## 6. Procedural Invariants

Automated validation should check:

- Connectivity and reachability
- Key-before-lock ordering
- Minimum and maximum path lengths
- Spawn safety distance and line of sight
- Threat budget by room and floor segment
- Required resource guarantees
- Duplicate room and pattern limits
- Reward spacing and drought bounds
- Biome-specific room quota
- Navmesh or movement validity
- Interactable accessibility
- Seed determinism

When validation fails, either repair the map, regenerate the invalid layer, or reject the seed with a logged reason. Never silently ship invalid layouts.

## 7. Fairness and Readability

- Threats are visible or announced before commitment
- Hazards use consistent visual and audio language
- Lethal combinations have escape or prevention windows
- Fog of war and hidden information support suspense without erasing planning
- Environmental rules remain consistent
- Color, contrast, text, and sound have accessibility alternatives

## 8. Variety Audit

Measure variation across:

- Topology
- Room geometry
- Threat role combinations
- Terrain interactions
- Objectives
- Reward decisions
- Route trade-offs
- Pacing sequences

A change in decoration alone does not count as gameplay variety.

## 9. Playtest Questions

- Where did the player pause to make a real decision?
- Which damage felt unavoidable, and why?
- Could the player predict the consequence of taking a route?
- Which rooms were solved identically?
- When did the player become lost for non-productive reasons?
- Did optional routes create temptation or merely extra walking?
- Which seed produced the worst pacing, and what invariant was missing?
- Could the player describe the biome's mechanical identity afterward?

## 10. Completion Criteria

A level or generator is ready for the next production stage when representative seeds are completable, progression invariants always pass, threats are readable, pacing falls within target ranges, biome identity is recognizable from play alone, and playtests reveal multiple viable tactical or routing decisions.
