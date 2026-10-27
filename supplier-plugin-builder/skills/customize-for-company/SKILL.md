---
name: customize-for-company
description: 이 플러그인 모음을 우리 회사에 맞게 고친다. ~~자리표시자를 실제 시스템 이름(그룹웨어·MES·ERP·고객 포털)으로 바꾸고, 회사 정보(1·2차 협력사 위치, 업종, 보유 인증, 사업장, 결재 라인, 용어, 양식)를 company-context 파일로 만들어 각 스킬이 참고하게 한다. "플러그인 회사 맞춤", "우리 회사용으로 바꿔줘", "자리표시자 바꾸기", "회사 정보 설정", "플러그인 커스터마이즈"라고 할 때 사용한다.
argument-hint: "<고칠 플러그인 이름 또는 '전체'>"
---

# /customize-for-company

> 자리표시자 목록은 [CONNECTORS.md](../../CONNECTORS.md)에 있다.

## 1. 회사 정보 수집

[references/company-context-template.md](references/company-context-template.md)의 항목을 질문으로 바꿔 한 번에 묻는다. 사용자가 회사 소개서, 조직도, 품질 매뉴얼을 첨부하면 거기서 먼저 채우고 빈 칸만 묻는다. 모르는 항목은 비워 둔다.

## 2. 자리표시자 교체

대상 플러그인 폴더에서 `~~`로 시작하는 자리표시자를 찾는다:

```bash
grep -rn '~~[A-Za-z]' <플러그인 폴더> --include='*.md' --include='*.json'
```

분류별로 묶어 사용자에게 실제 이름을 확인한 뒤 바꾼다. 연결할 MCP 서버가 없으면 이름만 바꾸고, `.mcp.json`은 비워 둔다. 사내 MCP 서버 주소를 받으면 `.mcp.json`에 등록하고 인증 정보는 환경변수로 받도록 한다.

## 3. company-context 파일 작성

채운 회사 정보를 각 플러그인 루트의 `COMPANY-CONTEXT.md`로 저장하고, 각 SKILL.md 상단 참고 줄에 "회사 맞춤 정보는 `../../COMPANY-CONTEXT.md`를 참고한다"를 마크다운 링크 형식으로 추가한다.

## 4. 양식 반영

회사 양식(8D, 4M 신청서, 작업표준서, 기안문)을 받으면 해당 스킬의 "출력 형식" 블록을 그 양식 항목 순서로 바꾼다. 스킬 이름과 폴더 이름은 바꾸지 않는다.

## 5. 점검

- `claude plugin validate <플러그인 폴더>`를 실행할 수 있으면 실행하고, 없으면 plugin.json JSON 유효성과 각 SKILL.md 프런트매터(name, description)를 직접 확인한다
- 남은 `~~` 자리표시자 목록을 보고한다

## 주의

- 고객 기밀(도면 번호, 단가)과 개인정보는 플러그인 파일에 넣지 않는다. 플러그인은 여러 사람에게 배포될 수 있다.
