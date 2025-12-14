# appendix/state_board.md — State Board (v1.1)

이 문서는 프로젝트의 “현재 상태를 한 장으로 고정”하기 위한 표준입니다.
목표: 컨텍스트 전환(모델/툴/날짜)이 있어도 **한 파일만 보면 지금 무엇을 해야 하는지** 알게 만들기.

## 1) 파일 위치
프로젝트 루트에 `STATE.md`를 생성합니다.

## 2) STATE.md 표준 스키마 (템플릿)
아래 템플릿을 그대로 복사해 `STATE.md`로 사용하세요.

```markdown
# STATE — <project_name>

## Goal
- (한 문장) 이 프로젝트는 무엇을 만든다.

## Deliverables
- [ ] deliverable 1 (형식/분량 포함)
- [ ] deliverable 2

## Constraints
- Must:
  - ...
- Must NOT:
  - ...
- Format/Style:
  - ...

## Tools / Stack
- primary tools:
- secondary tools:
- export target:

## Current Step
- step_id: 1
- step_name: (WORKPLAN의 단계명)
- done_definition: (무엇이면 '완료'인가)

## Next Step
- step_id:
- step_name:

## Open Questions
- Q1:
- Q2:

## Risks
- risk: / mitigation:

## Recent Decisions (last 5)
- YYYY-MM-DD: decision → reason

## Current Files of Truth
- WORKPLAN.md
- OUTLINE.md
- SOURCES.md
- LOG.md
```

## 3) 업데이트 규칙 (안정성 핵심)
1) **한 번에 한 섹션만** 업데이트한다. (충돌 방지)
2) “Current Step”은 반드시 WORKPLAN과 동기화한다. (둘 중 하나가 진실)
3) Decision은 LOG에도 남기고, STATE에는 “최근 5개만” 유지한다.

## 4) 언제 STATE를 쓰면 좋은가
- 프로젝트가 3일 이상 지속될 때
- 산출물이 2개 이상일 때
- 글/연구/코드가 섞이는 하이브리드 작업일 때
- 팀/학생과 협업하여 “현재 상태 공유”가 필요할 때

## 5) 에이전트용 지시(짧게)
- 어떤 질문이 와도 먼저 STATE를 확인하고 “Goal/Constraints/Current Step”을 기준으로 답한다.
- STATE가 없다면 생성부터 제안한다.
