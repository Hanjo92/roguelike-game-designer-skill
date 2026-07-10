# Procedural Generation Algorithm Guide

Load this reference when selecting, combining, implementing, or evaluating procedural generation for maps, rooms, caves, overworlds, missions, encounters, items, or run structure.

## 1. Select by Design Goal

Never choose an algorithm because it is fashionable or easy to demo. First define:

- Topology: linear, branching, looping, hub, layered, or open
- Navigation fantasy: explore, descend, infiltrate, escape, conquer, or survive
- Spatial verbs and combat ranges
- Required pacing and authored beats
- Locks, keys, shortcuts, secrets, and one-way transitions
- Destructibility and simulation requirements
- Content budget and authoring workflow
- Runtime budget, determinism, and debugging needs

Generate in layers: **progression graph → role assignment → geometry → population → validation and repair**.

## 2. Algorithm Selection Table

| Method | Best for | Strengths | Main risks |
|---|---|---|---|
| Random walk / drunkard's walk | Organic caves and winding spaces | Simple, connected tendency, tunable density | Blobs, weak pacing, poor room identity |
| Cellular automata | Natural caves and terrain fields | Organic silhouettes, cheap iteration | Disconnected regions, narrow artifacts |
| BSP | Room-and-corridor dungeons | Reliable partitioning, clear rooms | Repetitive rectangular structure |
| Room packing + corridors | Authored room grammar | Strong room control, flexible topology | Placement failure and corridor ugliness |
| Graph-first generation | Run paths, locks/keys, missions | Direct control of progression and pacing | Geometry realization can fail |
| Maze algorithms | Labyrinths and constrained navigation | Guaranteed connectivity properties | Repetitive, few tactical spaces |
| Wave Function Collapse | Local pattern-consistent layouts | Strong visual/style coherence | Contradictions, weak global pacing |
| Grammar-based generation | Structured levels and missions | Expressive hierarchy and rules | Rule complexity, debugging difficulty |
| Voronoi / Delaunay | Regions, overworlds, irregular networks | Natural adjacency and territories | Requires semantic post-processing |
| Noise fields | Terrain, biomes, resource distributions | Continuous multi-scale variation | Noise is not gameplay structure |
| Prefab/chunk assembly | Platforming, action rooms, production control | Validated pieces, predictable quality | Repetition and seam constraints |
| Constraint solving / search | Puzzles and hard guarantees | Can enforce global requirements | Computational cost and authoring burden |

Hybrid pipelines are usually stronger than a single algorithm.

## 3. Random Walk

### Use when

- Organic connected spaces matter more than explicit rooms
- A cave, ruin, trail, or excavated feeling is desired
- Fast prototypes or masks are needed

### Tuning knobs

- Walker count
- Step bias and momentum
- Turn probability
- Carve radius
- Branch probability
- Target fill percentage
- Boundary behavior

### Safeguards

- Post-process width and accessibility
- Detect large open blobs and uninteresting tunnels
- Place progression structure separately
- Validate path length and combat-space dimensions

Random walk should generate geometry or a mask, not be expected to create pacing by itself.

## 4. Cellular Automata

### Use when

Organic cave fields, cover patches, islands, corruption, or destructible terrain are desired.

Typical process:

1. Seed wall/floor probability.
2. Iterate neighborhood birth/survival rules.
3. Label connected components.
4. Keep, connect, or repurpose components.
5. Smooth only where it preserves gameplay dimensions.
6. Place progression and encounters afterward.

Validate connectivity, minimum corridor width, reachable area, spawn clearance, and line-of-sight characteristics.

## 5. Binary Space Partitioning

### Use when

Readable rooms, hierarchical regions, and guaranteed non-overlap are valuable.

Process:

1. Recursively split a rectangular region using size and aspect constraints.
2. Place one or more rooms in leaf regions.
3. Connect sibling regions.
4. Add optional loops across branches.
5. Assign room roles based on the progression graph.

Vary split ratios, room shapes, corridor routing, skipped leaves, merged cells, and landmarks to avoid uniformity. BSP guarantees partition structure, not interesting combat or pacing.

## 6. Room Packing and Prefab Assembly

### Use when

Room quality, traversal validity, camera framing, and authored encounter control outweigh free-form geometry.

Define connector contracts:

- Position, orientation, width, and height
- Traversal abilities required
- Camera and sightline assumptions
- Entry safety volume
- Biome and pacing tags
- Allowed neighbors
- Spawn, hazard, and reward sockets

Use backtracking or repair when no compatible chunk remains. Track room history and motif quotas to prevent repetition. For platformers, validate every connection under the actual movement model and current ability set.

## 7. Graph-First Generation

### Use when

Route choice, locks and keys, branches, loops, mission beats, or guaranteed progression dominate.

Represent nodes with semantic roles and edges with traversal conditions. Generate:

1. Critical path length range
2. Optional branches and reconnection loops
3. Gate/key dependencies as a directed acyclic dependency graph
4. Room roles and reward placements
5. Geometry realization
6. Validation and repair

Graph invariants should be testable before geometry exists. If realization fails, retry geometry without discarding a valid high-level graph when possible.

## 8. Maze Algorithms

Common choices:

- **Depth-first backtracker:** long corridors, strong single-path feeling
- **Prim:** many short branches, organic maze texture
- **Kruskal:** controllable merging and region connections
- **Recursive division:** strong walls and macro structure

A perfect maze has one route between any two cells and therefore no loops. Add loops, rooms, landmarks, and semantic dead ends when tactical routing or exploration requires them.

## 9. Wave Function Collapse

### Use when

Local adjacency, tile style, architectural grammar, or visual coherence is the primary problem.

WFC does not inherently understand critical paths, pacing, locks, combat spaces, or solvability. Supply those through constraints, a pre-generated mask/graph, tagged modules, or post-validation.

Required practices:

- Curate adjacency rules from intentional examples
- Weight patterns and control rare motifs
- Pin entrances, goals, landmarks, and reserved spaces
- Detect contradictions and bound retries
- Log decision and backtracking history
- Validate global gameplay properties afterward

Use backtracking, localized reset, fallback tiles, or hierarchical generation rather than restarting the entire level indefinitely.

## 10. Grammar-Based Generation

Use graph grammars, shape grammars, or mission grammars when content follows compositional rules.

Example:

```text
Floor → Entrance + Development + Climax
Development → Teach + Test + Reward
Test → Combat | Hazard | Objective
Combat → PrimaryThreat + OptionalModifier + CounterplaySpace
```

Rules should carry constraints, tags, budgets, and termination conditions. Guard against recursive expansion, unreachable states, and combinations that are grammatically valid but tactically unfair.

## 11. Voronoi, Delaunay, and Noise

### Voronoi / Delaunay

Use for regions, territories, biome cells, roads, settlement networks, or irregular rooms. Delaunay edges provide candidate connectivity; prune and augment them according to travel, pacing, and loop goals.

### Noise

Use Perlin, Simplex, fractal noise, ridged noise, or domain warping for continuous fields such as elevation, moisture, temperature, density, and biome tendency.

Noise should feed semantic classification and gameplay constraints. Do not mistake a plausible terrain image for a playable world. Validate slope, traversal, resource access, landmark distribution, and route cost.

## 12. Constraint Solving and Search

Use SAT/SMT, answer-set programming, exact cover, evolutionary search, or custom backtracking when hard global constraints dominate—especially puzzles, key-lock plans, tactical scenarios, and content schedules.

Separate:

- Hard constraints that must never fail
- Soft constraints with weighted preferences
- Optimization goals
- Time and retry limits
- Fallback behavior

A solver needs explainable failure reporting. Log which constraint set became unsatisfiable.

## 13. Population Algorithms

Do not uniformly scatter content. Use:

- Room-role sockets
- Poisson-disc sampling for spacing
- Influence maps for danger, visibility, access, or thematic intensity
- Threat budgets and role quotas
- Conditional probability by run state
- History-aware anti-repeat selection
- Guaranteed placements before optional random placements

Population must respect entry safety, line of sight, path clearance, objective access, and performance budgets.

## 14. Validation and Repair

Every pipeline should validate:

- Connectivity and reachability
- Key-before-lock order
- Critical and optional path ranges
- Traversal under current abilities
- Spawn safety and line of sight
- Room dimensions for movement and combat
- Threat, reward, and recovery distribution
- Duplicate and motif quotas
- Biome identity
- Performance and entity limits
- Seed determinism

Repair strategies:

- Connect components with targeted corridors
- Move or replace invalid gates, keys, spawns, or rewards
- Swap an incompatible prefab
- Widen or simplify traversal
- Regenerate only the failed layer or region
- Fall back to a known-valid authored segment
- Reject the seed with a reason after a bounded retry count

Never allow an unbounded generation retry loop.

## 15. Determinism and Debugging

Record:

- Master seed
- Derived seed per generation layer
- Algorithm version
- Content database version
- Parameters and constraints
- Rejected attempts and reasons
- Repair operations
- Final validation report

Use separate random streams so changing decoration does not silently alter topology or rewards. Provide developer commands to reproduce a seed, freeze layers, visualize graphs and influence maps, and batch-test thousands of seeds.

## 16. Evaluation

Batch metrics should include:

- Generation time and retry count
- Validation failure by reason
- Path length and branch distribution
- Loop, dead-end, and room-role counts
- Traversable area and spatial dimension distributions
- Threat/reward/recovery spacing
- Motif repetition
- Content coverage
- Outlier seeds

Automated metrics find invalid or extreme levels. Human playtests determine readability, pacing, tactical interest, surprise, and aesthetic coherence.

## 17. Selection Recipes

- **Traditional dungeon:** graph-first progression + room packing/BSP + corridor repair + role-based population
- **Organic cave:** cellular automata or random walk + component connection + semantic room detection
- **Action arena run:** graph-first pacing + validated prefab rooms + threat-budget population
- **Platform roguelite:** ability-aware progression graph + traversal-tested chunks + connector backtracking
- **Overworld:** Voronoi/Delaunay regions + noise fields + route and resource validation
- **Puzzle floor:** authored templates or constraint solver + strict solvability validation
- **Style-coherent interior:** graph/mask first + WFC realization + global gameplay validation

## Completion Criteria

An algorithm choice is justified when it maps to explicit topology, pacing, traversal, content, production, and runtime requirements; lists its failure modes; defines generation layers, invariants, repair and fallback behavior; preserves deterministic reproduction; and includes batch metrics plus human playtest questions.
