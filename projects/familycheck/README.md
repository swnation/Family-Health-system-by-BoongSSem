# familycheck

가족 건강관리 시스템의 주 구현 프로젝트입니다.

## 빠른 개요

- **목표:** 가족 구성원의 건강 기록, 체크, AI 보조 흐름을 한 시스템 안에서 안전하게 운영
- **아키텍처 방향:** Firebase 기반, Cloud Functions 중심, 데이터와 권한은 시스템별로 독립 유지
- **AI 비용 통합:** `shared/patterns/cost-tracking-v1.md` 표준 준수. event ledger + monthly aggregate + billing reconciliation. familycheck가 가격표 hub 역할
- **연계 프로젝트:** `cost-dashboard`가 familycheck와 향후 다른 시스템들의 비용 aggregate를 읽어 합산 뷰 제공

## 현재 상태

- 범위 확장 결정(D14 계열)까지 정리됨
- AI 비용 추적 공통 패턴이 active 승격됨
- 다음 단계는 cost-tracking 표준의 familycheck 구현 작업분해와 MVP endpoint 착수

## 참조 표준

familycheck가 구현 시 준수해야 하는 공통 패턴:

| 문서 | 상태 | 설명 |
|------|------|------|
| [`shared/patterns/cost-tracking-v1.md`](../../shared/patterns/cost-tracking-v1.md) | active | AI 비용 추적 공통 표준. familycheck가 가격표 hub 구현 필수. event ledger + aggregate + billing reconciliation |

## 관련 문서

- `projects/familycheck/sessions/2026-04-23-claude-familycheck-02.md`
- `projects/familycheck/decisions/2026-04-17-initial-scope-and-stack.md`
- `projects/familycheck/decisions/2026-04-17-gpt-redteam-feedback.md`
- `projects/familycheck/decisions/2026-04-17-scope-expansion.md`
- `projects/familycheck/design/overview-v1.md`

## 다음 세션 TODO

- [ ] cost-tracking-v1 표준 구현
  - [ ] `costEvents` (POST, GET) Cloud Function
  - [ ] `costAggregates` (GET) Cloud Function
  - [ ] `costReconcile` (POST, mode=live|dry-run) Cloud Function
  - [ ] 가격표 hub: `/config/price_tables/`, `/config/price_tables_meta/active`
  - [ ] Security Rules (Cloud Function write only)
  - [ ] Onboarding 검증 스크립트
