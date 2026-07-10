# Evaluation: Procedural Generation

## Prompt

> 로그라이크 플랫폼 게임의 레벨을 WFC로 전부 자동 생성하고 싶어. 플레이어는 이단 점프와 벽 점프를 런 중에 해금할 수 있어. 알고리즘과 구현 규칙을 설계해줘.

## Mandatory Checks

- States that WFC handles local compatibility, not global progression or solvability
- Separates ability-aware progression graph from geometry realization
- Defines connector contracts and traversal tests using actual movement physics
- Handles levels generated before and after ability acquisition
- Includes hard invariants, bounded retries, repair, and fallback
- Preserves deterministic seeds and layer-specific random streams
- Defines logging and batch metrics
- Covers blind jumps, camera, spawn safety, and incompatible chunks

## Strong Response Signals

- Recommends graph/mask first plus constrained WFC or prefab realization
- Defines which layer can be regenerated without perturbing the rest
- Includes known-valid fallback segments

## Critical Failure

Claims WFC alone guarantees a playable and solvable level.
