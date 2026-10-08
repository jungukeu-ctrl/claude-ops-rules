# claude-ops-rules

Claude.ai 프로젝트들이 공통으로 참조하는 운영 규칙의 단일 원본 레포입니다.

## 파일

| 파일 | 설명 |
|------|------|
| `system-and-workflow.md` | 세션 초기화, 자동 기록, 프로젝트 초기화, 코드 작업 위임, Notion 사용 불가 시 규칙, 알려진 한계 |
| `templates/index.md` | 프로젝트 메모리용 포인터 템플릿 (Notion URL 기록) |
| `templates/HISTORY.md` | 프로젝트 메모리용 이력 요약 사본 템플릿 (선택, 보조용) |
| `templates/notion-history-entry.md` | Notion HISTORY DB의 속성과 항목 본문 형식 |
| [`MIGRATION.md`](https://raw.githubusercontent.com/jungukeu-ctrl/claude-ops-rules/refs/heads/main/MIGRATION.md) | 기존 프로젝트를 공통 규칙 구조로 이행하는 절차 |

## 구조

이력의 원본은 프로젝트마다 가진 Notion 프로젝트 페이지 아래의 HISTORY 데이터베이스입니다.
프로젝트 메모리는 포인터와 보조 사본일 뿐이며, 모든 프로젝트는 Notion 페이지를 필수로 가집니다.

## 사용 방법

기록이 필요한 모든 프로젝트의 Instructions에 아래 표준 블록을 동일하게 붙여넣습니다.

    ## 공통 운영 규칙
    세션 시작 시 아래 URL을 fetch해서 규칙을 따른다. fetch할 때 URL 끝에 ?d=오늘날짜-임의의 숫자 4자리(예: ?d=20261008-4821)를 붙여 캐시를 우회하고, 브리핑에 규칙 문서 변경 이력의 마지막 줄을 그대로 인용해 한 줄 표시한다.
    https://raw.githubusercontent.com/jungukeu-ctrl/claude-ops-rules/refs/heads/main/system-and-workflow.md
    fetch에 실패하면 아래 요약 규칙만 적용하고, 실패 사실을 사용자에게 알린다.

    요약 규칙:
    - 이 프로젝트의 이력 원본은 Notion HISTORY다. 의사결정, 전략 변경, 미결 생성·해소 시 Notion HISTORY에 기록하고 "HISTORY 기록: 제목 (링크)"를 보고한다.
    - Notion 프로젝트 페이지가 연결되어 있지 않으면 초기 세팅을 먼저 진행한다. Notion 없이 진행하지 않는다.
    - 코드 변경은 직접 쓰지 않고 코드작업지시서로 Claude Code에 위임
    - 세션 시작 시 🔔 미결 항목을 확인해 브리핑

프로젝트 고유 값은 Instructions가 아니라 Notion 프로젝트 페이지와 프로젝트 메모리의 index.md에 둡니다.
코드 프로젝트는 위 블록 아래에 PLAN.md raw URL을 추가합니다.

## 수정 시 주의

- 프로젝트 고유 값(개별 레포 URL, Notion 페이지 ID·URL 등)을 넣지 않습니다.
- 수정 후 raw URL에 반영되기까지 시간이 걸릴 수 있습니다. 1시간 이상 구버전(새 파일은 404)이 반환된 사례도 있습니다.
- 캐시는 URL 끝에 `?d=날짜-임의4자리`(예: `?d=20261008-4821`)를 붙여 우회합니다. 날짜만 쓰면 같은 날 수정한 내용이 안 보일 수 있으니 값을 매번 다르게 씁니다.
- 반영 확인은 `##` 헤딩 목록이 아니라 문서 맨 아래 변경 이력의 마지막 줄로 합니다. 헤딩 목록은 구버전에도 같을 수 있어 버전을 구별하지 못합니다. 브리핑에는 마지막 줄을 그대로 인용합니다.
- 이 레포는 public이어야 Claude.ai가 raw URL을 읽을 수 있습니다. 개인 정보나 계정 정보를 넣지 않습니다.
