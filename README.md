# HKMC Supplier Plugins — 현대·기아 협력사 업무 플러그인 모음

Claude를 **현대·기아 협력사(1·2·3차)의 직무 전문가**로 바꾸는 오픈소스 플러그인 모음이다. Anthropic의 [knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) 구조(플러그인 = 스킬 + 연결 도구 + 문서)를 그대로 따르면서, 미국 IT 기업 기준이던 내용을 국내 자동차 부품 협력사 업무(SQ 인증, 5스타, 4M 변경점, 초도품(ISIR), 8D, 와이어링 하네스 압착 등)로 바꿨다. Claude 데스크톱 앱(Cowork)과 Claude Code에서 모두 쓸 수 있다.

> **비공식 자료 안내** — 이 플러그인 모음은 현대자동차·기아와 아무 관계가 없는 개인 제작물이다. 제도 관련 수치(합격 점수, 평가 주기 등)는 공개 기사·자료 기준이며 [기준 시점과 출처](./_shared/HKMC-FACTS.md)를 함께 적었다. 실제 업무에서는 **고객사가 배포한 최신 기준서가 항상 우선**한다.

## 플러그인 목록

| 플러그인 | 분야 | 스킬 수 | 하는 일 |
|---|---|---|---|
| **[supplier-quality](./supplier-quality)** | 협력사 품질보증 | 8 | SQ 인증 심사 준비, 8D 개선대책서, 클레임 초동 대응, PFMEA·관리계획서, 공정감사, 품질 실적 보고, 인증 심사, 고객 평가(5스타·SQ) 대응 |
| **[new-product-development](./new-product-development)** | 신차 개발·APQP | 5 | APQP 일정 역산, 초도품(ISIR) 제출 서류, 도면·사양 검토와 고객 질의서, 설계변경 영향 분석, 개발 이슈·단계 점검 |
| **[production-engineering](./production-engineering)** | 생산기술 | 6 | 작업표준서(다국어 포함), 4M 변경점 신고·초물 검증, 라인 밸런싱·CAPA, 설비·금형·애플리케이터 예방보전, 오류방지, 개선·VA/VE 제안서 |
| **[wiring-harness](./wiring-harness)** | 와이어링 하네스 | 5 | 단자 압착 품질(크림프 하이트·인장력·단면 분석·CFM), 공정흐름도와 고장 형태, 통전·오삽입 불량 분석, 도면↔BOM 대조, 압착기 호기·애플리케이터 배분 |
| **[supply-chain](./supply-chain)** | 구매·공급망 | 4 | 하위 협력사 평가·선정, 납입 성과·결품 조기 경보, 공급망 ESG 자가진단·실사 대응, 원가 계산서와 단가 조정 근거 |
| **[ehs-compliance](./ehs-compliance)** | 안전·환경 | 4 | 산업안전보건법 위험성평가, 중대재해처벌법 이행 점검, ISO 14001 환경측면·법규 대장, 재해·아차사고 조사 보고서 |
| **[office-workflow](./office-workflow)** | 사무·그룹웨어 | 5 | 전자결재 기안문·품의서, 주간·월간 보고, 회의록, 고객사 메일·공문 회신, 해외 사업장 다국어 커뮤니케이션 |
| **[supplier-plugin-builder](./supplier-plugin-builder)** | 플러그인 맞춤·제작 | 2 | 회사 맞춤(자리표시자 교체, 회사 정보 파일, 양식 반영), 새 협력사 업무 스킬 만들기 |

총 8개 플러그인, 39개 스킬.

## 원본과 무엇이 다른가

| 원본(knowledge-work-plugins) | 이 모음 |
|---|---|
| operations — 벤더 평가, 변경 요청(CAB), SOC 2·ISO 27001 컴플라이언스 | supplier-quality·production-engineering·supply-chain — SQ·5스타·IATF 16949, 4M 변경점, 하위 협력사 평가 |
| engineering — 스탠드업, 코드 리뷰, 장애 대응 | wiring-harness·new-product-development — 압착 품질, 통전 불량, APQP·초도품 |
| legal·human-resources — 미국 법 기준 | ehs-compliance — 산업안전보건법, 중대재해처벌법(법령 확인 전제) |
| 연결 도구: Slack, Jira, Notion | 연결 도구: 그룹웨어, MES, ERP, 고객 협력사 포털 (자리표시자, 연결 없이도 작동) |
| 영어 | 한국어 (해외 사업장용 다국어 지원 스킬 포함) |

## 설치

### Claude Code

```bash
# 저장소(또는 이 폴더)를 마켓플레이스로 추가
claude plugin marketplace add muzbox1973/hkmc-supplier-plugins

# 필요한 플러그인만 설치
claude plugin install supplier-quality@hkmc-supplier-plugins
claude plugin install wiring-harness@hkmc-supplier-plugins
```

### Claude 데스크톱 앱

플러그인 메뉴에서 이 폴더(또는 압축 파일)를 추가하고 필요한 플러그인을 켠다.

설치하면 스킬이 관련 요청에 자동으로 쓰이고, `/supplier-quality:eight-d-report`처럼 명령으로 직접 부를 수 있다.

## 처음 쓰는 순서

1. `supplier-plugin-builder`의 `/customize-for-company`로 회사 위치(1·2차), 업종, 보유 인증, 사업장, 시스템 이름, 결재 라인을 입력한다.
2. 회사 양식(8D, 4M 신청서, 작업표준서, 기안문)을 첨부해 출력 형식을 회사 양식으로 바꾼다.
3. 실제 업무 하나로 시험한다. 예: 최근 클레임 한 건으로 `/claim-response` → `/eight-d-report`.

## 플러그인 구조

```
plugin-name/
├── .claude-plugin/plugin.json   # 매니페스트
├── .mcp.json                    # 연결 도구 (기본 비어 있음)
├── CONNECTORS.md                # ~~자리표시자 설명
├── HKMC-FACTS.md                # 협력사 제도 공개 사실·출처 (검증 메모)
├── README.md
└── skills/스킬이름/SKILL.md     # 스킬 (필요하면 references/)
```

모든 파일이 마크다운과 JSON이다. 코드·빌드가 필요 없다. 공통 파일 원본은 [`_shared/`](./_shared)에 있고 각 플러그인에 복사되어 있다.

## 설계 원칙

- **근거 없는 수치 금지**: 규격값·기준값은 고객 도면·규격·사양서·회사 기준에서만 가져오고, 없으면 "확인 필요"로 남긴다.
- **계산은 코드로**: PPM, Cpk, 택트타임, 원가 같은 숫자는 실행해서 검산한다.
- **사실과 추정 분리**: 원인 분석·클레임 회신·ESG 설문에서 확인되지 않은 내용을 사실처럼 쓰지 않는다.
- **보안**: 고객 도면·단가·개인정보는 회사 정보보안 규정이 허용하는 범위에서만 다룬다.
- **법령은 확인 전제**: 안전·환경 스킬은 법률 자문이 아니며 최신 법령 확인을 결과물에 적는다.

## 기여

플러그인은 마크다운 파일이다. 포크해서 고치고 PR을 보내면 된다. 제도 관련 사실을 추가할 때는 `_shared/HKMC-FACTS.md`에 **출처와 기준 시점**을 함께 적는다.

## 라이선스

Apache License 2.0. 원본 구조는 Anthropic의 knowledge-work-plugins(Apache-2.0)를 참고했다. [NOTICE](./NOTICE) 참고.
