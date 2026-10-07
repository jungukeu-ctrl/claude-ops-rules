# claude-ops-rules

Claude.ai 프로젝트들이 공통으로 참조하는 운영 규칙의 단일 원본 레포입니다.

## 파일

| 파일 | 설명 |
|------|------|
| `system-and-workflow.md` | 세션 초기화, 자동 기록 트리거, 코드 작업 위임 패턴, 알려진 한계 |

## 사용 방법

각 프로젝트의 Instructions에 아래 URL을 등록하고, 세션 시작 시 fetch하도록 지시합니다.

https://raw.githubusercontent.com/jungukeu-ctrl/claude-ops-rules/main/system-and-workflow.md

## 수정 시 주의

- 프로젝트 고유 값(개별 레포 URL, Notion 페이지 ID 등)을 넣지 않습니다.
- 수정 후 raw URL에 반영되기까지 최대 15분이 걸릴 수 있습니다.
- 이 레포는 public이어야 Claude.ai가 raw URL을 읽을 수 있습니다. 개인 정보나 계정 정보를 넣지 않습니다.
