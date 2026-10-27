# Connectors (연결 도구)

## 도구 표기 방식

플러그인 파일은 `~~분류` 형태의 자리표시자로 도구를 가리킨다. 예를 들어 `~~groupware`는 회사가 쓰는 그룹웨어(전자결재·메일·게시판)를 뜻한다.
플러그인은 특정 제품에 묶이지 않는다. 회사마다 쓰는 시스템이 다르므로, 설치 후 `supplier-plugin-builder` 플러그인의 `/customize-for-company`로 자리표시자를 실제 시스템 이름으로 바꾼다.

국내 그룹웨어·MES·ERP 대부분은 아직 공식 MCP 서버가 없다. 연결이 없으면 각 스킬은 **파일 첨부(엑셀, PDF, 한글·워드 문서)와 대화 입력만으로 작동**한다. 사내 MCP 서버를 만들면 아래 분류에 맞춰 `.mcp.json`에 등록한다.

## 분류별 자리표시자

| 분류 | 자리표시자 | 예시 |
|---|---|---|
| 그룹웨어 | `~~groupware` | 사내 그룹웨어(전자결재·게시판), Microsoft 365, Google Workspace |
| 메일 | `~~email` | 그룹웨어 메일, Outlook, Gmail |
| 메신저 | `~~chat` | 사내 메신저, Microsoft Teams, Slack, 카카오워크 |
| 생산관리 | `~~MES` | 사내 MES, 공정 실적·불량 실적 시스템 |
| 경영관리 | `~~ERP` | SAP, 더존, 영림원 등 |
| 문서 저장소 | `~~document storage` | 사내 NAS, SharePoint, Google Drive |
| 고객 포털 | `~~customer portal` | 고객사(1차 협력사 또는 완성차)가 운영하는 협력사 포털 |
| 스프레드시트 | `~~spreadsheet` | Excel, Google Sheets |

## 보안 원칙

- 고객 도면, 사양서, 단가, 개인정보는 회사 정보보안 규정이 허용하는 범위에서만 첨부한다.
- 고객 포털 계정 정보는 플러그인 파일에 적지 않는다. 인증이 필요한 서버는 환경변수로 받는다.
