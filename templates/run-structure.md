# [Game / Mode] — Run Structure

## Run Contract

- Target duration and acceptable range:
- Structure: [acts / floors / missions / waves / days]
- Restart cost:
- Primary skill:
- Build identity target time:
- Specialization target time:
- Climax target time:
- Failure lesson:
- Global viability guarantees:

## Stage Arc

| Stage | Duration | Player state | Main decision | Threat band | Reward / recovery | Exit condition |
|---|---:|---|---|---:|---|---|
| Orientation |  |  |  |  |  |  |
| Formation |  |  |  |  |  |  |
| Commitment |  |  |  |  |  |  |
| Stress test |  |  |  |  |  |  |
| Transformation |  |  |  |  |  |  |
| Climax |  |  |  |  |  |  |
| Resolution |  |  |  |  |  |  |

## Beat Grammar

Allowed beats:

```text
Teach → Practice → Choice → Test → Reward
```

- Maximum repeated high-intensity beats:
- Recovery spacing:
- Shop / conversion spacing:
- Optional-risk spacing:
- Invalid beat sequences:

## Build and Reward Milestones

| Milestone | Target window | Guarantee | Allowed variance | Repair option |
|---|---:|---|---|---|
| First meaningful choice |  |  |  |  |
| First enabler |  |  |  |  |
| First defensive tool |  |  |  |  |
| Build identity |  |  |  |  |
| Specialization payoff |  |  |  |  |
| Pre-climax preparation |  |  |  |  |

## Power and Threat Bands

| Stage | Weak viable power | Median power | Strong realistic power | Base threat | Outlier threat | Recovery capacity |
|---|---:|---:|---:|---:|---:|---:|
|  |  |  |  |  |  |  |

## Act / Biome Contract

| Act or biome | Mechanical identity | New rule | Spatial grammar | Enemy emphasis | Economy modifier | Boss test |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

## Route Structure

| Route | Visible information | Threat / uncertainty | Reward class | Opportunity cost | Reconnection |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

## Recovery Budget

- Maximum intended power deficit:
- Health / defense recovery:
- Economy recovery:
- Build repair:
- Squad / deck / inventory repair:
- Cost of recovery:
- Practical irrecoverability rule:
- Maximum play after irrecoverability:

## Run Director

### Inputs

- [ ] Run stage and elapsed time
- [ ] Recent beat and encounter history
- [ ] Reward and recovery droughts
- [ ] Build tags and solution classes
- [ ] Resource trajectory
- [ ] Performance budget

### Allowed interventions

- [Define permitted interventions]

### Forbidden interventions

- [Define prohibited interventions]

### Candidate scoring

```text
candidate_score =
```

### Hard constraints before scoring

- [Define hard constraints]

## Instrumentation

- Time to first decision:
- Time to build identity:
- Reward and recovery drought:
- Beat repetition:
- Director intervention log:
- Practical irrecoverability point:
- Time after irrecoverability:

## Representative Seed Tests

| Seed / scenario | Weak build | Median build | Strong build | Expected pacing | Result |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

## Acceptance Criteria

- [ ] Opening reaches meaningful play inside the target window
- [ ] Every legal run can access at least one viable solution class
- [ ] Build formation and repair milestones fall inside allowed ranges
- [ ] Acts or biomes change decisions, not only presentation
- [ ] Difficulty spikes have preparation and recovery context
- [ ] Director obeys hard constraints and logs interventions
- [ ] No route is globally dominant across representative states
- [ ] Climax tests accumulated mastery without hidden build requirements
