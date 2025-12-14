# achmage_universal_workflow_init_v1_1  
**“5문항 + 폴더 + 마크다운” — 이렇게나 심플한데, 이렇게나 강력합니다.**

이 레포는 **어떤 작업이든**(글쓰기/리서치/코딩/행정/콘텐츠 제작) 시작할 때,  
AI가 **먼저 ‘워크플로우’를 설계하고** 그 다음에 **그 워크플로우대로 실행**하게 만드는 **범용 워크플로우 이니시에이터(Workflow Initiator)** 입니다.

핵심 아이디어는 단 하나입니다.

> **프로젝트는 ‘답’부터 내지 말고, 먼저 ‘운영체제(OS)’부터 깔아라.**  
> (폴더 구조 + 템플릿 + 실행 계획 + 품질 게이트)

---

## 이게 뭐가 그렇게 강력한가?

대부분의 AI 협업은 이렇게 망가집니다:

- “일단 만들어줘” → 결과가 들쭉날쭉  
- 자료/대본/프롬프트/파일이 흩어짐  
- 다음날 다시 열면 “어디까지 했지?”  
- 팀/학생에게 넘기면 그대로 재현이 안 됨

이 레포는 반대로 갑니다.

✅ **5문항 인터뷰**로 목표/제약/도구/기한을 확정하고  
✅ **WORKPLAN.md**로 단계별 실행 계획을 만들고  
✅ **BRIEF/OUTLINE/SOURCES/LOG**로 프로젝트의 “뼈대”를 고정합니다.  

그리고 필요하면(선택)  
✅ **STATE Board(STATE.md)**로 “현재 상태를 한 장으로” 유지하고  
✅ **Command Router(.init/.scaffold/.plan/.run …)**로 모델/툴이 바뀌어도 같은 명령으로 굴리며  
✅ **Quality Gates**로 결과 품질을 안정화합니다.

결과적으로, **AI가 ‘작업자’가 아니라 ‘오케스트레이터’가 됩니다.**

---

## 폴더/파일 구성

레포 루트에는 7개가 있습니다:

- `SKILL.md`  
  - 에이전트가 “언제 이 스킬을 써야 하는지” 판단하는 **엔트리포인트(관문)**  
- `ACHMAGE_Workflow_README.md`  
  - 사람이 읽고 그대로 따라할 수 있는 **상세 매뉴얼(본체)**  
- `appendix/`  
  - 고급 기능 모듈(필요할 때만 열어보는 방식)
  - `state_board.md` : STATE.md(상태보드) 스키마
  - `command_router.md` : `.init/.scaffold/.plan/.run/...` 명령 표준
  - `quality_writing.md / quality_research.md / quality_coding.md` : 품질 게이트

---

## Quick Start (3분 컷)

### 1) 새 프로젝트 폴더에 이 레포 파일을 “워크플로우 팩”으로 넣기
예시 구조(추천):

```plaintext
my_workspace/
├── workflow_pack/              # ← 여기에 이 레포 파일들 그대로 복사
└── projects/
    └── my_project/             # ← 여기가 실제 프로젝트 산출물 폴더
````

### 2) Codex(또는 VS Code 에이전트)에게 “워크플로우부터 만들라”라고 시키기

아래 프롬프트를 그대로 붙여넣으세요.

```text
workflow_pack/SKILL.md 와 workflow_pack/ACHMAGE_Workflow_README.md 를 읽고 따라줘.
appendix/command_router.md의 명령 체계를 사용해.

지금부터 .init → .scaffold → .plan 순서로 진행해.
- .init: 5문항을 나에게 하나씩 질문해.
- .scaffold: projects/my_project/ 아래에 폴더+템플릿을 만들어.
- .plan: WORKPLAN.md를 매우 구체적으로 작성해(단계별 산출물/체크리스트 포함).

시작: .init
```

### 3) 실행은 “WORKPLAN.md”대로

생성된 `projects/my_project/WORKPLAN.md`의 Step 1부터 실행하면 됩니다.
실행 중에는 이 루프만 기억하면 됩니다:

> **Run → Inspect → Fix → Log → Advance**

---

## “계획은 Codex, 실행은 Antigravity/Gemini” 분업(추천 사용법)

이 레포는 분업에 최적화되어 있습니다.

* **Codex(또는 다른 모델)**: 워크플로우/폴더/계획을 “파일로 고정” (설계 엔진)
* **Gemini(antigravity 내부)**: 웹서치/이미지 생성 등 “실행” (실행 엔진)

Gemini에 붙여 넣을 마스터 실행 프롬프트 예시:

```text
projects/my_project/WORKPLAN.md, SOURCES.md, OUTLINE.md, LOG.md를 열어보고
WORKPLAN Step 1부터 순서대로 실행해줘.

규칙:
- 웹서치는 공신력 있는 출처 위주로 하고 SOURCES.md에 기록.
- 각 단계가 끝날 때마다 LOG.md에 수행 내용과 다음 행동을 한 줄로 업데이트.
- 외부 실행/다운로드/대량 생성은 먼저 나에게 확인해.
시작: WORKPLAN Step 1 실행.
```

---

## 예시: “90초 AI 영상 제작 워크플로우” 만들기

이 레포의 진짜 힘은 이런 복합 작업에서 터집니다:

1. 주제 선정
2. 공신력 있는 자료 조사
3. 90초 대본(타임코드) 작성
4. 샷 리스트(이미지 시퀀스) 설계
5. 샷별 프롬프트 생성
6. 순차 생성/저장
7. 품질 점검

권장 프로젝트 구조 예시:

```plaintext
ai_video_project/
├── WORKPLAN.md
├── BRIEF.md
├── OUTLINE.md
├── SOURCES.md
├── LOG.md
├── research/
├── script/
├── storyboard/
├── prompts/
└── assets/
    ├── images/
    └── video/
```

Codex는 여기까지 “설계+생성”을 담당하고,
Gemini는 “웹서치+이미지 생성+저장”을 담당하면 됩니다.

---

## Advanced (선택 기능, 필요할 때만)

### 1) STATE Board (장기 프로젝트에 강추)

* 프로젝트 루트에 `STATE.md`를 만들고
* `appendix/state_board.md` 템플릿을 그대로 복사해 사용하세요.

**효과:** “내일 다시 열어도 5초 만에 상황 복구”

### 2) Command Router (팀/수업 운영에 강추)

* `.init / .scaffold / .plan / .run step=N / .review / .export` 같은 명령으로
* 어떤 모델/툴을 쓰든 동일한 운영이 가능해집니다.

### 3) Quality Gates (품질 안정화)

* writing/research/coding 각각의 체크리스트로
* 결과물의 들쭉날쭉함을 줄입니다.

---

## 이 레포가 “해주지 않는 것” (정직한 한계)

이 레포는 **실행 엔진**이 아니라 **운영 규격 + 실행 설계도**입니다.

* 외부 툴(API/CLI)이 있다면 자동화 수준을 더 높일 수 있지만,
* 기본 형태는 “파일 기반 오케스트레이션”입니다.
* 즉, **워크플로우는 자동 생성되고**, 실행은 환경에 따라 **자동/반자동**이 됩니다.

---

## 한 문장 요약

**“AI에게 일을 시키기 전에, 일을 ‘돌아가게 하는 구조’를 먼저 시키세요.”**
그게 이 레포의 전부이고, 그래서 강력합니다.
