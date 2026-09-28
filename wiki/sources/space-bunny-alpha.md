---
type: source
title: space-bunny-alpha (스페이스버니 알파)
status: review
tags:
  - llm
  - stealth-model
  - coding-agent
  - openrouter
  - opencode
aliases:
  - Space Bunny Alpha
  - SpaceBunny
created: 2026-09-28
updated: 2026-09-28
sources:
  - https://openrouter.ai/stealth/space-bunny-alpha
  - https://x.com/opencode/status/2102767716666941864
  - https://x.com/cheatyyyy/status/2102781392199565683
related:
  - wiki/sources/longcat-2-5-preview
---

# space-bunny-alpha (스페이스버니 알파)

## 자료 정보

- 원본: `raw/sources/space-bunny-alpha-research-2026-09-28.md`
- 조사일: 2026-09-28, 범위: X + Reddit
- 성격: 스텔스 LLM 실사용 평가 정리 (투자조언 아님)

## 핵심 내용

Space Bunny Alpha는 OpenRouter 스텔스 슬롯(`stealth/space-bunny-alpha`)의 익명 LLM이다. 2026-09-22~23 등장, 1M 컨텍스트, 텍스트/이미지/비디오 입력, 툴콜링/JSON, 5단계 reasoning, 무료 프리뷰가 공식 스펙이다. OpenCode에서 `space-bunny-free`로 1주 무료 제공됐다.

정체는 MiniMax M3.1설이 가장 유력하다. 토크나이저 지문이 MiniMax M2/M3와 50개 스트링 전부 일치한다는 독립 검증이 있으나 공식 확정은 없다.

X는 속도·가성비 호평과 장황함·물리/비전 약점·일시 다운 지적이 반반이다. Reddit은 코딩 호평(빠름, 지능 체감 높음) against 장황·오버띵킹·롱컨텍스트 회상 결함·caveman CoT 지적이 공존한다.

## 해석

무료 테스트용으로는 가성비가 좋다. 속도가 빠르다는 증언이 X·Reddit 양쪽에 있다. 다만 프로덕션 투입에는 주인 미공개, 프롬프트 보관 가능(약관상), 품질 편차가 리스크다. Solana 동명 $SBA 밈코인 무더기는 AI 모델과 무관한 이름 하이재킹이다.

## 한계

- 정체 미확정 (MiniMax설 유력이나 공식 확인 없음)
- 벤치 수치는 서브셋 자칭 측정이라 직접 비교 불가
- 품질 편차가 크고 effort 레벨 수동 튜닝이 필요하다

## 쟁점/관계

- MiniMax M3.1 정체 논쟁: 토크나이저 일치 vs 서양 모델이라는 핑거프린팅 주장 충돌
- [[wiki/sources/longcat-2-5-preview]] — DEV 실전 비교 1건에서 LongCat 2.5가 판정승 (N=1, 편향 가능)
