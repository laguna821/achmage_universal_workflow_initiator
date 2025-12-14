# appendix/command_router.md — Command Router (v1.1)

목표: 어떤 모델/툴에서도 동일한 명령으로 동일한 동작을 유도하기.
원칙: 명령은 단순하게, 출력은 고정되게.

## 1) 명령 표준
| Command | Purpose | Output |
|---|---|---|
| `.init` | 5문항 인터뷰 시작 | Q1~Q5 질문 |
| `.scaffold` | 폴더/템플릿 생성 | tree + 생성 파일 요약 |
| `.plan` | WORKPLAN 구체화/재작성 | WORKPLAN.md 업데이트 |
| `.run step=N` | N단계 실행 | 해당 산출물 + 다음 액션 |
| `.review` | 품질 게이트 점검 | pass/fail + fix list |
| `.log` | 변경 요약 기록 | LOG.md 업데이트(또는 텍스트 제공) |
| `.export format=pdf/docx/html` | 내보내기 가이드 | 실행 전 승인 요청 |

## 2) 리라이트 규칙(명령이 없을 때)
사용자 요청이 명령 형태가 아니라면, 에이전트는 내부적으로 가장 가까운 명령으로 변환합니다.
- “계획 세워줘” → `.plan`
- “폴더/파일 만들어줘” → `.scaffold`
- “다음 단계 진행” → `.run step=<current+1>`

## 3) 충돌 방지 규칙(안정성 핵심)
- 한 턴에는 **명령 1개만** 수행한다. (예: `.plan`과 `.run`을 동시에 하지 않음)
- `.export`는 항상 사용자 승인 후에만 실행한다.
- `.review` 결과가 fail이면 `.run`으로 진행하지 않고 fix 먼저 한다.

## 4) 팀/수업 운영 팁
- 학생/팀에게는 “명령어 3개만 먼저”(.init/.scaffold/.run) 알려주고,
  익숙해지면 .review/.export를 추가합니다.
