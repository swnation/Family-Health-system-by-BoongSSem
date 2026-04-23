# cost-dashboard

여러 독립 시스템의 AI 비용 데이터를 읽어 합산 뷰를 제공하는 소비자 프로젝트입니다.

## 준수 표준

**`shared/patterns/cost-tracking-v1.md` (active, 2026-04-23)** — 이 표준을 구현한 시스템들의 비용 데이터를 읽어와 합산 뷰 제공.

## 확장 구조

- 각 시스템(familycheck, 오랑붕쌤, 향후 시스템 X/Y/Z)은 자기 Firestore에 독립적으로 event/aggregate 보관
- cost-dashboard는 system registry를 통해 각 시스템을 등록하고 OIDC service account 기반 read-only 호출
- 새 시스템 추가 절차: 해당 시스템이 표준 구현 → onboarding 검증 9개 통과 → registry entry 추가 → 자동 합산 편입
- 확장 예상: clinical-assist, 개인 실험 프로젝트, 외주 프로젝트 등

## 구현 상태

- 설계: 완료 (`shared/patterns/cost-tracking-v1.md` 참조)
- 구현: 대기 중 (familycheck MVP 구현 후 이어서 진행 예정)

## 서브도메인 상태

| 서브도메인 | 상태 | 설명 |
|---|---|---|
| [cost-widget](./cost-widget/) | 설계 대기 | 신규 위젯, 표준 기반 구현 예정 |
| [dashboard](./dashboard/) | 설계 대기 | 합산 뷰 + system registry 관리 UI |
| [legacy-claude-widget](./legacy-claude-widget/) | 참고용 | 기존 앱, 포맷만 차용 |

## 관련 문서

- `shared/patterns/cost-tracking-v1.md`
- `projects/familycheck/sessions/2026-04-23-claude-familycheck-02.md`
