---
type: source
title: ling-3-0-flash-fin (링 3.0 플래시 핀)
status: review
tags:
  - llm
  - ant-group
  - coding-agent
  - open-weights
aliases:
  - Ling 3.0 Flash Fin
  - Ling 3.0 Flash Fin Free
created: 2026-10-03
updated: 2026-10-03
sources:
  - https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin
  - https://artificialanalysis.ai/articles/ant-group-releases-finance-focused-ling-3-0-flash-fin
  - https://opencode.ai/docs/zen/
related:
  - wiki/sources/space-bunny-alpha
---

# ling-3-0-flash-fin (링 3.0 플래시 핀)

## 자료 정보

- 원본: `raw/sources/ling-3-0-flash-fin-research-2026-10-03.md`
- 조사일: 2026-10-03, 범위: 공식 문서 + X + Reddit + 리더보드
- 성격: 정식 모델 평가 정리 (투자조언 아님, 금융 출력물은 전문가 검수 필수)

## 핵심 내용

Ling 3.0 Flash Fin은 Ant Group 산하 InclusionAI 정식 모델이다. 스텔스가 아니다. Fin = Finance (금융 계속학습판), finetune이 아니다. 스펙은 124B MoE / 활성 5.1B / 256K 컨텍스트 / 텍스트 전용 / reasoning ON / MIT 오픈웨이트다.

"Fin Free"는 OpenRouter `:free` + OpenCode Zen 무료 슬롯 이름이다. 유료판도 있다 ($0.042/$0.1232).

X는 "무료치고 미쳤다"(AhmadAwais, Kilo) vs 벤더 속도 주장(1100 tok/s) 불신·환각 지적 구도다. Reddit LocalLLaMA는 호의적이다 (275↑ 스레드, qwen3.6이 못 고친 버그 수정 목격담, 애플실리콘 60-80 t/s).

리더보드: AA Intelligence 23, Finance & Accounting 24에 등재됨. 단 AutomationBench 7%, Terminal-Bench 0%라 하드 에이전트는 약하다.

## 해석

GLM-5.3-Flash(AA42)·DeepSeek V4 Flash(AA52)가 코딩·종합에서 위다. Ling은 활성 파라미터당 효율 + 무료로 승부 보는 포지션이다. 공짜 양산 일꾼으론 굿, 어려운 작업은 GLM과 붙여보고 결정해라.

## 한계

- 벤더 벤치(SWE-Bench Pro 56.6 등)는 독립 재현 없음
- AA 버전별 점수 스케일 상이 (Fin 23 vs Flash 20 직접 비교 금지)
- Zen 무료 슬롯은 학습 사용 가능 (기밀·금융자료 주의)

## 쟁점/관계

- 금융 수치 환각 주의 (정확 17% vs 환각 33%)
- [[wiki/sources/space-bunny-alpha]] — 별개 스텔스 라인, 직접 비교 불가
