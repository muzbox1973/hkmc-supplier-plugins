# 신차 개발·APQP 플러그인 (`new-product-development`)

신차·신규 품번 개발 업무 — APQP 일정 역산, 초도품(ISIR) 제출 서류, 도면·사양 검토와 고객 질의서, 설계변경 영향 분석, 개발 이슈·단계 점검.

개발·선행품질 담당자가 고객 개발 이벤트(T카·Proto·P1·P2·M·SOP)에 맞춰 준비하는 일을 돕는다.

> 현대자동차·기아와 무관한 비공식 플러그인이다. 제도 관련 수치는 [HKMC-FACTS.md](HKMC-FACTS.md)의 공개 자료(기준 시점 표기)를 근거로 하며, 고객사가 배포한 최신 기준서가 항상 우선한다.

## 설치

```bash
claude plugin marketplace add <이 저장소 경로 또는 GitHub 주소>
claude plugin install new-product-development@hkmc-supplier-plugins
```

Claude 데스크톱 앱에서는 플러그인 메뉴에서 이 폴더(또는 압축 파일)를 추가한다.

## 스킬

| 명령 | 하는 일 |
|---|---|
| `/apqp-timeline` | 신차·신규 품번 개발 일정을 APQP 5단계와 완성차 개발 이벤트(T카·Proto·P1·P2·M·SOP 등)에 맞춰 짜고, 금형·설비·지그 준비, 초도품 제출, 양산 승인까지 역산 일정과 위험 항목을 만든다. |
| `/design-change` | 고객 설계변경(EO·도면 개정) 통보를 받았을 때 영향 범위를 분석하고 적용 계획을 세운다. |
| `/dev-issue-tracker` | 개발 단계(시작·파일럿·선행양산) 이벤트별 품질·조립성 이슈를 모아 이슈 리스트로 관리하고, 이벤트 전 단계 점검(Gate Review) 자료와 고객 개발 회의 보고서를 만든다. |
| `/drawing-review` | 고객 도면·사양서(ES·MS 같은 고객 규격 번호 포함)를 받아 제조 타당성을 검토한다. |
| `/isir-package` | 현대·기아 공급망의 초도품 승인(ISIR) 제출 서류를 준비·점검한다. |

스킬은 관련 요청을 하면 자동으로 쓰이고, 명령(`/new-product-development:스킬이름`)으로 직접 부를 수도 있다.

## 연결 도구

연결 없이 파일 첨부와 대화만으로 작동한다. 그룹웨어·MES·ERP·고객 포털을 연결하면 자료를 직접 가져온다. 자리표시자(`~~groupware` 등)의 뜻은 [CONNECTORS.md](CONNECTORS.md)를 본다. 회사 시스템 이름으로 바꾸려면 `supplier-plugin-builder` 플러그인의 `/customize-for-company`를 쓴다.

## 공통 원칙

- 규격값·기준값은 고객 도면·규격·사양서와 회사 기준에서만 가져오고, 없으면 "확인 필요"로 남긴다.
- 계산은 코드로 실행해 검산한다.
- 고객 도면·단가·개인정보는 회사 정보보안 규정이 허용하는 범위에서만 첨부한다.
