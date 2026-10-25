---
name: routines
description: 레포의 .workflow/routines/ 폴더(James 루틴)를 만들고 관리한다 — 초기화, 루틴 추가, 튜닝 내용을 어느 층에 둘지 판단, 점검(lint), James Job 등록·동기화. "루틴 만들어줘", "이 프로젝트에 정기 업무 걸어줘", "루틴 고쳐줘", "루틴 점검" 요청 시 사용.
---

# james-routines — 루틴 폴더 관리

루틴은 James가 정기적으로 돌리는 업무다. 프로젝트에 붙는 업무는 그 레포의 `.workflow/routines/`에 파일로 정의하고, 프로젝트에 속하지 않는 업무는 James Vault의 `routines/`에 둔다. 파일이 원본이고, 실행 상태(켜짐, 다음 실행, 이력, 비용)는 James가 들고 있다.

## 1. 구조

```
<repo>/.workflow/routines/
├── _project.md      # 이 프로젝트 루틴 전부에 적용되는 사실·금지사항
├── build.md         # 업무 하나 = 파일 하나 (스케줄 단위)
├── ship.md
└── grow.md
```

내용은 4개 층으로 나뉜다. 뒤쪽 층이 앞쪽을 덮어쓴다.

| 층 | 무엇 | 어디 |
|---|---|---|
| ① 스킬 | 업무 절차 (어떻게) | 플러그인 또는 `~/.claude/skills` |
| ② 프로필 | 잡 종류별 스킬·MCP 묶음 + 짧은 공통 지침 | James Context Preset |
| ③ 프로젝트 공통 | 경로, 계정, 키 위치, 제품 사실의 출처, 금지사항 | `_project.md` |
| ④ 루틴 | 스케줄, 실행 설정, 이번 기간 목표, 단계별 튜닝 | `<업무>.md` |

## 2. 배치 규칙 (가장 중요)

새 지시나 튜닝을 받으면 먼저 어느 층에 들어갈지 정한다.

- 모든 프로젝트에 해당한다 → ①이나 ②. 이 폴더에 쓰지 않는다
- 이 프로젝트의 모든 업무에 해당한다 → ③ `_project.md`
- 한 업무에만 해당한다 → ④ 그 루틴 파일
- 한 업무 안의 한 단계에만 해당한다 → ④ 파일 안의 해당 `## 단계` 섹션

정리할 때는 이렇게 끌어올린다.
- 여러 루틴 파일에 같은 내용이 반복되면 `_project.md`로 올린다
- 여러 프로젝트의 `_project.md`에 같은 내용이 반복되면 스킬이나 프로필로 올리자고 사용자에게 제안한다

절대 규칙
- **include 금지.** 파일에서 다른 파일을 끌어오는 문법을 만들지 않는다. 참고 자료는 경로만 적고, 실행 중인 에이전트가 직접 읽게 한다
- **비밀값 금지.** 토큰, 비밀번호, API 키 값을 적지 않는다. 키체인 항목 이름이나 키 파일 위치만 적는다
- **유추 금지.** 경로, 앱키, URL은 실측한 값만 적는다. 모르면 사용자에게 묻거나 `(미확인)`으로 남긴다
- **루틴 본문에는 기본값과 다른 점만 적는다.** 본문이 2,000자를 넘으면 무언가 층을 잘못 들어온 것이다

## 3. 작업별 절차

### 초기화 (`_project.md`가 없을 때)

1. 레포의 README, `.workflow/steering/`, `docs/`, 기존 `.workflow` 문서를 읽고 프로젝트 사실을 모은다
2. 업무에 필요한 외부 위치(볼트 문서, 대시보드, 데이터 소스)를 사용자에게 확인한다
3. [templates.md](references/templates.md)의 `_project.md` 템플릿으로 파일을 만든다

### 루틴 추가

1. 업무 이름과 그 업무를 수행할 스킬(`run`)을 정한다. 스킬이 없으면 사용자에게 알린다. 절차를 루틴 본문에 길게 쓰는 걸로 대신하지 않는다
2. 템플릿으로 `<업무>.md`를 만든다. frontmatter는 §4 표를 따른다
3. 같은 레포에서 이미 돌고 있는 루틴과 스케줄이나 대상이 겹치는지 확인한다
4. James Job 등록은 §5를 따른다

### 튜닝

1. §2 배치 규칙으로 어느 층, 어느 섹션에 넣을지 정한다
2. 그 섹션만 고친다. 다른 섹션이나 다른 파일은 다시 쓰지 않는다
3. ①②층에 넣어야 할 내용이면 직접 고치지 않고 사용자에게 제안한다
4. frontmatter를 바꿨다면 §5 동기화를 한다

### 점검 (lint)

다음을 확인해서 문제만 보고한다.
- frontmatter 필수 키(`name`, `schedule`, `run`)가 있는지, 모르는 키는 없는지
- 본문 2,000자 초과, 비밀값처럼 보이는 문자열, include 같은 문법
- 루틴끼리 반복되는 문장 (→ `_project.md`로 올릴 후보)
- 루틴 파일과 James Job 설정이 어긋나는지 (`job_list`/`job_get`과 대조)
- `run`이 가리키는 스킬이 이 컴퓨터에 있는지

## 4. 루틴 frontmatter ↔ James Job

| frontmatter | James `job_create` / `job_update` |
|---|---|
| `name` | `name` |
| `schedule` (cron) / `at` (ISO) | `cron` / `at` (Asia/Seoul) |
| `run` | `prompt` |
| `model`, `effort` | `model`, `effort` |
| `budgetUsd`, `maxTurns` | `maxBudgetUsd`, `maxTurns` |
| `approval` | `approval` (`wait`/`acceptEdits`/`bypass`) |
| `overlap`, `missed` | `overlap`, `missed` |
| `outputs.todos`, `outputs.todoOnFailure` | `allowTodos`, `todoOnFailure` |
| `outputs.vault` | `vaultPath` |
| (레포 경로) | `projectPath` |

## 5. James Job 등록·동기화

James가 아직 루틴 파일을 직접 읽지 않는다. 그때까지는 이 스킬이 파일 내용을 Job으로 옮긴다.

- **등록:** `job_create`로 등록하고 바로 `job_toggle(false)`로 꺼둔다. 켤지는 사용자가 정한다. 같은 루틴 파일이 여러 컴퓨터에 퍼지기 때문에, 실행할 컴퓨터에서만 켜야 한다
- **식별:** Job 이름은 루틴의 `name`과 똑같이 한다. 그래야 다시 찾을 수 있다
- **동기화:** frontmatter를 바꾸면 같은 이름의 Job을 찾아 `job_update`로 맞춘다. 본문만 바뀐 경우는 할 일이 없다 (실행할 때 스킬이 파일을 읽는다)
- **시험 실행:** 사용자가 원하면 `job_run`으로 1회 돌리고 결과(`job_run_get`)를 함께 확인한다
- **삭제:** 루틴 파일을 지울 때는 Job도 지울지 사용자에게 확인한다

## 6. 프로젝트 없는 루틴

리서치나 SNS처럼 특정 레포에 속하지 않는 업무는 James Vault의 `routines/`에 같은 구조로 둔다. `_project.md`는 도메인 공통 사실이고, Job의 `projectPath`는 `none`이다.
