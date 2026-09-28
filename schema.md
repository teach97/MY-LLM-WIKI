# schema.md (스키마)

## 페이지 종류

| type | 디렉터리 | 용도 |
|---|---|---|
| `entity` | `wiki/entities/` | 모델, 기업, 인물, 조직, 데이터셋, 프로젝트 |
| `concept` | `wiki/concepts/` | 이론, 기법, 구조, 현상, 용어 |
| `source` | `wiki/sources/` | 논문, 공식 문서, 기사, 강연, 영상, 원본 자료 요약 |
| `query` | `wiki/queries/` | 조사 중인 질문, 불확실성, 후속 연구 과제 |
| `comparison` | `wiki/comparisons/` | 모델·기법·도구의 비교 |
| `synthesis` | `wiki/synthesis/` | 여러 출처를 종합한 결론과 분석 |

## 공통 frontmatter

```yaml
---
type: concept
title: attention (어텐션)
status: draft
tags:
  - llm
aliases:
  - Attention
created: 2026-08-12
updated: 2026-08-12
sources: []
related: []
---
```

### 필드 규칙

- `type`: 위 페이지 종류 중 하나를 사용한다.
- `title`: 사람이 읽는 제목을 기록한다.
- `title`과 문서 첫 번째 H1은 영문 식별자를 먼저 쓰고 한글 설명을 소괄호로 병기한다. 예: `attention (어텐션)`. 널리 쓰이는 약어·제품명·고유명사는 원문 표기를 유지하거나 `aliases`에 추가한다.
- `status`: `draft`, `review`, `stable`, `deprecated` 중 하나를 사용한다.
- `tags`: 짧고 재사용 가능한 분류 태그를 사용한다.
- `aliases`: 약어·한국어·영문명 등 검색에 사용할 별칭을 기록한다.
- `created`, `updated`: `YYYY-MM-DD` 형식을 사용한다.
- `sources`: 기여한 원본 또는 `wiki/sources/` 페이지의 Vault 상대 경로를 기록한다.
- `related`: 밀접한 관련 페이지의 Vault 상대 경로를 기록한다.

## 파일명 규칙

- 기본 형식은 영문 `kebab-case.md`이다.
- 모델·기업·프로젝트는 공식 이름을 최대한 보존하되 링크 충돌을 피한다.
- 논문·공식 문서는 `author-year-short-title.md` 형식을 권장한다.
- 질문은 핵심 내용을 짧게 요약한 slug를 사용한다.

## 본문 구조

### Concept / Entity

```markdown
# identifier (한글 설명)

## 한 줄 요약

## 핵심 내용

## 작동 방식 또는 특징

## 관련 페이지

## 근거 자료

## 논쟁과 한계

## 추가 질문
```

### Source

원본 자료를 그대로 복제하지 않고, 메타데이터·핵심 주장·방법·한계·관련 페이지를 기록한다. 원본 파일은 `raw/sources/`에 보관한다.

### Query

질문, 현재 답변, 근거, 반대 근거, 미해결 부분, 다음 조사 단계를 기록한다.

### Comparison

비교 기준을 먼저 정의한 뒤 표로 정리한다. 각 셀의 중요한 주장에는 출처를 연결한다.

### Synthesis

여러 출처가 공통으로 지지하는 내용, 서로 충돌하는 내용, 현재 결론, 결론의 한계를 구분한다.

## 인덱스 규칙

`wiki/index.md`는 페이지 종류별 카탈로그이다.

```markdown
- [[wiki/concepts/attention]] — 토큰 간 중요도를 계산하는 메커니즘
```

## 로그 규칙

`wiki/log.md`는 추가·갱신·질문·lint 기록을 시간순으로 남기는 append-only 파일이다.

```markdown
## [2026-08-12] init | Wiki skeleton

- LLM WIKI 기본 구조를 생성함
```

## 충돌 처리

1. 기존 페이지의 내용을 조용히 삭제하지 않는다.
2. 충돌하는 출처를 모두 연결한다.
3. 차이가 생긴 이유가 시점·정의·실험 조건 중 무엇인지 확인한다.
4. 결론이 나지 않으면 `wiki/queries/`에 추적 질문을 만든다.
5. 결론을 내릴 때 근거와 불확실성을 함께 기록한다.
