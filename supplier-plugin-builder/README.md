# 플러그인 맞춤·제작 플러그인 (`supplier-plugin-builder`)

이 플러그인 모음을 회사에 맞게 고치고(자리표시자 교체, 회사 정보 파일, 양식 반영) 새 협력사 업무 스킬을 만든다.

원본 cowork-plugin-management 역할을 협력사 환경에 맞게 옮긴 플러그인이다.

> 현대자동차·기아와 무관한 비공식 플러그인이다. 제도 관련 수치는 [HKMC-FACTS.md](HKMC-FACTS.md)의 공개 자료(기준 시점 표기)를 근거로 하며, 고객사가 배포한 최신 기준서가 항상 우선한다.

## 설치

```bash
claude plugin marketplace add <이 저장소 경로 또는 GitHub 주소>
claude plugin install supplier-plugin-builder@hkmc-supplier-plugins
```

Claude 데스크톱 앱에서는 플러그인 메뉴에서 이 폴더(또는 압축 파일)를 추가한다.

## 스킬

| 명령 | 하는 일 |
|---|---|
| `/create-supplier-skill` | 협력사 현장 업무를 새 스킬로 만든다. |
| `/customize-for-company` | 이 플러그인 모음을 우리 회사에 맞게 고친다. |

스킬은 관련 요청을 하면 자동으로 쓰이고, 명령(`/supplier-plugin-builder:스킬이름`)으로 직접 부를 수도 있다.

## 연결 도구

연결 없이 파일 첨부와 대화만으로 작동한다. 그룹웨어·MES·ERP·고객 포털을 연결하면 자료를 직접 가져온다. 자리표시자(`~~groupware` 등)의 뜻은 [CONNECTORS.md](CONNECTORS.md)를 본다. 회사 시스템 이름으로 바꾸려면 `supplier-plugin-builder` 플러그인의 `/customize-for-company`를 쓴다.

## 공통 원칙

- 규격값·기준값은 고객 도면·규격·사양서와 회사 기준에서만 가져오고, 없으면 "확인 필요"로 남긴다.
- 계산은 코드로 실행해 검산한다.
- 고객 도면·단가·개인정보는 회사 정보보안 규정이 허용하는 범위에서만 첨부한다.
