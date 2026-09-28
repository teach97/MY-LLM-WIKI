# LongCat 2.5 (롱캣 2.5) X / Reddit 평가 리서치 — 형님용 정리

> 날짜: 2026-09-28 기준. 2.5-Preview 나온 지 3일밖에 안 됐어서, 팩트는 팩트대로, 카더라는 카더라대로 구분해뒀다.
> 투자조언 아님. 그냥 써볼지 말지 판단용이다.

---

## 1. LongCat 2.5가 뭔지 특정 — 헷갈리는 것들 정리

형님, 롱캣 버전 네이밍이 존나 헷갈리게 되어 있다. 딱 정리한다:

- **LongCat 2.5-Preview = Meituan(메이투안, 중국 배달 공룡) LongCat팀 신모델, 맞다.**
  공식 Change Log에 `Version: 2026-09-25 / LongCat-2.5-Preview Now Available`로 박혀 있다.
  출처: https://longcat.chat/platform/docs/change-log
- **2.0이랑은 다르다:**
  - 2.0 = 2026-06-30 릴리스, 오픈웨이트(MIT), 스텔스명 `Owl Alpha`로 OpenRouter에서 2달간 익명 테스트 → 월 10.1T 토큰, Hermes 1위 / Claude Code 2위 / OpenClaw 3위 찍고 정체 공개한 그 모델
  - 출처: https://longcat.chat/blog/longcat-2.0 , https://github.com/meituan-longcat/LongCat-2.0 , https://lcx.com/en/cryptonews/longcat-20-the-stealth-ai-model-that-was-quietly-topping-openrouter-all-along , https://cryptobriefing.com/openrouter-owl-alpha-model-global-ranking
  - 2.5-Preview = 2.0 다음 세대, **프리뷰(API only, 가중치 미공개)**. 파라미터 수는 2.0이랑 동일 티어라 스펙 점프 아니다.
- **이전 Flash 시리즈랑도 다르다:**
  - LongCat-Flash-Chat / Flash-Thinking / Flash-Lite (560B급, 68.5B급 등)은 2025-09 ~ 2026-03 세대. 2026-05-29에 레거시 6종 서비스 종료 공지 떴다.
  - 출처: https://longcat.chat/platform/docs/change-log (Version 2026-05-29 섹션)
- **스텔스명?**
  - 2.0 = `Owl Alpha` 확실. GLM-5.3-Flash = `ox-alpha` 확실.
  - 출처: https://glm5.app/blog/what-is-glm-5-3-flash , https://z.ai/blog/glm-5.3-flash
  - **2.5는 스텔스명 없음.** 이번엔 대놓고 `LongCat-2.5-Preview`로 OpenCode/Vercel에 떴다. Space Bunny처럼 익명 돌린 게 아니다.
  - Models.dev ID: `meituan/longcat-2.5-preview`, Release 2026-09-25, Weights Closed
  - 출처: https://models.dev/models/meituan/longcat-2.5-preview/ , https://models.opencode.ai/models/meituan/longcat-2.5-preview/ , https://vercel.com/ai-gateway/models/longcat-2.5-preview

한 줄로: **형님이 본 LongCat 2.5 = 메이투안 정식 후속 프리뷰, 2.0 오픈소스 떴던 그 라인의 신버전인데 이번엔 클로즈드 프리뷰다.**

---

## 2. 스펙 정리 (공식만 모음)

| 항목 | 내용 | 출처 |
|---|---|---|
| 정식명 | LongCat-2.5-Preview | https://longcat.chat/platform/docs/change-log |
| 공개일 | 2026-09-25, LongCat API 플랫폼 | https://longcat.chat/platform/docs/change-log , https://news.cocoloop.cn/en/2026/09/longcat-25-preview-1m-context |
| 구조 | MoE, 총 ~1.6T, 토큰당 ~48B 활성화 (약 3%) | https://x.com/TechBuzzChina/status/2104093701077074266 , https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ , https://news.cocoloop.cn/en/2026/09/longcat-25-preview-1m-context |
| 컨텍스트 | 1M (1,048,576 토큰) 네이티브 | https://vercel.com/ai-gateway/models/longcat-2.5-preview , https://longcat.chat/platform/docs/change-log |
| 최대 출력 | 128K (공식 퀵스타트) / Vercel·Models.dev는 131,072로 표기. 같은 거 반올림 차이다. | https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ , https://vercel.com/ai-gateway/models/longcat-2.5-preview , https://www.blackbox.ai/models/blackboxai/meituan/longcat-2.5-preview |
| 멀티모달 | **이미지 이해 신규 추가.** 텍스트+이미지 입력 → 텍스트 출력. 크로스모달 Q&A, 요약, visual reasoning 표방 | https://longcat.chat/platform/docs/change-log , https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ |
| Reasoning | thinking on/off 지원 (chat API에 `thinking` 세팅 노출) | https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ |
| Tool calling | 지원. OpenAI + Anthropic 포맷 둘 다 지원 | https://news.cocoloop.cn/en/2026/09/longcat-25-preview-1m-context , https://models.dev/models/meituan/longcat-2.5-preview/ |
| 타겟 | long-horizon tasks: 터미널, 브라우저, GUI, 스프레드시트, 디자인툴 across 연속 작업 + 코딩 (생성/이해/자동 프로그래밍) | https://longcat.chat/platform/docs/change-log , https://x.com/Meituan_LongCat/status/2103488918788411728 |
| 호환 | Claude Code, OpenCode, OpenClaw, Hermes, Kilo Code, Cline 등 | https://longcat.chat/platform/docs/change-log |
| 라이선스 | **클로즈드 프리뷰. 가중치 미공개.** 2.0(MIT 오픈)이랑 착각하면 안 된다 | https://models.dev/models/meituan/longcat-2.5-preview/ (Weights Closed) , https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ ("They do not announce public 2.5 model weights") |
| 가격 (한시) | input $0.30 / cached input $0.006 / output $1.20 (per 1M) | https://longcat.chat/platform/docs/pricing/longcat-2.5 , https://vercel.com/ai-gateway/models/longcat-2.5-preview , https://www.blackbox.ai/models/blackboxai/meituan/longcat-2.5-preview |
| 가격 (정상가) | input $0.75 / cached $0.015 / output $2.95 (Eyestech가 공식 프라이싱 인용. 공식 페이지는 현재 한시가격만 노출) | https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ |
| 무료 | 기존 유저 5M 토큰 trial quota + OpenCode에서 2주간 무료 (Zero Data Retention 명시) | https://news.cocoloop.cn/en/2026/09/longcat-25-preview-1m-context , https://x.com/opencode/status/2103841640171614322 |
| 벤치마크 | **2.5 전용 벤치 점수 없음.** 공식 발표에도 숫자표 없음. 2.0 점수를 2.5인 척 둔갑시키면 안 된다 | https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/ , https://x.com/TechBuzzChina/status/2104093701077074266 |

참고로 2.0 점수 (2.5 아님, 헷갈리지 말라고 적는다 — 전부 Meituan 자체 하네스 측정):
- Terminal-Bench 2.1: 70.8, SWE-bench Pro: 59.5 (GPT-5.5 58.6보다 위라 주장), SWE-bench Multilingual: 77.3, FORTE: 73.2, BrowseComp: 79.9, RWSearch: 78.8
- 출처: https://github.com/meituan-longcat/LongCat-2.0/blob/main/README.md , http://longcat.chat/blog/longcat-2.0 , https://www.longcatai.org/benchmarks

---

## 3. X(트위터) 분위기 — 긍정 / 부정 / 유보

전체적으로 **"관심은 폭발, 검증은 아직"**이다. 출시 3일차라 당연하다.

### 3-1. 공식 + 대형 계정 (팩트 전달)

**① @Meituan_LongCat (공식, 2026-09-25)**
- 원문: `"LongCat-2.5-Preview is now live. Built to take on long-horizon tasks. From terminals and browsers to GUIs, spreadsheets, and design tools."`
- 번역: "LongCat-2.5-Preview 떴다. 롱호라이즌 작업용으로 만들었다. 터미널, 브라우저부터 GUI, 스프레드시트, 디자인툴까지."
- 출처: https://x.com/Meituan_LongCat/status/2103488918788411728

**② @opencode (공식, 2026-09-26) — 252K 조회, 3.3K 좋아요**
- 원문: `"LongCat-2.5-Preview is now free on OpenCode for two weeks - 1M Context - Multi-modal - Zero Data Retention"`
- 번역: "LongCat-2.5-Preview, OpenCode에서 2주간 무료다 - 1M 컨텍스트 - 멀티모달 - 제로 데이터 리텐션"
- 출처: https://x.com/opencode/status/2103841640171614322
- 리플 분위기:
  - @elstar4x: `"We are getting more and more for free to test, a good time we are living in"` / "공짜로 테스트할 게 점점 늘어나네, 좋은 시대에 산다" — 긍정
  - @sarlloc: `"created this with space bunny gonna create the same thing with longcat as well now"` / "이거 스페이스 버니로 만들었는데 이제 롱캣으로도 똑같이 만들어보겠다" — 비교 실험 예고, 중립-긍정

**③ @Meituan_LongCat (OpenCode 무료 인용, 2026-09-26)**
- 원문: `"LongCat-2.5-Preview is now free to try on @opencode for two weeks! Give it a spin and show us what you build."`
- 번역: "OpenCode에서 2주간 무료로 써봐라! 돌려보고 뭐 만들었는지 보여줘라."
- 출처: https://x.com/Meituan_LongCat/status/2103844449550020816

### 3-2. 회의적 / 유보적 시각 (형님이 제일 봐야 할 부분)

**④ TechBuzzChina (2026-09-27) — 핵심 인용**
- 원문 (스펙 전달): `"Meituan's LongCat API platform launched LongCat-2.5-Preview on September 25. It's a mixture-of-experts model with about 1.6 trillion total parameters, activating roughly 48 billion per inference. The model adds image understanding, claims strong coding performance, and supports a 1 million token context window natively."`
- 번역: "메이투안 LongCat API 플랫폼이 9월 25일 2.5-Preview를 냈다. MoE로 총 1.6T, 추론당 약 48B 활성화. 이미지 이해 추가, 코딩 강하다 주장, 1M 컨텍스트 네이티브 지원."
- 원문 (평가 — 중요): `"But this is a preview release with no benchmark numbers yet, so actual capability is unproven. We'd argue the more interesting question is whether LongCat-2.5 can turn that parameter count into reliable long-task performance. Only 48B parameters activate per token, which leaves a lot of dormant capacity to manage."`
- 번역: "근데 이거 프리뷰고 벤치 숫자도 없어서 실제 성능은 미검증이다. 더 재밌는 질문은 이 파라미터 수를 믿을 만한 롱태스크 성능으로 바꿀 수 있냐는 거다. 토큰당 48B만 활성화라 놀리는 용량이 존나 많다."
- 출처: https://x.com/TechBuzzChina/status/2104093701077074266
- 형님용 해석: 1.6T 마케팅 숫자에 낚이지 마라. 활성화 3%짜리 MoE다. 메모리엔 1.6T 다 올려야 한다 (Eyestech도 같은 지적: https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/).

**⑤ David Hendrickson (@TeksEdge, 2026-09-27) + @DailyXplorer**
- 원문: `"It's already showing up in Vercel AI Gateway. 1.6T total / ~48B active, 1M context, up to 128K output, multimodal ... $0.30 / 1M input, $0.006 / 1M cached input, $1.20 / 1M output"`
- 번역: "벌써 Vercel AI Gateway에 떴네. 1.6T / 48B, 1M 컨텍스트, 128K 출력, 멀티모달 ... 가격 이렇다"
- 왜 로우키냐는 반응 (`"Why so low-key?"`) — 마케팅 없이 조용히 풀었다는 게 공통 관측
- 출처: https://x.com/TeksEdge/status/2104080600248545519 (검색 스니펫 기준)

### 3-3. 실전 사용 후기 (X, 1건 확보 — 귀하다)

**⑥ @VulKan42069 (2026-09-25, 2D 리듬게임 제작)**
- 원문: `"LongCat Flash 2.5 Preview on 2D rhythm game. The model is pretty decent and quite fast in doing task, but for getting good result, you need to do multiple-iterations of prompts. It's not a one-shot wonder model, 3D visuals are not its strong suit."`
- 번역: "LongCat 2.5 Preview로 2D 리듬게임 만들어봤다. 꽤 괜찮고 작업도 빠른데, 좋은 결과 내려면 프롬프트 여러 번 돌려야 한다. 원샷 원더 모델은 아니다. 3D 비주얼은 약하다."
- 출처: https://x.com/VulKan42069/status/2103523586569077094
- 형님용 해석: 코딩 에이전트용으론 속도 괜찮다는 증언 1표. 근데 원샷 기대하면 안 된다. (이름을 "Flash 2.5"라고 쓴 건 본인이 헷갈린 거다. Flash ≠ 2.5다.)

**X 총평:** 긍정은 "무료로 1M 멀티모달 써본다"는 기대감, 부정은 "벤치 없이 파라미터 장사냐"는 경계. 실전 후기는 VulKan 1건 + 아래 DEV 실전 비교 1건이 전부다. 벤치 vs 실전 논쟁은 아직 시작도 안 했다 — 비교할 벤치가 없으니까.

---

## 4. Reddit 평가 — 서브레딧별

먼저 양해: Reddit 본문 fetch가 로그인 월에서 막혀서, 검색 스니펫 + 스레드 타이틀로 확인된 것만 적는다. 날조 안 했다.

### 4-1. r/opencode / r/opencodeCLI (2026-09-26)

- 스레드: `"LongCat-2.5-Preview is now free on OpenCode for two weeks"` (두 서브에 동시)
- 출처: https://www.reddit.com/r/opencode/comments/1wqqtgx/longcat25preview_is_now_free_on_opencode_for_two , https://www.reddit.com/r/opencodeCLI/comments/1wqqt8f/longcat25preview_is_now_free_on_opencode_for_two
- 분위기: 공지 + "좋은 타이밍에 공짜로 테스트한다"는 반응. 아직 핸즈온 리포트는 없음. r/opencodeCLI 스니펫에 `"Longcat is completely created and trained from scratch by a Chinese food delivery company (as far as I know) called meituan"`라는 설명이 달림 — 번역: "롱캣은 내가 알기로 메이투안이라는 중국 배달회사가 스크래치부터 만든 거다" — 정체 소개 수준이다.

### 4-2. r/SillyTavernAI (2026-09, 2.5 스레드)

- 스레드: `"Longcat 2.5 Preview is live"`
- 출처: https://www.reddit.com/r/SillyTavernAI/comments/1wpyho8/longcat_25_preview_is_live
- 핵심 댓글 원문: `"Haven't tried it yet but I liked 2.0's creative writing even if the model itself would misattribute at times."`
- 번역: "2.5는 아직 안 써봤는데 2.0 창작 글쓰기는 좋았었다. 가끔 엉뚱한 귀속(주어/화자 착각) 하긴 했어도."
- 형님용 해석: 창작용으론 2.0 평이 좋았다는 방증. 2.5 창작 후기는 아직 0건이다.

### 4-3. r/SillyTavernAI — 2.0 레퍼런스 (2.5 판단 배경용)

- 스레드: `"LongCat 2.0 is a hidden gem"` (2026-08-14)
- 출처: https://www.reddit.com/r/SillyTavernAI/comments/1vogw2f/longcat_20_is_a_hidden_gem
- 스니펫 원문들:
  - `"Pros: [1] Very faithful and accurate instruction adherence ... elegantly navigates extremely complex worldbuildings"`
  - 번역: "장점 1: 지시 이행이 충실하고 정확하다. 존나 복잡한 월드빌딩도 우아하게 넘긴다"
  - `"ZERO censorship on any nature of content"` / "어떤 수위도 검열 제로" (주장 — 검증 안 됨, 그냥 이런 말이 돈다 수준으로 받아들여라)
- 스레드: `"Longcat 2 50 M tokens for 2 dollars on official site"` (2026-07-03)
- 출처: https://www.reddit.com/r/SillyTavernAI/comments/1umscea/longcat_2_50_m_tokens_for_2_dollars_on_official
- 원문: `"For 2 bucks you get 50 Million input/output tokens to spend on the model for 1 month."`
- 번역: "2달러 내면 50M 토큰을 한 달간 쓴다" — 2.0 가성신화의 근거다. 2.5는 아직 이런 요금제 없다.

### 4-4. r/LocalLLaMA — 2.0 기술 평가 (2.5 기대치 조정용)

- 스레드: `"Introducing LongCat-2.0, a large-scale MoE ... This was the stealth model ... 'owl-alpha'"` (2026-06-30)
- 출처: https://www.reddit.com/r/LocalLLaMA/comments/1uj7egu/introducing_longcat20_a_largescale_moe_language
- 스레드: `"Longcat 2 model weights have been published"` (2026-07-04) + `"longcat 2.0 (1.6T, ~48B active) weights are now open under MIT license"` (2026-07-05)
- 출처: https://www.reddit.com/r/LocalLLaMA/comments/1umo8zu/longcat_2_model_weights_have_been_published , https://www.reddit.com/r/LocalLLaMA/comments/1unyvnz/longcat_20_16t_48b_active_weights_are_now_open
- 핵심 평가 스니펫 원문: `"It's not as 'smart' as other frontier models when it comes to benchmark style tests (one shots, riddles, etc) but it was very good at (1) ..."`
- 번역: "원샷·수수께끼 같은 벤치 스타일 테스트에선 다른 프론티어보다 '똑똑'하진 않은데, (1)...에선 매우 좋았다" (뒷부분 잘림 — 원문 확인 필요)
- 형님용 해석: 2.0도 벤치보단 실전 에이전트 체감으로 먹은 모델이다. 2.5도 같은 패턴일 가능성 높다. 벤치만 보고 판단하면 안 된다.

### 4-5. r/LocalLLM / r/AIToolsPerformance / r/singularity (2.0 배경)

- `"Meituan unveils LongCat-2.0, China's first trillion-parameter AI model built on domestic chips"`: https://www.reddit.com/r/LocalLLM/comments/1ujr7nh/meituan_unveils_longcat20_chinas_first
- `"LongCat-2.0: China Just Built a 1.6T AI WITHOUT Nvidia"`: https://www.reddit.com/r/AIToolsPerformance/comments/1ujsb9z/longcat20_china_just_built_a_16t_ai_without_nvidia
- `"LongCat, new reasoning model, achieves SOTA benchmark performance for open source models"` (2025-09, Flash-Thinking 시절): https://www.reddit.com/r/singularity/comments/1nn4uk1/longcat_new_reasoning_model_achieves_sota
- 공통 정서: 국산 칩 50,000장 풀트레인 스토리에 다들 놀람 + "배달회사가 이걸 한다고?" 반응. 기술 평가는 2차다.

**Reddit 총평:** 2.5 전용 평가는 사실상 없음. 있는 건 공지 + 2.0 회상. r/SillyTavernAI 창작파는 호의적, r/LocalLLaMA 기술파는 "벤치 말고 실전" 주의다.

---

## 5. 비교 언급 정리 — Space Bunny Alpha / GLM 5.3 Flash / DeepSeek

### 5-1. Space Bunny Alpha vs LongCat 2.5 — 유일한 직접 비교 (DEV, 2026-09-28)

형님, 이거 오늘(9/28) 올라온 따끈한 글이다. Prakhar Yadav (인도, ServiceNow SWE) 실전 비교.

- 출처: https://dev.to/prakh_r/longcat-25-preview-vs-space-bunny-alpha-my-experience-building-real-projects-5an1
- 실험: 미니 웹사이트, ServiceNow 엔터프라이즈 데모(MCP 서버 연동), 크롬 익스텐션, Homebrew 인스톨러, 자동화 스크립트 — 벤치 프롬프트가 아니라 진짜 프로젝트로 비교
- 결론 원문: `"For my specific workflows, LongCat 2.5 Preview felt noticeably more intelligent than Space Bunny Alpha, even when Space Bunny was configured with High Thinking mode enabled."`
- 번역: "내 워크플로우에선 LongCat 2.5 Preview가 Space Bunny Alpha보다 눈에 띄게 똑똑하게 느껴졌다. 버니를 High Thinking으로 켜놔도 그랬다."
- 세부 7개 항목 원문 → 번역:
  1. `"LongCat generally understood project goals, architecture, and previous discussions much faster"` / "롱캣이 프로젝트 목표·아키텍처·이전 대화를 훨씬 빨리 이해했다"
  2. `"LongCat was significantly better at tool calling and coordinating workflows involving multiple tools"` / "롱캣이 툴콜·멀티툴 조율에서 확실히 나았다"
  3. `"LongCat regularly suggested logical follow-up actions ... without requiring additional prompting"` / "롱캣은 시키지 않아도 다음 스텝·검증 전략을 제안했다"
  4. `"LongCat provided stronger and more actionable [architecture] recommendations"` / "아키텍처 피드백이 더 강하고 실행 가능했다"
  5. `"often required fewer prompts to arrive at the desired outcome"` / "원하는 결과까지 프롬프트가 덜 들었다"
  6. `"LongCat frequently inferred the objective behind my request even when instructions were incomplete"` / "지시가 불완전해도 의도를 알아챘다"
  7. `"When encountering blockers, LongCat was better at proposing workarounds ... Space Bunny was more likely to get stuck"` / "막히면 롱캣은 우회책을 냈고, 버니는 stuck 되거나 유저한테 떠넘겼다"
- 주의: N=1 리뷰다. 필자 편향 가능. 그래도 현재 유일한 롱폼 실전 비교라 가중치는 있다.

### 5-2. Space Bunny Alpha 스펙 (비교용 배경)

- 정체: 익명 스텔스, OpenRouter `stealth/space-bunny-alpha`, 2026-09-23 등장, 무료 프리뷰, 1M 컨텍스트, 텍스트·이미지·비디오 입력 → 텍스트 출력
- 출시 직후 provider-side 이슈로 일시 오프라인 갔다는 기록 있음
- 출처: https://spacebunnyalpha.com/ , https://huggingface.co/stealth-model/space-bunny-alpha , https://blog.buildfastwithai.com/space-bunny-review
- 독립 측정치 (spacebunnyalpha.com 자체 평가, 60Q/300Q 서브셋이라 레퍼런스와 직접비교 불가):
  - AI BENCHY high: 7.0/10 (data extraction·tool calling 10/10)
  - GPQA Diamond 자체 60Q: 82.0%
  - MMLU-Pro: 75%
  - HLE 오리지널 300Q: 46.1% (95% CI 40.4–51.8)
  - 토큰 효율: Qwen3.8 Flash 대비 출력 토큰 67% 적음
  - 속도 P50: 87 tok/s, 지연 1.07s
  - 출처: https://spacebunnyalpha.com/
- 정체 미스터리: OpenAI/GPT-OSS 유사 vs MiniMax 패밀리 유사 두 가설, M3.1-Flash 정확 일치는 SVG 대조로 약화 — 출처: https://spacebunnyalpha.com/ ("M3.1 Flash? We checked the selfie" 섹션)
- 형님용 해석: 버니는 가볍고 싼 맛 + 미스터리 마케팅으로 뜬 거고, 롱캣 2.5는 무거운 에이전트용이다. DEV 리뷰가 롱캣 손을 들어준 것도 체급 차이 감안하면 자연스럽다.

### 5-3. GLM-5.3 Flash (지푸) — 현시점 가장 센 비교축

- 스펙: 2026-08-26 릴리스, 구 스텔스명 `ox-alpha`, 320B total / 18B active, 1M 컨텍스트, 131K 출력, 네이티브 멀티모달(텍스트·이미지·비디오→텍스트), MIT 오픈웨이트
- 출처: https://z.ai/blog/glm-5.3-flash , https://glm5.app/blog/what-is-glm-5-3-flash , https://docs.b.ai/llmservice/models/glm-5-3-flash
- 가격: 정상 $0.15 in / $0.50 out (per 1M), 한시 반값($0.075/$0.25, ~2026-09-09까지) — 롱캣 2.5 한시($0.30/$1.20)보다 싸다
- 출처: https://myclaw.ai/blog/glm-5-3-flash-vs-opus-5 , https://aimlapi.com/models/glm-5-3-flash
- 벤치 (Z.ai 발표): Terminal-Bench 2.1: 84.3, DeepSWE v1.1: 63.4, AutomationBench: 48.8, Toolathlon Verified: 78.4 — Opus 4.8에 근접 주장
- 출처: https://z.ai/blog/glm-5.3-flash , https://docs.b.ai/llmservice/models/glm-5-3-flash
- 형님용 해석: **증거 수준은 GLM-5.3-Flash가 롱캣 2.5보다 한참 위다.** 벤치표 + 오픈웨이트 + MIT + 스텔스 기간 주간 1위 기록까지 있다. 롱캣 2.5는 아직 숫자표 자체가 없다. 가격도 GLM이 싸다. 롱캣이 이기려면 OpenCode 2주 실전 평이 터져야 한다.

### 5-4. DeepSeek (V4 Pro / V4 Flash / V4.1-Flash)

- 라인업 (2026-09 기준): Pro = DeepSeek-V4-Pro-0813, Flash = V4-Flash-0731 (284B total / 13B active), 신형 = V4.1-Flash (2026-09-10, 552B CED 아키텍처, KV캐시 4x 압축 주장)
- 출처: https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/deepseek-v4-1-flash-is-coming-to-microsoft-foundry/4556431 , https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash/blob/main/README.md , https://www.scmp.com/tech/big-tech/article/3367051/deepseek-says-new-flash-ai-model-beats-kimi-k3-cyber-coding-benchmarks , https://myclaw.ai/blog/deepseek-v4-flash-vs-kimi-k3
- LongCat 2.0 vs DeepSeek (Artificial Analysis, 2.5 아님 주의):
  - vs DeepSeek V3.2 Reasoning: 지능 34 vs 33* — 롱캣 근소 우위, 가격은 DeepSeek가 쌈 ($0.46 vs $0.11)
  - 출처: https://artificialanalysis.ai/models/comparisons/longcat-2-0-vs-deepseek-v3-2-reasoning
  - vs DeepSeek V4 Flash High Effort: 26* vs 30* — DeepSeek 우위, 가격도 DeepSeek가 쌈 ($0.46 vs $0.07)
  - 출처: https://artificialanalysis.ai/models/comparisons/longcat-2-0-vs-deepseek-v4-flash-0420-high
  - vs DeepSeek V4 Pro Max Effort: 34 vs 53 — DeepSeek 압승, 속도는 42 vs 68 tok/s
  - 출처: https://artificialanalysis.ai/models/comparisons/deepseek-v4-pro-vs-longcat-2-0
  - vs Kimi K2.5 Reasoning: 34 vs 36 — Kimi 우위, 속도는 39 vs 81 tok/s
  - 출처: https://artificialanalysis.ai/models/comparisons/longcat-2-0-vs-kimi-k2-5
- 형님용 해석: 롱캣 2.0은 "가성비 1M 에이전트" 포지션이지 최강자는 아니다. DeepSeek Pro / Kimi K3 / GLM-5.3이 지능·속도에서 앞선다. 2.5가 이 구도를 깰지는 미정. 그리고 DeepSeek V4.1-Flash(9/10)랑 Space Bunny(9/23)랑 LongCat 2.5(9/25)가 2주 안에 몰려나와서 지금 중국 모델 전쟁 중이다.

---

## 6. 총평 — 써볼 만한지 + 리스크 (투자조언 아님)

**써볼 만한지: 응, 써봐라. 지금이 제일 쌀 때다.**

1. OpenCode 2주 무료 + Zero Data Retention이면 밑질 게 없다. 1M 컨텍스트 멀티모달 에이전트를 공짜로 돌려보는 기회다.
2. 2.0 전적(Owl Alpha 실사용 1위)이 있어서 "벤치 없는 신모델" 중에서는 신뢰도가 그나마 있다. 익명 블라인드에서 뽑힌 모델이다.
3. DEV 실전 비교 1건이 Space Bunny 대비 판정승이라 코딩 에이전트 용도로는 기대해볼 만하다.
4. 한시 가격 $0.30/$1.20이면 1M급 중에선 저렴한 편이다. 캐시 히트($0.006)는 씹사기 수준이라 롱런 에이전트에 유리하다.

**근데 이건 알고 써라 (리스크):**

1. **벤치 0건.** 2.5 숫자표가 없다. "코딩 강함"은 회사 말뿐이다. VulKan 후기처럼 원샷 기대하면 안 되고 멀티턴으로 깎아야 한다.
2. **클로즈드다.** 2.0은 MIT 오픈이었는데 2.5는 API only다. 나중에 과금·리텐션·센서 바뀔 수 있다. 로컬·셀프호스팅 계획이면 2.0이나 GLM-5.3-Flash를 봐라.
3. **문서 구멍 있다.** chat completions 레퍼런스에 image 페이로드 예시가 없다는 지적이 있다 (Eyestech). 스크린샷-heavy 워크플로우는 작은 호출로 포맷 먼저 확인해라.
4. **중국 모델 특유 리스크.** 메이투안 공식 라이선스 문구에 상표·특허 권리 유보 + 국내 칩 클러스터 서빙이라 지정학적·지연 이슈 가능. Zero Data Retention은 OpenCode 경유 한정 문구라 본 플랫폼 약관은 따로 확인해라.
5. **비교축이 세다.** GLM-5.3-Flash(벤치·가격·오픈 다 갖춤), DeepSeek V4.1-Flash(효율), Kimi K3(지능) 다 있다. 롱캣 2.5에 올인하지 말고 2주 무료 동안 A/B로 돌려봐라.
6. **투자 관점 아님.** 이 글은 모델 써볼지 판단용이지 매매·투자 조언 아니다. $MPNGY 어쩌고는 TechBuzzChina 태그일 뿐이다.

**형님 액션 추천:**
- OpenCode에서 `longcat-2.5-preview-free`로 지금 하던 작업 그대로 돌려봐라. 특히 툴 여러 개 쓰는 에이전트 작업.
- Space Bunny Free랑 같은 태스크로 비교해봐라. DEV 글처럼 롱캣이 이기는지 형님 손으로 확인하는 게 제일 빠르다.
- 2주 끝나기 전에 유료 전환가 확인해라. $0.30/$1.20 한시가가 끝나면 $0.75/$2.95 될 수 있다.

---

## 출처 모음 (주요 URL)

- 공식 Change Log: https://longcat.chat/platform/docs/change-log
- 공식 가격: https://longcat.chat/platform/docs/pricing/longcat-2.5
- 공식 블로그 2.0: http://longcat.chat/blog/longcat-2.0
- 공식 GH 2.0: https://github.com/meituan-longcat/LongCat-2.0
- Vercel 게이트웨이: https://vercel.com/ai-gateway/models/longcat-2.5-preview
- Models.dev: https://models.dev/models/meituan/longcat-2.5-preview/
- BlackBox: https://www.blackbox.ai/models/blackboxai/meituan/longcat-2.5-preview
- Cocoloop 정리: https://news.cocoloop.cn/en/2026/09/longcat-25-preview-1m-context
- Eyestech 분석: https://eyestech.in/longcat-2-5-preview-vision-1m-agent-tasks/
- DEV 실전 비교: https://dev.to/prakh_r/longcat-25-preview-vs-space-bunny-alpha-my-experience-building-real-projects-5an1
- Space Bunny: https://spacebunnyalpha.com/
- GLM-5.3-Flash 공식: https://z.ai/blog/glm-5.3-flash
- GLM 설명: https://glm5.app/blog/what-is-glm-5-3-flash
- X 공식: https://x.com/Meituan_LongCat/status/2103488918788411728 , https://x.com/opencode/status/2103841640171614322 , https://x.com/Meituan_LongCat/status/2103844449550020816
- X 평가: https://x.com/TechBuzzChina/status/2104093701077074266 , https://x.com/VulKan42069/status/2103523586569077094 , https://x.com/TeksEdge/status/2104080600248545519
- Reddit: https://www.reddit.com/r/opencode/comments/1wqqtgx/longcat25preview_is_now_free_on_opencode_for_two , https://www.reddit.com/r/opencodeCLI/comments/1wqqt8f/longcat25preview_is_now_free_on_opencode_for_two , https://www.reddit.com/r/SillyTavernAI/comments/1wpyho8/longcat_25_preview_is_live , https://www.reddit.com/r/LocalLLaMA/comments/1uj7egu/introducing_longcat20_a_largescale_moe_language , https://www.reddit.com/r/SillyTavernAI/comments/1vogw2f/longcat_20_is_a_hidden_gem
