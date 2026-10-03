# 형님용 리서치: Ling 3.0 Flash Fin Free (a.k.a. Ling 3.0 Flash Fin, `ling-3.0-flash-fin-free`)

> 작성일: 2026-10-03 (UTC). 형님 말대로 반말 + 한국어 informal로 정리했음. 주장마다 출처 URL 박았고, 실제 해외 의견은 원문(영문) + 번역 같이 넣었음.

---

## 0. TL;DR — 30초 요약

- 형님, 이거 **스텔스 모델 아님**. 정체 명확한 중국 앤트그룹(InclusionAI/Ant Group) 정식 모델이야.
- **Fin = Finance (금융 특화)**. finetune 약자 아님. base인 Ling-3.0-flash에 금융 데이터 계속학습시킨 버전.
- 스펙은 **124B MoE / 활성 5.1B / 256K 컨텍스트(서빙상 262,144) / 텍스트 전용 / reasoning 기본 ON / tool-calling 지원**.
- **"Fin Free"는 OpenRouter `:free` 엔드포인트 + OpenCode Zen 무료 슬롯** 이름이야. 유료판(`inclusionai/ling-3.0-flash-fin`)도 있음.
- 평가는 **"가성비 괴물, 근데 플래그십은 아님"**이 중론. 코딩 에이전트용으로 무료치고 대박이라는 평이 X·레딧에 많음.
- 리더보드: **AA Intelligence Index 23 (Fin), Finance & Accounting Index 24** (2026-09-16 AA 기사 기준). base Flash는 AA 38 (구버전 기준) / 현행 AA 페이지에선 20으로 표기됨 — 버전 차이니 아래 표 참고.
- 비교하면 **GLM-5.3-Flash·DeepSeek V4 Flash가 코딩/종합에서 위**, Ling은 **효율(활성 파라미터당 지능) + 무료**로 승부 보는 포지션. Space Bunny Alpha·LongCat 2.5는 별개 스텔스/프리뷰 라인.

---

## 1. 얘 정체가 뭐냐 (형님이 헷갈린 포인트 정리)

| 형님 질문 | 답 |
|---|---|
| Ling 팀 모델이 맞냐? | 응. **Ant Group 산하 InclusionAI (Ant Ling)** 정식 모델 패밀리. Ling = 범용 MoE, Ring = 추론 특화, Ming = 멀티모달. 출처: [OrcaRouter Ling-3.0-flash 해설](https://www.orcarouter.ai/blog/ling-3-0-flash), [Ant Ling 공식 문서](https://developer.ant-ling.com/en/docs/models/ling/) |
| 중국 모델 맞냐? | 맞음. Ant Group(중국) + inclusionAI. HF 오거나이저 `inclusionAI`. 출처: [HF inclusionAI/Ling-3.0-flash](https://huggingface.co/inclusionAI/Ling-3.0-flash) |
| OpenRouter 스텔스 슬롯이냐? (`stealth/xxx` 같은 거) | **아님**. `inclusionai/ling-3.0-flash-fin:free`처럼 벤더명 박힌 정식 리스팅. 스텔스는 Space Bunny Alpha(`stealth/space-bunny-alpha`)那种. 출처: [OpenRouter Fin 무료 페이지(검색 스니펫)](https://openrouter.ai/inclusionai/ling-3.0-flash-fin:free), [Space Bunny Alpha 딥다이브](https://sioralabs.com/blog/space-bunny-alpha-deep-dive) |
| OpenCode 무료 모델이냐? | **맞음, 그중 하나**. OpenCode Zen에 `ling-3.0-flash-fin-free`로 무료 등재. 옆에 Space Bunny Free, LongCat 2.5 Preview Free, Nemotron 시리즈랑 같이 있음. 출처: [OpenCode Zen 공식 문서](https://opencode.ai/docs/zen/) |
| Fin이 finetune 뜻이냐? | **아니, Finance**. HF 공식 설명: "first finance-enhanced model in the Ant Ling family... extends Ling-3.0-flash through continued training on high-quality financial data." 즉 금융 계속학습판. 출처: [HF inclusionAI/Ling-3.0-flash-Fin](https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin) |

### 릴리즈 타임라인 (이거 중요)

- **2026-07-23/24**: Ling-3.0-flash 발표 (Ant Group). BusinessWire 보도. 출처: [AETOSWire/BusinessWire 재보도](https://www.aetoswire.com/en/news/2707202656473), [OrcaRouter 7/24 글](https://www.orcarouter.ai/blog/ling-3-0-flash)
- **~2026-08-03까지**: base Flash 무료 API 프로모. 출처: [AETOSWire](https://www.aetoswire.com/en/news/2707202656473), [AntLing 공식 X](https://x.com/AntLingAGI/status/2080351022028095681)
- **2026-08-07**: base Flash 가중치 MIT 오픈소스 (HF + ModelScope). 출처: [OrcaRouter 정리글](https://www.orcarouter.ai/blog/ling-3-0-flash)
- **2026-08-27**: **Fin API 출시** (유료 + 무료 엔드포인트). OpenRouter 릴리즈 날짜로 명시. 출처: [OpenRouter Fin 페이지](https://openrouter.ai/inclusionai/ling-3.0-flash-fin), [TechNode 보도](https://technode.com/2026/08/28/ant-group-launches-finance-tuned-ling-model-plans-to-open-source-it-next-week/)
- **2026-09-09 (Inclusion·외탄 컨퍼런스)**: **Fin 가중치 오픈소스** (MIT) + 금융검색 벤치 FinFIRST 공개. 출처: [BusinessWire 9/8](https://www.businesswire.com/news/home/20260908565055/en/Ant-Group-Open-Sources-Ling-3.0-flash-Fin-for-Real-World-Financial-Workflows), [Ant Group 공식 PR](https://www.antgroup.com/en/news-media/press-releases/1788944400000), [Artificial Analysis 기사 9/16](https://artificialanalysis.ai/articles/ant-group-releases-finance-focused-ling-3-0-flash-fin)

---

## 2. 스펙 (형님, 여기서 숫자 틀리면 쪽팔리니까 출처별로 정리)

### 2.1 공식 스펙표

| 항목 | 값 | 출처 |
|---|---|---|
| 아키텍처 | Hybrid-linear MoE (KDA + Gated MLA 5:1, 35 KDA + 7 MLA, 1/64 sparse MoE, routed expert 512 중 8개 활성화 + shared 1) | [HF 모델카드](https://huggingface.co/inclusionAI/Ling-3.0-flash) |
| 총 파라미터 | **124B** | [HF](https://huggingface.co/inclusionAI/Ling-3.0-flash), [AA](https://artificialanalysis.ai/models/ling-3-0-flash) |
| 활성 파라미터 | **~5.1B / 토큰** | 동일 |
| 컨텍스트 | 네이티브 **256K**, 서빙상 **262,144 토큰**, 최대 출력 32,768 (OpenRouter 표기). 1M까지 확장 주장(벤더) | [Ant Ling Docs](https://developer.ant-ling.com/en/docs/models/ling/), [OpenRouter](https://openrouter.ai/inclusionai/ling-3.0-flash-fin) |
| 멀티모달 | **Fin/Flash 텍스트 전용**. 이미지·영상은 별도 VL 모델(`Ling-3.0-flash-VL`, 활성 5.5B)이 담당 | [Ant Ling Docs](https://developer.ant-ling.com/en/docs/models/ling/), [AA Fin 기사](https://artificialanalysis.ai/articles/ant-group-releases-finance-focused-ling-3-0-flash-fin) |
| Reasoning | **기본 ON (hybrid reasoning)**, 끌 수 있음. 권장 샘플링: Fin은 `temperature=1.0, top_p=0.95, top_k=20` / base는 `0.6/0.95/20` | [HF Fin](https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin), [HF base](https://huggingface.co/inclusionAI/Ling-3.0-flash) |
| Tool calling | 지원 (ling3 파서, SGLang/vLLM 레시피) | [HF](https://huggingface.co/inclusionAI/Ling-3.0-flash) |
| 속도(벤더 주장) | 피크 **~1000 tok/s**, TTFT <100ms (HiCache+Mooncake 적용시), FP4/DGX Spark 단일머신 ~80 tok/s 디코딩 | [AETOSWire](https://www.aetoswire.com/en/news/2707202656473), [AntLing X INT4/FP4](https://x.com/AntLingAGI/status/2085024077434196211) |
| 속도(독립 측정) | AA 측정 base 약 **353~368 tok/s**, TTFT ~2초. OpenRouter 중앙값: Flash 110 tok/s vs Fin 80 tok/s | [AA base 페이지](https://artificialanalysis.ai/models/ling-3-0-flash), [OpenRouter 비교](https://openrouter.ai/compare/inclusionai/ling-3.0-flash/inclusionai/ling-3.0-flash-fin) |
| 가격(유료) | base: **$0.075 / $0.22 per 1M** (in/out, 1st-party). Fin 유료: **$0.042 / $0.1232** (NovitaAI 44% off 기준, OpenRouter) — 시점·프로바이더별 변동 큼. 무료 티어는 $0 | [AA](https://artificialanalysis.ai/models/ling-3-0-flash), [OpenRouter Fin 유료](https://openrouter.ai/inclusionai/ling-3.0-flash-fin) |
| 무료 | OpenRouter `:free` ($0) + **OpenCode Zen `ling-3.0-flash-fin-free` ($0)**. 단, 무료 기간엔 데이터 학습 사용 가능(아래 주의) | [OpenCode Zen](https://opencode.ai/docs/zen/) |
| 라이선스 | **MIT** (base 8/7, Fin 9/9 오픈소스) | [OrcaRouter](https://www.orcarouter.ai/blog/ling-3-0-flash), [BusinessWire](https://www.businesswire.com/news/home/20260908565055/en/Ant-Group-Open-Sources-Ling-3.0-flash-Fin-for-Real-World-Financial-Workflows) |
| 학습·에이전트 | 10,000+ 인터랙티브 환경 학습, Claude Code/Kilo/Qwen Code 등 호환 주장 | [HF](https://huggingface.co/inclusionAI/Ling-3.0-flash) |

### 2.2 Fin이 base랑 뭐가 다르냐

OrcaRouter 비교글 한 줄 요약 빌리면: **"Fin is a promise and Flash is a product"** (Fin은 약속, Flash는 제품). 같은 뇌(124B/5.1B), 다른 튜닝 목적 + 검증 격차. 출처: [OrcaRouter Fin vs Flash](https://www.orcarouter.ai/blog/ling-3-0-flash-fin-vs-ling-3-0-flash)

- Fin 추가물: 금융 리서치 end-to-end (검색→증거 검토→계산→모델링→리포트), 권위 소스 우선 검색, 멀티문서 조정(회계기간·정의·충돌 수치), 밸류에이션/스프레드시트 워크플로, **FinFIRST 벤치 오픈소스**. 출처: [HF Fin](https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin)
- Fin 한계 (공식도 인정): 복잡한 long-horizon 검증 더 필요, **가정·밸류에이션·투자 결론은 전문가 리뷰 필수, 투자조언 아님**. 출처: [HF Fin Limitations](https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin)

### 2.3 무료 쓰면 데이터 어떻게 되냐 (형님 주의)

OpenCode Zen 공식 문서: **Ling 3.0 Flash Fin Free는 무료 기간 동안 수집 데이터가 모델 개선에 사용될 수 있음**. Space Bunny Free·LongCat 2.5 Preview Free는 zero-retention이라 대조됨. 기밀 코드·금융자료 넣고 돌릴 거면 이거 꼭 알아둬라. 출처: [OpenCode Zen Privacy](https://opencode.ai/docs/zen/)

---

## 3. X(트위터) 분위기 — 긍정 7 : 부정·유보 3 느낌

전체적으로 **"무료치고 미쳤다" vs "벤더 숫자(1100 tok/s)는 못 믿는다"** 구도. 아래 인용은 전부 실존 포스트/기사임.

### 3.1 긍정파

**① Ahmad Awais (개발자 인플루언서)**
> 원문: "Ling-3.0-flash is now free in Command Code … and it's pretty darn good. having fun building with it."
> 번역: "Ling-3.0-flash가 Command Code에서 무료로 풀렸는데… 꽤 엄청 좋네. 갖고 놀면서 빌딩 중."
> 출처: https://x.com/MrAhmadAwais/status/2080377586224623631

**② Kilo Code 공식**
> 원문: "Ling 3.0 Flash is live on Kilo now, free for a limited time, and it's punching way above its weight for agentic coding tasks."
> 번역: "Ling 3.0 Flash가 Kilo에 라이브됐고 한시적 무료. 에이전틱 코딩에서 체급 فوق 펀치를 날리고 있음."
> 출처: https://x.com/kilocode (고정 포스트 계열, [Kilo 블로그 공지](https://blog.kilo.ai/p/announcing-ling-30-flash-free-on)와 교차 확인)

**③ 유튜버 WorldofAI 리뷰 (제목 자체가 평가)**
> 원문(영상 제목): "Ling 3.0 Flash First Test – A Surprisingly GOOD Coding Model!"
> 번역: "첫 테스트 — 놀랍도록 좋은 코딩 모델!"
> 내용: 브라우저 OS·서브웨이 FPS·3D 시계 사이트 테스트에서 피드백 반영해서 고치는 모습에 호평 ("competently fixing things", 256K 중 63% 써도 멀쩡히 수정). 단, 전체 다시 쓰기로 컨텍스트 까먹는癖 있음.
> 출처: https://www.youtube.com/watch?v=6hlMmq7lKsk

**④ Ant Ling 공식 (릴리즈 포스트)**
> 원문: "Today, we're releasing Ling-3.0-flash — a hybrid-reasoning MoE model built for production-scale agents. free to use through August 3, 2026. Try it in your coding, […]"
> 번역: "오늘 Ling-3.0-flash 릴리즈. 프로덕션급 에이전트용 하이브리드 추론 MoE. 8월 3일까지 무료. 코딩에 써봐라."
> 출처: https://x.com/AntLingAGI/status/2080351022028095681

**⑤ SEO 유튜버 Julian Goldie**
> 원문(기사 제목): "Ling 3.0 Flash Is Surprisingly Powerful For A FREE Model"
> 번역: "무료 모델치고 놀랍게 강력함" — 앱 빌드·리서치·에이전트에 쓸만하다는 취지.
> 출처: https://x.com/JulianGoldieSEO/article/2081835401703223334

### 3.2 부정·유보파 (형님이 진짜 봐야 할 쪽)

**⑥ Artificial Analysis 공식 (지식 신뢰도 디스)**
> 원문: "Ling 3.0 Flash scores -18 on AA-Omniscience, a 48 point improvement from Ling 2.6 Flash's -66. This is driven primarily by significant decrease […]"
> 번역: "Omniscience -18점. 전작(-66)보다 48점 올랐는데, 정확도 상승보다 환각 감소(거절/기권) 덕이 큼."
> 출처: https://x.com/ArtificialAnlys/status/2085878147782939064
> 해설: OrcaRouter도 같은 지적 — "hallucination fell (97% → 44%) while accuracy rose only slightly (16% → 18%)". 출처: https://www.orcarouter.ai/blog/ling-3-0-flash

**⑦ Siora Labs (Space Bunny 딥다이브, Ling 비교시사점)**
> 원문 취지: "The listing calls the model 'blazing-fast,' but the endpoint record publishes no throughput […] Measure the first call yourself before believing an operator adjective."
> 번역: "리스팅은 '초고속'이라는데 실측 throughput·latency 공개 없음. 형용사 믿지 말고 첫 호출 직접 재봐라."
> 출처: https://sioralabs.com/blog/space-bunny-alpha-deep-dive (스텔스 모델 글이지만 벤더 속도 주장 불신 논리는 Ling에도 그대로 적용 — OrcaRouter도 Ling 1100tok/s를 "vendor-only, marketing ceiling"이라 못박음: https://www.orcarouter.ai/blog/ling-3-0-flash)

**⑧ AI/ML API (물리 시뮬 비교, Space Bunny vs GLM-5.3 — Ling 진영 간접 참고)**
> 원문: "Space Bunny performs TERRIBLE in physics 💀 we tested Space Bunny against GLM 5.3 […] the Newton's cradle is where GLM 5.3 [won]"
> 번역: "Space Bunny 물리 개못함 ㅋㅋ GLM 5.3이 뉴턴 요람에서 이김"
> 출처: https://x.com/aimlapi/status/2102913874064257073 (Ling 직접 언급 아님. 비교 섹션용으로만 사용)

---

## 4. Reddit 평가 — 서브레딧별 정리

> 참고: 레딧은 직접 fetch가 막혀서 스레드 제목·투표수·검색 스니펫 인용으로 정리. 전부 실존 스레드임.

### r/LocalLLaMA (로컬·오픈웨이트 본진, 대체로 호의적 + 검증파)

**① "AntLing-3.0-flash is now live on OpenRouter, and free to …" — 275 upvotes, 51 comments**
- 반응: 무료 + 124B MoE + 에이전트 특화에 관심 폭발. 스레드 자체가 관심 지표.
- 출처: https://www.reddit.com/r/LocalLLaMA/comments/1v4m5cr/antling30flash_is_now_live_on_openrouter_and_free/

**② "Ling-3.0-flash is another potential model to test before …"**
> 원문(스니펫): "I tested Ling-3.0-flash with hard bugs and it fixed bugs that qwen3.6-27b could not. This models speed faster than deepseek v4 flash but […]"
> 번역: "어려운 버그에 테스트해봤는데 qwen3.6-27b가 못 고친 걸 고침. 속도는 deepseek v4 flash보다 빠름. 근데 […]"
> 출처: https://www.reddit.com/r/LocalLLaMA/comments/1veqd5c/ling30flash_is_another_potential_model_to_test/
- 형님 포인트: Qwen 3.6-27B급이랑 붙어도 코딩 실전 평이 나옴. 뒷말 잘린 건 아쉽지만 대체로 긍정.

**③ "inclusionAI/Ling-3.0-flash · Hugging Face" (가중치 공개 스레드)**
- 반응: "124B A5B 오픈웨이트 떴다. Kimi K3·DeepSeek-V4-Flash 나와서 묻힌 감 있는데 봐야 한다"는 취지.
- 출처: https://www.reddit.com/r/LocalLLaMA/comments/1vfdcd7/inclusionailing30flash_hugging_face/

**④ "Ling-3.0-flash-Fin weights released" — 121 upvotes**
- 반응: 금융판 가중치 릴리즈 자체에 관심. r/LocalLLaMA 검색 노출 기준 121 추천이면 중상급 관심.
- 출처: r/LocalLLaMA 내 스레드 (검색 경유, URL은 HF https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin 에서 교차 확인)

**⑤ Apple Silicon 실측파**
> 원문(스니펫): "Ling-3.0 flash is quite bright and its speed monster - 4-5 bit works like a charm 60-80 t/s TG."
> 번역: "Ling-3.0 flash 꽤 똑똑하고 속도 괴물임. 4~5bit 양자화 짱, 토큰 생성 60~80 t/s 나옴."
> 출처: https://www.reddit.com/r/LocalLLaMA/comments/1vphr8u/sota_apple_silicon_inference_august_15_2026/

**⑥ "Ling 3.0 Tiny is the strongest, fastest…" (형제 모델, 참고용)**
> 원문(스니펫): "This Ling 3.0 Tiny 8b param with 1.3b active is the fastest, smartest model I can run on my poor old pc, with 4gb vram."
> 번역: "가난한 내 PC(4GB VRAM)에서 돌아가는 것 중 제일 빠르고 똑똑함."
> 출처: https://www.reddit.com/r/LocalLLaMA/comments/1vqx6nd/ling_30_tiny_is_the_strongest_fastest_and/
- 시사점: Ling 패밀리 효율 설계 평판이 좋음. Fin(5.1B active)도 같은 설계 철학.

### r/opencodeCLI (실사용자, 무료 슬롯 관심)

**⑦ "Ling 3.0 Flash Fin FREE is on Opencode Zen"**
> 원문(본문 스니펫): "a finance-focused mixture-of-experts model built on the same backbone as Ling 3.0 Flash: 124B total parameters with ~5.1B active per token"
> 출처: https://www.reddit.com/r/opencodeCLI/comments/1w0vcli/ling_30_flash_fin_free_is_on_opencode_zen/
- 반응: Zen 무료 슬롯 추가로 실사용 문의 위주. 형님이 쓰는 그 슬롯 맞음.

### r/singularity (빅픽처 논쟁장)

**⑧ "GLM 5.3 Flash (Ox Alpha) benchmark comparisons"**
- Ling 직접 스레드는 아니고, 스텔스→정체공개 흐름(Ox Alpha = GLM-5.3-Flash) 논의. Ling도 같은 중국 Flash 경쟁 구도로 언급되는 맥락.
- 출처: https://www.reddit.com/r/singularity/comments/1vyywzk/glm_53_flash_ox_alpha_benchmark_comparisons/

---

## 5. 리더보드 (형님, 숫자 게임 정리)

### 5.1 Artificial Analysis (제일 공신력 있음)

**Fin (2026-09-16 AA 공식 기사):**
| 지표 | 점수 | 해석 |
|---|---|---|
| Intelligence Index | **23** | MiniMax-M2.7(23)과 동점인데 활성은 절반(5.1B vs 10B). Active 파라미터당 Pareto frontier 진입 |
| Finance & Accounting Index | **24** | VL(24)과 동점. 단, 지식 정확 17% vs 11%로 높지만 환각도 높음 (non-halluc rate 67% vs 81%) |
| GDPval-AA v2 | **1171 Elo** | VL 1225보다 ~50점 낮음, MiniMax-M2.7 1087보단 위 |
| AA-Briefcase | **967 Elo** | VL 986보다 살짝 낮음. rubric 통과율 23.5% vs 24.9% |
| AutomationBench-AA | **7%** | VL 16%의 절반 이하. 어려운 agentic에선 약함 |
| Terminal-Bench v4.0 | **0%** | VL도 0%. 터미널 하드코어 태스크는 둘 다 못 함 |
| 토큰 사용량 | **~67k / task** | VL(~50k)보다 34% 많이, MiniMax-M2.7(~21k)의 3.2배. 버보스함 |
| 출처 | | https://artificialanalysis.ai/articles/ant-group-releases-finance-focused-ling-3-0-flash-fin |

**Base Flash (버전 주의!):**
- OrcaRouter 인용 (구 AA 기준): **Intelligence Index 38**, Ling-2.6-flash(14)보다 +24, τ3-Banking 27%, GDPval 1108 Elo. 출처: https://www.orcarouter.ai/blog/ling-3-0-flash
- 현행 AA 페이지 (v4.3.2): **Intelligence Index 20**, 속도 353.4 tok/s로 동급 1위, verbose 4/4. 출처: https://artificialanalysis.ai/models/ling-3-0-flash
- 형님, 이거 헷갈리지 마라: **AA가 벤치 버전을 올리면서 점수 스케일이 바뀐 거**. 둘 다 맞는데 기준이 다름. 최신 기준으론 Fin 23 vs Flash 20이라 Fin이 오히려 위처럼 보이지만, 측정 시점·버전이 달라서 직접 비교는 금지. 추세만 봐라: "Flash 계열 효율 대비 선방".

### 5.2 OpenRouter 자체 지수 (실전 라우팅 기준)

| 비교 | Ling 3.0 Flash | Ling 3.0 Flash Fin |
|---|---|---|
| Intelligence Index | 20.1 | **22.6** |
| Coding Index | 50.6 | **55.6** |
| Agentic Index | 19.3 | **27.9** |
| Latency p50 | 0.98s | 1.31s |
| Throughput p50 | 110 tok/s | 80 tok/s |
| 가격 | $0.021 / $0.063 | $0.042 / $0.1232 (per 1M) |
| 출처 | | https://openrouter.ai/compare/inclusionai/ling-3.0-flash/inclusionai/ling-3.0-flash-fin |

- 해석: Fin이 지능·코딩·에이전트 지수 전부 위인데 느리고 비쌈. 금융 튜닝이 일반 지표까지 올린 건지, 측정 노이즈인지는 불명. 어쨌든 무료 티어면 체감가 $0이라 상관없음.

### 5.3 벤더 자체 주장 (믿되 검증해라)

- SWE-Bench Pro 56.6, Multilingual 72.4, AIME 2026 93.2, HLE 22.7 — 전부 **벤더 리포트, 독립 재현 없음**. 출처: [OrcaRouter 정리](https://www.orcarouter.ai/blog/ling-3-0-flash) (모델카드 표 인용)
- Fin 금융 벤치 (벤더): FinFIRST 52.85, FinSearchComp Verified 77.04, FinCRAFT 51.74, Finance Agent 69.19/59.81, APEX-Agents 29.17, SpreadsheetBench 86.5/21.81, τ3-banking 41. 출처: [HF Fin](https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin) / [OpenCode Data](https://opencode.ai/data/inclusionai/ling-3-0-flash-fin) / [benchlm](https://benchlm.ai/models/ling-3-0-flash-fin)
- benchlm 총평: "3개 벤치 행만 공개, 종합랭크 없음(unranked)". 출처: https://benchlm.ai/models/ling-3-0-flash-fin

### 5.4 LMArena / OpenCode 실사용 랭크

- **LMArena: 미등재** (2026-10-03 기준 검색에 Ling-3.0-flash-fin 아레나 Elo 없음). 형님, 아레나로 검증 불가.
- **OpenCode 실사용**: Fin 유료 ID 기준 **지난주 토큰 #20위, 2개월 2.4T 토큰, 점유율 0.3%, 유니크 유저 131K, 세션 350만+, 캐시 히트 89.4%**. 무료라 세션당 비용 $0. 출처: https://opencode.ai/data/inclusionai/ling-3-0-flash-fin
- llm-stats: Fin 종합 43.3점 전체 #39 (비교군 Grok 4.1 19.6). 출처: 검색 경유 llm-stats 비교 페이지.

---

## 6. 라이벌 비교 (Space Bunny Alpha / LongCat 2.5 / GLM-5.3-Flash)

형님이 이름 던진 것들 정리.

| 모델 | 정체 | 컨텍스트 | 가격 | 지능 지표 | Ling과 관계 |
|---|---|---|---|---|---|
| **Space Bunny Alpha** | 정체불명 스텔스 (`stealth/space-bunny-alpha`), 2026-09-23 등장. MiniMax M3.1설 있음(토크나이저 24/24 매치) | **1M** (출력 상한 524K) | 무료(스텔스 기간) | 미공개 (벤치 없음) | 직접 비교 불가. 코딩 에이전트 소비 1~5위가 전부 코딩 에이전트라 "코딩용"이라는 것만 확인. 출처: [Siora 딥다이브](https://sioralabs.com/blog/space-bunny-alpha-deep-dive), [SpaceBunny 벤치 정리](https://spacebunnyai.com/space-bunny-alpha-benchmarks.html) |
| **LongCat 2.5 Preview** | Meituan LongCat, OpenCode Zen `longcat-2.5-preview-free` 무료. zero-retention | 미공개(Preview) | 무료 | 미공개 | Zen 무료 슬롯 이웃. Ling Fin Free와 같은 "피드백 수집용 무료" 포지션. 출처: [OpenCode Zen](https://opencode.ai/docs/zen/) |
| **GLM-5.3-Flash** (a.k.a. Ox Alpha) | Zhipu Z.ai 정식 Flash. 스텔스 Ox Alpha 정체가 얘로 밝혀진 케이스 | — | $0.15 / $0.50 (Zen 기준) | **AA 42, Coding 72** (OrcaRouter 모델 목록 기준). DeepSWE 63.4 vs 46.2(5.2 대비) | **Ling보다 위**. 코딩·에이전트 둘 다 GLM-5.3-Flash가 한 체급 위. 대신 Ling은 무료. 출처: [OrcaRouter 모델 목록](https://www.orcarouter.ai/blog/ling-3-0-flash-fin-vs-ling-3-0-flash), [Z.ai 블로그](https://z.ai/blog/glm-5.3-flash) |
| **DeepSeek V4 Flash** | Flash 오픈웨이트 대장 | — | $0.14 / $0.28 | **AA 52** (max reasoning) | Ling(38/20)보다 위. τ3-Banking 39% vs Ling 27%. 출처: [OrcaRouter](https://www.orcarouter.ai/blog/ling-3-0-flash) |
| **Qwen3.8-27B / MiMo-V2.5** | 동급 오픈웨이트 | — | — | AA 34 / Ling-2.6-flash 대비 +24점 동급 (MiMo-V2.5 ≈ Ling 38) | Ling이 활성화 파라미터는 훨씬 작으면서 동점. 효율 승. 출처: [OrcaRouter](https://www.orcarouter.ai/blog/ling-3-0-flash) |

핵심 비교 인용:

> 원문: "GLM-5.3 beat Space Bunny Alpha (the new stealth model launched today) on Newton's cradle in a 5-scene physics test"
> 번역: "GLM-5.3이 오늘 출시된 스텔스 모델 Space Bunny Alpha를 뉴턴 요람 5씬 물리 테스트에서 이김"
> 출처: X @rohanpaul_ai 인용 포스트 (캐시 전문: bittide 아카이브) + 원본 https://x.com/aimlapi/status/2102913874064257073

> 원문(OrcaRouter): "Right now, Ling 3.0 Flash Fin is a promise and Ling 3.0 Flash is a product."
> 번역: "지금 Fin은 약속이고 Flash는 제품이다. 같은 뇌지만 검증 footing이 다름."
> 출처: https://www.orcarouter.ai/blog/ling-3-0-flash-fin-vs-ling-3-0-flash

---

## 7. 총평 (형님용, 투자조언 아님 명시)

> **이거 투자조언 아님. 모델 선택 조언도 그냥 참고용. 돈(실계좌·실매매) 걸린 의사결정은 형님이 알아서 하고, Fin 출력물은 무조건 전문가 검수 거치셈. 공식 모델카드에도 "do not constitute investment advice" 박혀 있음.** 출처: https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin

1. 형님, **Fin = 금융+코딩 겸용 무료픽으로는 꽤 괜찮다**. OpenRouter 지수상 base보다 코딩(55.6 vs 50.6)·에이전트(27.9 vs 19.3) 위, AA 금융 지수 24로 VL급. 공짜면 써봐라.
2. 근데 **어려운 에이전트(AutomationBench 7%, Terminal-Bench 0%)는 약함**. 복잡한 터미널·SaaS 자동화는 GLM-5.3-Flash나 유료 플래그십에 맡기고, Ling은 "양산형 실행 노드(싸고 빠른 일꾼)"로 써라. 벤더도 그렇게 포지셔닝함.
3. **숫자 장사는 걸러라**: 1100 tok/s·TTFT 100ms 미만은 벤더 전용 셋업 수치. 독립 측정은 350 tok/s대·TTFT 2초. 그래도 동급 1위라 느린 건 아님.
4. **지식 환각 주의**: Omniscience -18, Fin도 정확 17% vs 환각 33%. 금융 수치·밸류에이션은 무조건 원문 대조해라. FinFIRST가 "출처 추적" 내세우는데, 그거 믿고 복붙하면 터진다.
5. **프라이버시**: Zen 무료 슬롯은 학습 사용 가능. 형님 매매 전략·계좌·고객 코드 돌리면 유료 엔드포인트나 셀프호스팅(FP8 ~128GB)으로 가라.
6. **스텔스랑 헷갈리지 마라**: Space Bunny Alpha·Ox Alpha 같은 스텔스 슬롯이랑 달리 Ling Fin은 정체·가중치·벤치 다 공개된 애. 불확실성 리스크는 낮음. 반대로 말하면 "정체 밝혀지면 떡상" 같은 로또도 없음.
7. 다음 액션 추천: **① Zen 무료로 형님 실업무(코딩+간단 금융정리) 1주 돌려보고, ② GLM-5.3-Flash 유료랑 같은 프롬프트로 붙여보고, ③ 차이 없으면 공짜 계속 쓰고 차이 나면 돈 내라.** 라우터 failover 걸어두면 공짜 실험 리스크 없음.

---

## 8. 출처 모음 (형님, 팩트체크용)

- HF base: https://huggingface.co/inclusionAI/Ling-3.0-flash
- HF Fin: https://huggingface.co/inclusionAI/Ling-3.0-flash-Fin
- Ant Ling Docs: https://developer.ant-ling.com/en/docs/models/ling/
- OpenRouter Fin 무료: https://openrouter.ai/inclusionai/ling-3.0-flash-fin:free
- OpenRouter Fin 유료: https://openrouter.ai/inclusionai/ling-3.0-flash-fin
- OpenRouter Flash vs Fin 비교: https://openrouter.ai/compare/inclusionai/ling-3.0-flash/inclusionai/ling-3.0-flash-fin
- OpenCode Zen: https://opencode.ai/docs/zen/
- OpenCode Data Fin: https://opencode.ai/data/inclusionai/ling-3-0-flash-fin
- AA base: https://artificialanalysis.ai/models/ling-3-0-flash
- AA Fin 기사: https://artificialanalysis.ai/articles/ant-group-releases-finance-focused-ling-3-0-flash-fin
- OrcaRouter Fin vs Flash: https://www.orcarouter.ai/blog/ling-3-0-flash-fin-vs-ling-3-0-flash
- OrcaRouter Flash 해설: https://www.orcarouter.ai/blog/ling-3-0-flash
- Kilo 공지: https://blog.kilo.ai/p/announcing-ling-30-flash-free-on
- BusinessWire Fin 오픈소스: https://www.businesswire.com/news/home/20260908565055/en/Ant-Group-Open-Sources-Ling-3.0-flash-Fin-for-Real-World-Financial-Workflows
- TechNode: https://technode.com/2026/08/28/ant-group-launches-finance-tuned-ling-model-plans-to-open-source-it-next-week/
- benchlm Fin: https://benchlm.ai/models/ling-3-0-flash-fin
- Reddit ①: https://www.reddit.com/r/LocalLLaMA/comments/1v4m5cr/antling30flash_is_now_live_on_openrouter_and_free/
- Reddit ②: https://www.reddit.com/r/LocalLLaMA/comments/1veqd5c/ling30flash_is_another_potential_model_to_test/
- Reddit ③: https://www.reddit.com/r/LocalLLaMA/comments/1vfdcd7/inclusionailing30flash_hugging_face/
- Reddit ⑤: https://www.reddit.com/r/LocalLLaMA/comments/1vphr8u/sota_apple_silicon_inference_august_15_2026/
- Reddit ⑦: https://www.reddit.com/r/opencodeCLI/comments/1w0vcli/ling_30_flash_fin_free_is_on_opencode_zen/
- X AhmadAwais: https://x.com/MrAhmadAwais/status/2080377586224623631
- X AntLing 릴리즈: https://x.com/AntLingAGI/status/2080351022028095681
- X AA: https://x.com/ArtificialAnlys/status/2085878147782939064
- X aimlapi: https://x.com/aimlapi/status/2102913874064257073
- Siora Space Bunny: https://sioralabs.com/blog/space-bunny-alpha-deep-dive
- Z.ai GLM-5.3-Flash: https://z.ai/blog/glm-5.3-flash
