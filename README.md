# claude-ops-rules

Claude.ai 프로젝트들이 공통으로 참조하는 운영 규칙의 단일 원본 레포입니다.

## 파일

| 파일 | 설명 |
|------|------|
| `system-and-workflow.md` | 세션 초기화, 프로젝트 초기화, 자동 기록 트리거, 코드 작업 위임 패턴, 알려진 한계 |
| `templates/HISTORY.md` | 프로젝트 메모리용 의사결정 이력 템플릿 |
| `templates/index.md` | 프로젝트 메모리용 자원 지도 템플릿 |

## 사용 방법

모든 프로젝트의 Instructions에 아래 표준 블록을 동일하게 붙여넣습니다.

    ## 공통 운영 규칙
    세션 시작 시 아래 URL을 fetch해서 규칙을 따른다.
    https://raw.githubusercontent.com/jungukeu-ctrl/claude-ops-rules/main/system-and-workflow.md
    fetch에 실패하면 아래 요약 규칙만 적용하고, 실패 사실을 사용자에게 알린다.

    요약 규칙:
    - 의사결정, 전략 변경, 미결 생성·해소 시 HISTORY.md에 자동 기록
    - 코드 변경은 직접 쓰지 않고 코드작업지시서로 Claude Code에 위임
    - 세션 시작 시 HISTORY.md, index.md가 없으면 초기 세팅 여부를 묻고, 🔔 미결 항목을 확인해 브리핑

프로젝트 고유 내용(개요 등)은 Instructions가 아니라 프로젝트 메모리의 index.md에 둡니다.
코드 프로젝트는 위 블록 아래에 PLAN.md raw URL과 Notion URL을 추가합니다.

## 수정 시 주의

- 프로젝트 고유 값(개별 레포 URL, Notion 페이지 ID 등)을 넣지 않습니다.
- 수정 후 raw URL에 반영되기까지 최대 15분이 걸릴 수 있습니다.
- 이 레포는 public이어야 Claude.ai가 raw URL을 읽을 수 있습니다. 개인 정보나 계정 정보를 넣지 않습니다.
