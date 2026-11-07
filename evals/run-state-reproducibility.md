# Evaluation: Run State and Reproducibility

## Prompt

> 45분짜리 덱빌딩 로그라이트야. 자동 저장은 방을 나갈 때 마스터 시드와 HP, 골드, 덱만 기록해. 보스 보상은 먼저 계정에 지급하고 나중에 런 저장을 갱신해. 보상 창을 다시 열면 후보를 새로 뽑아. QA는 같은 시드면 재현된다고 하는데, 카드 패치 후나 중간에 종료했다가 이어 하면 다른 결과가 나와. 영구 사망은 유지하면서 저장·복구·버그 재현 명세와 테스트 계획을 만들어줘. 소규모 싱글플레이 팀이라 온라인 서버나 전 플랫폼 결정론을 전제로 하지 마.

## Mandatory Checks

- Distinguishes seeded generation, suspend/resume, deterministic replay, and diagnosis
- Explains why the seed plus HP/gold/deck omits authoritative state and current RNG state
- Specifies safe boundaries or pending-resolution serialization
- Restores offered choices, claim state, pool eligibility, pity/banish/director histories where relevant
- Defines stable settlement IDs and recoverable run/account cost-and-grant reconciliation
- Prevents duplicate grants or charges when interruption occurs around each commit boundary
- Preserves permadeath without treating suspend as death or silently rerolling on load
- Defines versioned seed claims and an explicit patch/mod compatibility policy with original-save preservation
- Includes save round-trip, uninterrupted/resumed continuation, interrupted write, and migration-retry tests
- Captures ordered actions, versions, settings, checkpoint context, and first divergence in a privacy-safe packet
- Scopes determinism to supported systems and keeps implementation within a small solo-game budget

## Strong Response Signals

- Separates normalized authoritative comparisons from volatile presentation data
- Tests an early exit from the reward/game-over UI without losing or duplicating earned value
- Notes that balance A/B changes may consume RNG differently even with the same seed
- Uses a fixed regression corpus plus exploratory seeds and clearly labels untested implementation claims

## Critical Failures

- Claims a master seed alone guarantees resume or cross-version replay
- Permits a repeated reward grant or free reroll through ordinary load
- Deletes progression or forces death as the default solution to normal interruption
- Assumes an online service or cross-platform lockstep despite the stated production scope
