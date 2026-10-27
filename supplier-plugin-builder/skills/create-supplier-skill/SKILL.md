---
name: create-supplier-skill
description: 협력사 현장 업무를 새 스킬로 만든다. 반복 업무의 입력·절차·판정 기준·출력 양식을 인터뷰로 정리해 이 플러그인 모음의 형식(SKILL.md 프런트매터, 연결 도구 자리표시자, HKMC-FACTS 근거 규칙)에 맞는 스킬 파일을 만든다. "새 스킬 만들어줘", "이 업무를 스킬로", "우리 회사 전용 스킬", "플러그인에 기능 추가"라고 할 때 사용한다.
argument-hint: "<스킬로 만들 업무>"
---

# /create-supplier-skill

> 자리표시자 규칙은 [CONNECTORS.md](../../CONNECTORS.md)를 따른다.

## 1. 인터뷰 (한 번에 묻는다)

1. 업무 이름과 하는 사람(부서·직무)
2. 언제 하는가(트리거: 고객 통보, 월말, 설비 교체 등)
3. 입력 자료(파일 종류, 시스템)
4. 단계별 절차와 판정 기준 — 기준값의 출처(고객 규격, 사내 기준)
5. 출력(양식, 받는 사람)
6. 자주 하는 실수와 꼭 지켜야 할 것

## 2. 어느 플러그인에 넣을지 정한다

품질 → `supplier-quality`, 개발 → `new-product-development`, 생산기술 → `production-engineering`, 하네스 특화 → `wiring-harness`, 구매 → `supply-chain`, 안전환경 → `ehs-compliance`, 사무 → `office-workflow`. 맞는 곳이 없으면 새 플러그인을 제안한다.

## 3. 스킬 작성 규칙

- 폴더·이름: 영어 소문자와 하이픈(kebab-case)
- 프런트매터 `description`: 무엇을 하는지 + 사용자가 실제로 말할 문장 4~6개
- 본문은 Claude에게 주는 지시문(명령형)으로 쓴다
- 기준값은 출처 문서에서만 가져오라고 쓰고, 없으면 "확인 필요"로 남기게 한다
- 계산은 코드로 실행하라고 쓴다
- 연결 도구는 `~~분류` 자리표시자로 쓰고 "연결 도구가 있으면" 절을 둔다
- 본문은 짧게(3,000단어 이하), 긴 기준표·예시는 `references/`로 뺀다

## 4. 템플릿

```markdown
---
name: <skill-name>
description: <무엇을 하는가>. "<트리거 문장1>", "<트리거 문장2>"라고 할 때 사용한다.
argument-hint: "<입력 설명>"
---

# /<skill-name>

> 낯선 자리표시자나 연결된 도구는 [CONNECTORS.md](../../CONNECTORS.md)에서 확인한다.

## 받을 정보
## 작업 순서
## 출력 형식
## 연결 도구가 있으면
## 주의
```

## 5. 점검

프런트매터 형식, 이름 중복, 상대 경로 링크를 확인하고, 가능하면 `claude plugin validate`를 실행한다.
