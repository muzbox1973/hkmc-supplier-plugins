# 협력사 품질보증 플러그인 (`supplier-quality`)

현대·기아 협력사 품질보증 업무 — SQ 인증 심사 준비, 8D 개선대책서, 클레임 초동 대응, PFMEA·관리계획서, 공정감사, 품질 실적 보고, 인증 심사, 고객 평가(5스타·SQ) 대응.

품질팀이 고객 평가 제도(SQ·5스타)와 IATF 16949 요구에 맞춰 매일 하는 문서·분석 업무를 돕는다.

> 현대자동차·기아와 무관한 비공식 플러그인이다. 제도 관련 수치는 [HKMC-FACTS.md](HKMC-FACTS.md)의 공개 자료(기준 시점 표기)를 근거로 하며, 고객사가 배포한 최신 기준서가 항상 우선한다.

## 설치

```bash
claude plugin marketplace add muzbox1973/hkmc-supplier-plugins
claude plugin install supplier-quality@hkmc-supplier-plugins
```

Claude 데스크톱 앱에서는 플러그인 메뉴에서 이 폴더(또는 압축 파일)를 추가한다.

## 스킬

| 명령 | 하는 일 |
|---|---|
| `/certification-audit` | IATF 16949, ISO 9001, ISO 14001, ISO 45001 인증 심사(최초·사후·갱신)와 내부심사를 준비한다. |
| `/claim-response` | 고객사 품질 클레임·라인 불량 통보를 받았을 때 첫 24시간 초동 대응을 이끈다. |
| `/customer-rating` | 현대·기아 협력사 평가 제도(1차 협력사 대상 품질·기술·납입 5스타, 2·3차 협력사 대상 SQ 인증)와 1차 협력사가 하는 하위 협력사 정기 평가에 대비해, 회사 실적을 평가 지표별로 정리하고 등급 하락 위험과 개선 과제를 찾는다. |
| `/eight-d-report` | 고객 클레임·공정 부적합·필드 불량에 대한 8D 개선대책서(시정조치 보고서)를 작성하거나 검토한다. |
| `/pfmea-control-plan` | 공정 FMEA(PFMEA)와 관리계획서(Control Plan)를 작성·검토·개정한다. |
| `/process-audit` | 자체 공정감사와 계층별 공정감사(LPA) 체크리스트를 만들고, 감사 결과를 지적사항·시정조치 보고서로 정리한다. |
| `/quality-kpi-report` | 월간·주간 품질 실적 보고서를 만든다. |
| `/sq-audit-prep` | 현대·기아 2·3차 협력사의 SQ 인증 심사(신규·갱신)를 준비한다. |

스킬은 관련 요청을 하면 자동으로 쓰이고, 명령(`/supplier-quality:스킬이름`)으로 직접 부를 수도 있다.

## 연결 도구

연결 없이 파일 첨부와 대화만으로 작동한다. 그룹웨어·MES·ERP·고객 포털을 연결하면 자료를 직접 가져온다. 자리표시자(`~~groupware` 등)의 뜻은 [CONNECTORS.md](CONNECTORS.md)를 본다. 회사 시스템 이름으로 바꾸려면 `supplier-plugin-builder` 플러그인의 `/customize-for-company`를 쓴다.

## 공통 원칙

- 규격값·기준값은 고객 도면·규격·사양서와 회사 기준에서만 가져오고, 없으면 "확인 필요"로 남긴다.
- 계산은 코드로 실행해 검산한다.
- 고객 도면·단가·개인정보는 회사 정보보안 규정이 허용하는 범위에서만 첨부한다.
