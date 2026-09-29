---
type: synthesis
title: windows-agent-tooling-lessons (Windows 에이전트 도구 삽질 기록)
status: draft
tags:
  - tooling
  - windows
  - troubleshooting
aliases:
  - Windows 삽질 기록
created: 2026-09-29
updated: 2026-09-29
sources: []
related:
  - wiki/synthesis/llm-wiki-operating-model
---

# windows-agent-tooling-lessons (Windows 에이전트 도구 삽질 기록)

## 한 줄 요약

Windows 에이전트 세션에서 직접 부딪혀 확인한 도구 고장 6건의 증상·원인·해결을 모았다.

## 1. graphify 실행기 심 깨짐

- 증상: `graphify update .` 실행 시 `python.exe: can't open file '...\bin\graphify'` 후 종료 코드 1.
- 원인: `%USERPROFILE%\.local\bin\graphify.exe`가 오래된 심. 같은 날짜의 복사본이라 겉보기엔 정상.
- 해결: `uv tool install --upgrade graphifyy`로 재설치. 이후에는 uv 툴 환경의 exe(`%APPDATA%\uv\tools\graphifyy\Scripts\graphify.exe`)를 풀 경로로 호출.
- 검증: 재설치 후 `graphify update .` 정상 완료 (1728 노드).

## 2. `.graphify_python` 절대경로 잔재

- 증상: 다른 사용자(`rlagn`) 경로가 박힌 `.graphify_python` 때문에 스킬 절차가 실패.
- 해결: 현재 환경의 인터프리터 경로를 BOM 없이 기록. PowerShell 5.1의 `Out-File -Encoding utf8`은 BOM을 붙이므로 `[System.IO.File]::WriteAllText` + `UTF8Encoding($false)` 사용.
- 재발 방지: `graphify-out/.graphify_python`, `.graphify_root`, `cache/`는 머신 종속이라 gitignore. 산출물(`graph.json`, `GRAPH_REPORT.md`, `manifest.json`)만 공유하면 다른 환경에서 바로 `query` 가능.

## 3. TYPESAFE_API_KEY 401 진단법

- 증상: JEV 모드에서 `GATEWAY_ERROR` ("게이트웨이 호출에 실패").
- 분리 절차: 무효 키로 게이트웨이에 직접 POST → 401이 돌아오면 망은 정상. 설정된 키로 같은 호출 → 401이면 키 무효·만료·취소 확정.
- 주의: 키 값은 절대 출력·커밋하지 않는다. 길이·HTTP 상태만 확인한다.
- 해결: 대시보드에서 새 키 발급 → `backend/.env` 교체 → 백엔드 재시작.

## 4. 에이전트 세션에 npx 없음

- 증상: `npx`를 찾을 수 없음. Machine PATH에는 `C:\Program Files\nodejs\`가 있으나 에이전트 서버 프로세스가 예전 환경을 물려받아 세션에 없음.
- 해결: 사용자 PATH를 고칠 필요 없음. 명령어마다 `$env:PATH += ';C:\Program Files\nodejs'`를 앞에 붙인다.

## 5. `NUL` 찌꺼기 파일 삭제

- 증상: 리다이렉트 오타로 생긴 0바이트 `NUL` 파일. Windows 예약어라 일반 삭제로 안 지워짐.
- 해결: `python -c "import os; p='\\\\?\\'+os.path.join(os.getcwd(),'NUL'); os.remove(p)"` — 경로는 프로그램으로 조립해 인코딩 문제를 피한다.

## 6. 전역 버튼 min-height가 아이콘 버튼을 타원으로 만듦

- 증상: 36×36 원형 버튼이 36×44 타원으로 렌더. 실측으로 확인.
- 원인: 전역 `button { min-height: 44px }` (터치 타깃 규칙)가 고정 크기 버튼의 height를 덮어씀.
- 해결: 아이콘 전용 버튼(`.thread-to-bottom`, `.attach-chip button`)에 `min-height: 0; padding: 0` 오버라이드.

## 논쟁과 한계

- 전부 단일 Windows PC(Playdata)에서의 일회성 확인이다. 다른 머신·버전에서는 재확인이 필요하다는 표시를 `확인 필요`로 남긴다.
- graphify 0.9.66→0.9.70 과정에서 확인한 내용이라 이후 버전에서는 달라질 수 있다.

## 추가 질문

- uv 툴 심이 왜 깨졌는지(복사본 유입 경로)는 미확인이다. 재발하면 추적한다.
