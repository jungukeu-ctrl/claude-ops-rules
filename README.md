# claude-ops-rules

Claude.ai 프로젝트들이 공통으로 참조하는 운영 규칙의 단일 원본 레포입니다.

## 파일

| 파일 | 설명 |
|------|------|
| `system-and-workflow.md` | 세션 초기화, 자동 기록, 프로젝트 초기화, 코드 작업 위임, Notion 사용 불가 시 규칙, 알려진 한계 |
| `templates/index.md` | 프로젝트 메모리용 포인터 템플릿 (Notion URL 기록) |
| `templates/HISTORY.md` | 프로젝트 메모리용 이력 요약 사본 템플릿 (선택, 보조용) |
| `templates/notion-history-entry.md` | Notion HISTORY DB의 속성과 항목 본문 형식 |
| [`MIGRATION.md`](MIGRATION.md) | 기존 프로젝트를 공통 규칙 구조로 이행하는 절차 |

## 구조

이력의 원본은 프로젝트마다 가진 Notion 프로젝트 페이지 아래의 HISTORY 데이터베이스입니다.
프로젝트 메모리는 포인터와 보조 사본일 뿐이며, 모든 프로젝트는 Notion 페이지를 필수로 가집니다.

## 사용 방법

기록이 필요한 모든 프로젝트의 Instructions에 아래 표준 블록을 동일하게 붙여넣습니다.

    ## 공통 운영 규칙
    세션 시작 시 아래 Notion 페이지를 열어 "현재 해시"를 읽는다.
    https://app.notion.com/p/3f368e1fa04c81b4b5a9f9e85c79cf69
    읽은 해시로 https://raw.githubusercontent.com/jungukeu-ctrl/claude-ops-rules/{해시}/system-and-workflow.md 를 fetch해서 규칙을 따른다. 쿼리 파라미터는 붙이지 않는다. 브리핑에 규칙 문서 변경 이력의 마지막 줄을 그대로 인용해 한 줄 표시한다.
    Notion 페이지를 읽지 못하거나 fetch에 실패하면 아래 요약 규칙만 적용하고, 실패 사실을 사용자에게 알린다.

    요약 규칙:
    - 이 프로젝트의 이력 원본은 Notion HISTORY다. 의사결정, 전략 변경, 미결 생성·해소 시 Notion HISTORY에 기록하고 "HISTORY 기록: 제목 (링크)"를 보고한다.
    - Notion 프로젝트 페이지가 연결되어 있지 않으면 초기 세팅을 먼저 진행한다. Notion 없이 진행하지 않는다.
    - 코드 변경은 직접 쓰지 않고 코드작업지시서로 Claude Code에 위임
    - 세션 시작 시 🔔 미결 항목을 확인해 브리핑

프로젝트 고유 값은 Instructions가 아니라 Notion 프로젝트 페이지와 프로젝트 메모리의 index.md에 둡니다.
코드 프로젝트는 위 블록 아래에 PLAN.md raw URL을 추가합니다.

## 수정 시 주의

- 프로젝트 고유 값(개별 레포 URL, Notion 페이지 ID·URL 등)을 넣지 않습니다.
- `refs/heads/main` 계열 raw URL은 캐시로 오래된 내용을 줄 수 있어 쓰지 않습니다. 항상 커밋 해시 URL을 씁니다.
- 규칙을 수정해 push한 뒤에는 반드시 Notion "공통 규칙 버전" 페이지의 해시를 새 커밋 해시로 갱신해야 모든 프로젝트에 반영됩니다. (갱신 절차는 system-and-workflow.md 8장 참고)
- 반영 확인은 `##` 헤딩 목록이 아니라 문서 맨 아래 변경 이력의 마지막 줄로 합니다. 헤딩 목록은 구버전에도 같을 수 있어 버전을 구별하지 못합니다. 브리핑에는 마지막 줄을 그대로 인용합니다.
- 이 레포는 public이어야 Claude.ai가 raw URL을 읽을 수 있습니다. 개인 정보나 계정 정보를 넣지 않습니다.
