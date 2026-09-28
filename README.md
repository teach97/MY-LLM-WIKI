# README.md (시작 안내)

Obsidian과 Codex로 유지하는 개인 LLM WIKI이다.

## 역할 분담

- Obsidian: 노트 읽기, 링크 탐색, 그래프 확인, 수동 검토
- Codex: 원본 ingest, 페이지 생성·갱신, 링크 연결, lint
- Git: 변경 이력과 복구

## 시작 방법

1. 이 폴더를 Obsidian에서 Vault로 연다.
2. `AGENTS.md`와 `purpose.md`, `schema.md`를 확인한다.
3. 논문·기사·공식 문서를 `raw/sources/`에 저장한다.
4. Codex에게 다음처럼 요청한다.

```text
raw/sources/파일명.md를 ingest해줘.
purpose.md와 schema.md를 먼저 읽고, 기존 위키 페이지와 중복·충돌을 확인해줘.
관련 source/concept/entity 페이지를 생성 또는 갱신하고
wiki/index.md, wiki/overview.md, wiki/log.md까지 업데이트해줘.
변경한 파일과 출처를 마지막에 보고해줘.
```

## 읽기 전용 질문

```text
현재 위키를 읽기 전용으로 검색해서
RLHF와 DPO의 차이를 출처와 함께 설명해줘. 파일은 수정하지 마.
```

## 점검

```text
위키를 읽기 전용으로 lint해줘.
깨진 링크, 고아 페이지, 출처 없는 주장, 중복, 오래된 정보를 찾아줘.
```

## 원칙

`raw/`는 원본이고, `wiki/`는 합성된 지식이다. 질문에 답하는 것과 위키를 수정하는 것을 분리한다. 자동 생성된 내용은 출처와 상태를 남긴다.
