---
type: source
title: fledge-alpha-free (플리지 알파 프리)
status: review
tags:
  - llm
  - stealth-model
  - coding-agent
  - opencode
aliases:
  - Fledge Alpha
  - Fledge Alpha Free
created: 2026-10-03
updated: 2026-10-03
sources:
  - https://opencode.ai/docs/zen
  - https://opencode.ai/data/unknown/fledge-alpha
  - https://x.com/aitrackerbot/status/2105751970107560102
related:
  - wiki/sources/space-bunny-alpha
  - wiki/sources/longcat-2-5-preview
---

# fledge-alpha-free (플리지 알파 프리)

## 자료 정보

- 원본: `raw/sources/fledge-alpha-research-2026-10-03.md`
- 조사일: 2026-10-03 (출시 3일차), 범위: X + Reddit + OpenCode Data
- 성격: 출시 직후 실사용·정체 평가 정리 (투자조언 아님)

## 핵심 내용

Fledge Alpha Free는 OpenCode Zen 전용 무료 스텔스 모델이다 (`opencode/fledge-alpha-free`). 2026-10-01 전후 데뷔, 입출력 전부 무료이나 기간 한정이다. OpenRouter 스텔스 슬롯이 아니라 Zen 전용이다.

정체는 3파전으로 미확정이다: ①Thinking Machines Lab/Inkling 후속 (Tinker 참조·reasoning 설정·40px 이미지 패치그리드 지문) ②라우터 (DeepSeek 4.1 + Kimi K3? + unknown 돌려막기) ③DeepSeek V4.1 Pro. 공식 스펙(컨텍스트 등)은 미공개다.

X는 조용하고 AI Tracker Bot 지문 트윗(30K뷰)이 사실상 유일 신호다. Reddit은 "공짜치고 쎄다" vs "누구냐" 반반이며 정체 파헤치는 중이다.

## 해석

출시 3일 만에 OpenCode 사용량 #15위(302B 토큰)라 흡입력은 진짜다. 단, Space Bunny/LongCat과 달리 **zero-retention이 아니라** 무료 기간 데이터가 학습에 쓰일 수 있다. 회사 코드·비밀키는 넣지 마라.

## 한계

- AA/LMArena 미등재 (#15위는 사용량 순위, 성능 순위 아님)
- Reddit 본문 크롤링 불가(403)라 스니펫 기반 인용
- "limited time" 무료라 예고 없이 종료·유료 전환 가능 (Ox 전례)

## 쟁점/관계

- Inkling 지역 제공 여부와 Fledge 제공 국가가 다르다는 관측 (정체썰 역풍 요소)
- [[wiki/sources/space-bunny-alpha]] — 같은 Zen 무료 라인, 얘는 zero-retention
- [[wiki/sources/longcat-2-5-preview]] — 같은 Zen 무료 라인, 얘도 zero-retention
