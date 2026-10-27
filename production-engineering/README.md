# 생산기술 플러그인 (`production-engineering`)

생산기술 업무 — 작업표준서(다국어 포함), 4M 변경점 신고·초물 검증, 라인 밸런싱·CAPA, 설비·금형·애플리케이터 예방보전, 오류방지, 개선·VA/VE 제안서.

생산기술 담당자가 공정을 표준화하고 변경점을 빠짐없이 관리하도록 돕는다.

> 현대자동차·기아와 무관한 비공식 플러그인이다. 제도 관련 수치는 [HKMC-FACTS.md](HKMC-FACTS.md)의 공개 자료(기준 시점 표기)를 근거로 하며, 고객사가 배포한 최신 기준서가 항상 우선한다.

## 설치

```bash
claude plugin marketplace add muzbox1973/hkmc-supplier-plugins
claude plugin install production-engineering@hkmc-supplier-plugins
```

Claude 데스크톱 앱에서는 플러그인 메뉴에서 이 폴더(또는 압축 파일)를 추가한다.

## 스킬

| 명령 | 하는 일 |
|---|---|
| `/equipment-pm` | 설비·금형·지그·애플리케이터·검사구의 예방보전(PM) 계획, 점검표, 수명 관리대장, 고장 이력 분석(MTBF·MTTR)을 만든다. |
| `/four-m-change` | 4M(사람·설비·재료·방법) 변경점을 고객 신고·승인 대상인지 판단하고, 변경 신청서, 영향·위험 분석, 초물 검증·유동 관리 계획, 관련 문서 개정 목록을 만든다. |
| `/kaizen-proposal` | 현장 개선·원가절감(VA/VE) 제안서를 만든다. |
| `/line-balancing` | 조립 라인의 택트타임, 공정별 작업시간, 라인 밸런스 효율, 필요 인원·설비 대수(CAPA)를 계산하고 병목 해소안을 만든다. |
| `/poka-yoke` | 반복 불량이나 사람 실수에서 생기는 불량을 막는 오류방지(Poka-Yoke) 아이디어를 낸다. |
| `/work-standard` | 공정별 작업표준서(작업지도서)를 작성·개정한다. |

스킬은 관련 요청을 하면 자동으로 쓰이고, 명령(`/production-engineering:스킬이름`)으로 직접 부를 수도 있다.

## 연결 도구

연결 없이 파일 첨부와 대화만으로 작동한다. 그룹웨어·MES·ERP·고객 포털을 연결하면 자료를 직접 가져온다. 자리표시자(`~~groupware` 등)의 뜻은 [CONNECTORS.md](CONNECTORS.md)를 본다. 회사 시스템 이름으로 바꾸려면 `supplier-plugin-builder` 플러그인의 `/customize-for-company`를 쓴다.

## 공통 원칙

- 규격값·기준값은 고객 도면·규격·사양서와 회사 기준에서만 가져오고, 없으면 "확인 필요"로 남긴다.
- 계산은 코드로 실행해 검산한다.
- 고객 도면·단가·개인정보는 회사 정보보안 규정이 허용하는 범위에서만 첨부한다.
