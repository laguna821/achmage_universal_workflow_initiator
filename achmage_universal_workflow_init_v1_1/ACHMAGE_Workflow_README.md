# ACHMAGE_Workflow_README.md v1.1
> 이 파일은 사람(휴먼) 기준의 상세 매뉴얼입니다. 실제 스킬 엔트리포인트는 같은 폴더의 `SKILL.md`를 사용하세요.

## 1) What this is
이 문서는 어떤 작업이든(글쓰기/리서치/코딩/행정/콘텐츠 제작) **“프로젝트 OS처럼”** 시작할 수 있게 해주는 범용 워크플로우 이니시에이터입니다. 핵심은 간단합니다: **(1) 5문항 인터뷰 → (2) 폴더+템플릿 자동 생성 → (3) WORKPLAN 기반 실행 루프**. v1.1에서는 fewweekslater 스타일의 장점(상태보드/라우팅/품질 게이트)을 **모듈(appendix)로만 흡수**하여, 안정성과 유지보수성을 해치지 않으면서도 더 깊게 확장할 수 있게 했습니다.

## 2) Quick start (3 steps)
1. 아래 **Bootstrap Interview(5문항)**에 답한다. (모르면 기본값으로 진행)
2. 에이전트에게 “프로젝트 루트 폴더 + 5개 핵심 파일(WORKPLAN/BRIEF/OUTLINE/SOURCES/LOG)”을 생성하게 한다.
3. `WORKPLAN.md` 1단계를 실행하고, 결과를 **Inspect → Fix → Log** 루프로 개선한다.

## 3) Bootstrap Interview (≤5 questions)
아래 5문항만으로 프로젝트 초기화를 끝냅니다. 답변이 비어 있으면 기본값으로 채우고 계속 진행합니다.

1) **Goal & Deliverable**: 최종적으로 무엇을 만들고 싶나요? (기본값: “샘플 연습 프로젝트”)
2) **Domain / Topic**: 주제/분야/배경은 무엇인가요? (기본값: “일반 주제”)
3) **Constraints**: 필수 조건/금지 조건/분량/형식 제약이 있나요? (기본값: “특별한 제약 없음”)
4) **Tools / Format**: 선호 도구/스택/출력 형식이 있나요? (기본값: “표준 도구 + Markdown”)
5) **Timeline / Depth**: 기한/완성도/깊이는 어느 정도인가요? (기본값: “1주 내 기본 수준”)

## 4) Answer → Workflow Mapping
인터뷰 답변으로 project_type과 scaffold를 결정합니다.

| project_type | 대표 신호 | 기본 폴더 | 핵심 파일(항상) | 조건부 추가 |
|---|---|---|---|---|
| writing | 소설/에세이/원고/강의노트/스크립트 | (root) | WORKPLAN/BRIEF/OUTLINE/SOURCES/LOG | drafts/ (챕터/버전 관리 필요 시) |
| research | 논문/리뷰/분석/조사/IRB/리포트 | (root) | 동일 | data/, references/ |
| coding | 앱/웹/스크립트/자동화/패키지 | (root) | 동일 | src/, tests/ |
| general | 혼합/모호/기획 | (root) | 동일 | 필요 시 최소만 |

**복잡도 레벨(선택):**
- L1(간단): 핵심 5파일만 생성하고 바로 실행
- L2(표준): 조건부 폴더 + 품질 게이트 일부 적용
- L3(심화): State Board + Command Router + Quality Gates(appendix 사용)

## 5) Generation Algorithm (pseudocode)
결정론적으로 생성합니다. 동일한 답변이면 동일한 산출을 목표로 합니다.

```
INPUT: answers(Q1..Q5)

1. Fill defaults for missing answers.
2. Infer project_type from keywords and constraints.
3. Derive project_name (snake_case) from goal/topic, else "my_project".
4. Create project root folder.
5. Always create:
   - WORKPLAN.md, BRIEF.md, OUTLINE.md, SOURCES.md, LOG.md
6. Conditionally create folders:
   - writing -> drafts/
   - research -> data/, references/
   - coding -> src/, tests/ (if testing required)
7. Populate files:
   - BRIEF.md: 목적/범위/대상/성공기준
   - OUTLINE.md: 구조(목차/모듈/섹션)
   - SOURCES.md: 출처/링크/참고(없으면 placeholder)
   - LOG.md: 날짜/행동/결정/다음액션 템플릿
   - WORKPLAN.md: 단계별 계획(각 단계 산출물/검토 기준 포함)
8. Print tree + next action: "Proceed with WORKPLAN Step 1?"
```

## 6) Execution Loop (quality control)
WORKPLAN을 실행하는 동안 “완료”는 한 번에 오지 않습니다. 아래 루프를 반복합니다.

1. **Run**: WORKPLAN의 현재 step을 수행해 산출물을 만든다.
2. **Inspect**: 산출물이 목표/제약/형식에 맞는지 점검한다.
3. **Fix**: 결함/누락을 수정한다.
4. **Log**: LOG.md에 무엇을 했고 무엇을 바꿨는지 기록한다.
5. **Advance**: 다음 step으로 이동한다.

**품질 게이트(선택):**
- writing: `appendix/quality_writing.md`
- research: `appendix/quality_research.md`
- coding: `appendix/quality_coding.md`

## 7) Progressive Disclosure (optional appendices)
v1.1의 고급 기능은 **필요할 때만** 켭니다. (핵심은 여전히 5문항+스캐폴드입니다)

### 7.1 Advanced Mode: State Board (권장)
장기 프로젝트나 잦은 컨텍스트 전환이 있다면 `STATE.md`를 도입합니다.
- 스키마/작성 규칙: `appendix/state_board.md`
- 운영 원칙: STATE는 “현재 한 장”, LOG는 “역사 전체”

### 7.2 Advanced Mode: Command Router (선택)
툴/모델을 바꿔도 동일한 명령으로 동일한 동작을 유도하려면 커맨드 라우터를 씁니다.
- 명령어 표준: `appendix/command_router.md`
- 예: `.init`, `.scaffold`, `.plan`, `.run step=2`, `.review`, `.export format=pdf`

### 7.3 Advanced Mode: Quality Gates (권장)
산출물 품질이 들쭉날쭉하거나 팀/학생이 같이 쓰는 경우, 품질 게이트로 안정성을 올립니다.
- writing/research/coding 각각 체크리스트는 appendix에 분리되어 있습니다.

### 7.4 Optional Modules (확장 슬롯)
프로젝트가 커질수록 README를 비대하게 만들지 말고, 아래 원칙을 따릅니다.
- appendix는 1-depth만 허용(README → appendix까지만)
- 새 모듈은 “파일 1개 = 기능 1개”로 분리
- 모듈 네이밍은 `appendix/<topic>_<purpose>.md` (예: `domain_novel_plot.md`)

### 7.5 How to run (tool-agnostic prompts)
아래 프롬프트를 어떤 환경에서도 그대로 붙여 넣어 시작할 수 있습니다.

- 초기화:
  - “이 폴더의 SKILL.md와 ACHMAGE_Workflow_README.md를 읽고, 5문항 인터뷰를 진행한 뒤 scaffold를 생성해줘.”
- 실행:
  - “WORKPLAN.md step 1을 실행하고, Inspect→Fix→Log 루프로 개선해줘.”

## 8) Safety & Guardrails
- 원격 fetch/다운로드/패키지 설치/쉘 실행/코드 실행은 **항상 사용자 승인 후** 진행합니다.
- 비밀정보(API 키/비밀번호/토큰)는 요구하거나 저장하지 않습니다. 필요하면 사용자가 로컬 `.env`에 넣도록 안내합니다.
- 애매한 요구는 기본값으로 진행하되, 중요한 결정(범위 확대/외부 실행)은 중간 확인을 받습니다.

## 9) Version + Changelog
- v1.0: 5문항 + 기본 스캐폴드 + 실행 루프
- v1.1: Advanced 기능을 appendix로 모듈화(State Board, Command Router, Quality Gates)하여 “더 길고 체계적”이면서도 유지보수성을 확보
