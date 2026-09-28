---
type: source
title: longcat-2.5-preview (롱캣 2.5 프리뷰)
status: review
tags:
  - llm
  - meituan
  - coding-agent
  - moe
aliases:
  - LongCat 2.5
  - LongCat-2.5-Preview
created: 2026-09-28
updated: 2026-09-28
sources:
  - https://longcat.chat/platform/docs/change-log
  - https://longcat.chat/platform/docs/pricing/longcat-2.5
  - https://x.com/opencode/status/2103841640171614322
  - https://x.com/TechBuzzChina/status/2104093701077074266
  - https://dev.to/prakh_r/longcat-25-preview-vs-space-bunny-alpha-my-experience-building-real-projects-5an1
related:
  - wiki/sources/space-bunny-alpha
---

# longcat-2.5-preview (롱캣 2.5 프리뷰)

## 자료 정보

- 원본: `raw/sources/longcat-2-5-research-2026-09-28.md`
- 조사일: 2026-09-28 (출시 3일차), 범위: 공식 문서 + X + Reddit
- 성격: 출시 직후 실사용 평가 정리 (투자조언 아님)

## 핵심 내용

LongCat-2.5-Preview는 Meituan LongCat팀의 2.0 후속 프리뷰로 2026-09-25 API 공개됐다. MoE 총 ~1.6T / 추론당 ~48B 활성화, 1M 네이티브 컨텍스트, 128K 출력, 이미지 이해 신규, thinking on/off, OpenAI+Anthropic 툴콜 포맷 지원이 공식 스펙이다. 2.0(MIT 오픈)과 달리 이번엔 클로즈드(API only)다.

가격은 한시 input $0.30 / cached $0.006 / output $1.20, 기존 유저 5M trial + OpenCode 2주 무료(Zero Data Retention)다. 2.5 전용 벤치 점수는 없다. "코딩 강함"은 회사 주장뿐이다.

X는 "무료 1M 써본다"는 기대 against "벤치 없이 파라미터 장사냐"는 경계로 갈린다. 실후기는 원샷 불가·멀티턴 필수라는 1건이 전부다. Reddit 2.5 전용 평가는 사실상 없고, 2.0 회상(창작 호평, 벤치보다 실전)만 있다.

## 해석

DEV 실전 비교 1건(진짜 프로젝트 5종)에서 LongCat 2.5가 Space Bunny Alpha 대비 판정승(7개 항목: 이해 속도, 툴콜 조율, 후속 제안, 아키텍처 피드백, 프롬프트 효율, 의도 추론, 블로커 우회)이라 코딩 에이전트 용도로 기대할 만하다. 단 N=1이다. 증거 수준은 벤치표+오픈웨이트를 갖춘 GLM-5.3-Flash가 아직 위다.

## 한계

- 2.5 벤치 0건, 실전 비교 N=1
- 클로즈드라 과금·리텐션·검열 변경 가능
- 문서에 image 페이로드 예시 누락 지적 (스크린샷-heavy 워크플로우는 포맷 사전 확인 필요)
- 중국 모델 특유 거버넌스·서빙 리스크

## 쟁점/관계

- 2.0 전적(Owl Alpha 블라인드 실사용 1위)이 2.5 신뢰도의 유일한 근거
- [[wiki/sources/space-bunny-alpha]] — 같은 태스크 A/B 비교 권장
- 한시가격 종료 시 정상가($0.75/$2.95) 전환 가능성
