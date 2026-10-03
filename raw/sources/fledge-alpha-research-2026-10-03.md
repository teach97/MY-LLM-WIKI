# Fledge Alpha Free 리서치 (형님용 정리)

> 작성일: 2026-10-03 / 조사 대상: "Fledge Alpha Free" (OpenCode 무료 스텔스 모델)
> 한 줄 요약: 형님, 이거 10월 1~2일에 갑툭튀한 OpenCode 전용 무료 스텔스 모델이야. 정체 불명인데 Thinking Machines Lab(Inkling 후속?) 썰이 제일 뜨거워. 그리고 라우터(뒤에 모델 3개 돌려막기)라는 목격담도 있어.

---

## 1. Fledge Alpha가 뭔데?

- **정체: OpenCode Zen 전용 무료 스텔스 모델.** OpenRouter 스텔스 슬롯(Ox/Space Bunny/Union Alpha 라인)이랑은 달라. OpenRouter 카탈로그에 `stealth/fledge-alpha` 같은 건 없고, OpenCode가 자기 게이트웨이(Zen)에서만 푸는 모델이야.
  - 출처: OpenCode Zen 공식 문서 모델 목록에 `Fledge Alpha Free | fledge-alpha-free` 등재 — https://opencode.ai/docs/zen
  - 모델 ID: `opencode/fledge-alpha-free` (엔드포인트 `https://opencode.ai/zen/v1/chat/completions`, OpenAI-compatible)
- **공개일: 2026-10-01 전후.** OpenCode Data 일별 집계를 보면 9/30엔 토큰 861K(테스터 1명 수준) 찍다가 10/01에 29B, 10/02에 208B로 폭발. 사실상 10월 1일이 데뷔일이야.
  - 출처: https://opencode.ai/data/unknown/fledge-alpha
- **가격: 완전 무료 (input/output/cached 전부 Free).** 단, **"limited time(기간 한정)"** + **"free period 동안 수집 데이터가 모델 개선에 사용될 수 있음"** 조건 붙어. Space Bunny Free / LongCat 2.5 Preview Free가 zero-retention(학습에 안 씀)인 거랑 대조돼. 형, 회사 코드·비밀키 박으면 안 돼.
  - 출처: https://opencode.ai/docs/zen (Pricing + Privacy 섹션)
- **Lab 표기: Unknown.** OpenCode Data 페이지에서 Lab이 "Unknown", Context/Output/Knowledge 전부 "Unknown"이야. 공식 스펙이 아직 없는 상태.
  - 출처: https://opencode.ai/data/unknown/fledge-alpha

### 정체 썰 3파전 (아무도 확정 못 함)

**썰 ① Thinking Machines Lab (미라 무라티네) — 현재 제일 뜨거운 썰**
- X의 AI Tracker Bot이 지문 분석 결과를 올림. OpenCode PR이 Tinker(Thinking Machines의 파인튜닝 API)를 참조하고, reasoning 설정이 Inkling이랑 일치하고, 이미지 테스트 16개 전부 40px 패치 그리드를 따랐다는 거야. 단, 텍스트 토크나이저는 정확히 매칭되는 게 없어서 미확정이라고 스스로 선 그음.
  - 원문 (EN): *"Fledge Alpha points toward Thinking Machines Lab 👀 OpenCode's PR references Tinker. Its reasoning settings match Inkling's, and all 16 image tests followed a 40px patch grid. No exact text-tokenizer match yet, so the owner and underlying model remain unconfirmed."*
  - 번역: "Fledge Alpha는 Thinking Machines Lab을 가리키고 있어 👀 OpenCode PR이 Tinker를 참조하고, reasoning 설정은 Inkling과 일치하고, 이미지 테스트 16개 전부 40px 패치 그리드를 따랐어. 아직 텍스트 토크나이저가 정확히 매칭된 건 없어서, 소유자와 기반 모델은 미확정이야."
  - 출처: https://x.com/aitrackerbot/status/2105751970107560102
- 레딧에서도 "Fledge Alpha = 업데이트된 Inkling?" 스레드가 두 개나 파였어 (r/opencode, r/opencodeCLI).
  - 출처: https://www.reddit.com/r/opencode/comments/1wvaxn8/fledge_alpha_is_an_updated_inkling / https://www.reddit.com/r/opencodeCLI/comments/1wvayj8/fledge_alpha_is_an_updated_inkling
- 참고로 Inkling이 뭔지: Thinking Machines Lab이 2026-07-15에 낸 첫 오픈웨이트 모델. MoE 975B(활성 41B), 컨텍스트 최대 1M, 45T 토큰(텍스트·이미지·오디오·비디오) 학습, Apache-2.0. Tinker에서 파인튜닝 지원. 랩 스스로 "최강 모델 아니다, 커스텀용 베이스"라고 인정한 놈.
  - 출처: https://thinkingmachines.ai/news/introducing-inkling / https://simonwillison.net/2026/Jul/16/inkling

**썰 ② 라우터(Router) — 뒤에 모델 3개 돌려막기**
- r/opencode 스레드 제목 자체가 "New fledge alpha model is a router"야. 본문 요약: 밑에 세 개 모델이 돌고 있음 — DeepSeek 4.1, Kimi(K3?), 그리고 unknown 하나. 그리고 "censor API layer가 위에 없어서 중국산은 아닐 듯"이라는 추측도 붙어.
  - 원문 (EN, 스레드 제목+요약): *"New fledge alpha model is a router. There three different models currently under hood. Deepseek 4.1, kimi (k3?) and unknown one (maybe...)"* / *"No censor api layer on top, so its likely not a chinese [model]"*
  - 번역: "새 fledge alpha 모델은 라우터다. 밑에 현재 세 개의 다른 모델이 돌아가고 있다. DeepSeek 4.1, Kimi(K3?), 그리고 정체불명 하나(아마…)" / "위에 검열 API 레이어가 없으니 중국산은 아닐 가능성이 높다"
  - 출처: https://www.reddit.com/r/opencode/comments/1wvfc2a/new_fledge_alpha_model_is_a_router

**썰 ③ DeepSeek V4.1 Pro?**
- r/opencode에 "could fledge alpha be deepseek v4.1 pro?" 스레드, r/LocalLLaMA에 "Now which lab is behind fledge alpha?" 스레드가 따로 있어. 근거는 "calculating... particularly strong model and has vision capabilities(생각보다 쎄고 비전 된다)" 정도. 썰 ②의 라우터 구성원 중 하나가 DeepSeek이라는 얘기랑 맞물려.
  - 원문 (EN): *"It appears to be a particularly strong model and has vision capabilities!"*
  - 번역: "상당히 강한 모델로 보이고 비전 기능도 있어!"
  - 출처: https://www.reddit.com/r/opencode/comments/1wv82yd/could_fledge_alpha_be_deepseek_v41_pro / https://www.reddit.com/r/LocalLLaMA/comments/1wv7t3a/now_which_lab_is_behind_fledge_alpha

---

## 2. 스펙 (확정 vs 미확정)

| 항목 | 내용 | 상태 |
|---|---|---|
| 모델 ID | `opencode/fledge-alpha-free` (Zen), Data 페이지는 `fledge-alpha` | 확정 (공식 문서) |
| 가격 | input/output/cached 전부 Free, 기간 한정 | 확정 (공식 문서) |
| 컨텍스트 | Unknown (공식 표기 없음). Inkling 썰이면 최대 1M이겠지만 Fledge 실측 아님 | 미확정 |
| 멀티모달 | 비전 된다는 목격담 있음 ("has vision capabilities"), 이미지 패치그리드 지문도 있음 | 목격담 수준 |
| Reasoning | 조절식(reasoning effort) 흔적 — Inkling이랑 설정 일치한다는 분석 | 분석 주장 수준 |
| 데이터 정책 | 무료 기간 수집 데이터가 모델 개선에 쓰일 수 있음 (zero-retention 아님!) | 확정 (공식 문서 Privacy) |
| 공개일 | 2026-10-01 전후 (Data 일별 집계 기준) | 집계 기반 추정 |
| 리더보드 | Artificial Analysis / LMArena 등재 없음 (너무 최신+스텔스라 당연) | 확인됨 (없음) |

- OpenCode Data 수치 (2026-10-03 06:44 UTC 업데이트 기준): 지난주 토큰 기준 **#15위, 302B 토큰**, 유니크 유저 5.7K, 완료 세션 170,485, 세션당 평균 1.8M 토큰, 총 지출 $0, 캐시 히트 92.9%. 일별: 10/01 29B → 10/02 208B → 10/03 65B(집계 중). 출시 3일 만에 붙박이 유료 모델들(DeepSeek V4 Pro, MiniMax, GPT-6 Luna 등) 사이에 낀 거 보면 초반 흡입력은 진짜야.
  - 출처: https://opencode.ai/data/unknown/fledge-alpha
- 참고: 같은 Data 페이지 초기 스냅샷(검색 캐시)에서는 #44위·939K 토큰으로 찍혔는데, 이건 집계 시작 직후(10/01) 수치야. 지금(10/03)은 #15·302B로 뛰었어. 혼동 금지.
- 국가별 분포: 미국 16.8%, 인도 11.4%, 브라질 6.6%, 인도네시아 5.6%, 중국 5.5% 순. 레딧에 "중국 전체가 막히지 않은 것 같다"(whole of china isnt blocked) 같은 글이 있는데, 실제로 중국 트래픽 5.5% 찍혀 있어. 지역 차단 논란은 아래 레딧 섹션 참고.
  - 출처: https://opencode.ai/data/unknown/fledge-alpha / https://www.reddit.com/r/opencode/comments/1wvtr5v/fledge_alpha

---

## 3. X(트위터) 분위기

솔직히 말하면, 형, **Fledge Alpha 단독으로 X에서 터진 건 아직 거의 없어.** Ox Alpha 때(Stripe CEO 패트릭 콜리슨이 "very impressive" 붙인 거) 같은 빅샷 인용은 제로. 현재 X 신호는 딱 두 갈래야:

1. **AI Tracker Bot 지문 분석 (긍정도 부정도 아닌 탐정 모드, 조회수 30K)**
   - 원문 (EN): *"Fledge Alpha points toward Thinking Machines Lab 👀 OpenCode's PR references Tinker. Its reasoning settings match Inkling's, and all 16 image tests followed a 40px patch grid. No exact text-tokenizer match yet, so the owner and underlying model remain unconfirmed."*
   - 번역: 위 1번 썰 참고. "Thinking Machines 쪽 가리키는데 확정은 아니다"가 요지.
   - 출처: https://x.com/aitrackerbot/status/2105751970107560102
   - 달린 댓글 중 Seth Rose: *"Tinker is a flexible API for efficiently fine-tuning open source models with LoRA… Have they fine tuned GLM 5.3?"* (번역: "Tinker는 LoRA로 오픈소스 파인튜닝하는 유연한 API인데… 걔네가 GLM 5.3을 파인튜닝한 거 아냐?") — 즉 X에서도 "Tinker 흔적 = Thinking Machines" vs "GLM 파인튜닝물" 두 썰이 맞붙는 중.
2. **OpenCode 공식 계정 (@opencode)은 아직 Fledge를 직접 언급 안 함 (9/29 기준).** 대신 같은 시기 "space bunny got an upgrade… free period extended to 10/05" 같은 스텔스 모델 운영 공지만 올라와. Fledge는 아직 공식 포스트 없이 조용히 풀린 상태야.
   - 출처: https://x.com/opencode

분위기 한 줄: **기대감 > 실망감인데, 근거는 "공짜 + 쎄다" 체감이지 누구 작품인지는 아무도 모름.**

---

## 4. Reddit 평가 (서브레딧별)

전부 2026-10-01~02에 파인 따끈한 스레드들이야. Reddit이 403을 뱉어서 본문 전문은 검색 스니펫+제목 기반으로만 인용했어 (전문 크롤링 불가 — 아래 한계 참고).

### r/opencode — "New fledge alpha model is a router" (핵심 스레드)
- 주장: 라우터다, 밑에 3개 모델 (DeepSeek 4.1 / Kimi K3? / unknown). 검열 레이어 없어서 중국산 아닐 듯.
- 원문 (EN): *"New fledge alpha model is a router. There three different models currently under hood. Deepseek 4.1, kimi (k3?) and unknown one (maybe…)"*
- 번역: "새 fledge alpha 모델은 라우터야. 지금 밑에서 세 개의 다른 모델이 돌아가고 있어. 딥시크 4.1, 키미(K3?), 그리고 정체불명 하나(아마…)"
- 출처: https://www.reddit.com/r/opencode/comments/1wvfc2a/new_fledge_alpha_model_is_a_router

### r/opencode — "could fledge alpha be deepseek v4.1 pro?"
- 주장: 꽤 강하고 비전 됨. DeepSeek V4.1 Pro 아니냐?
- 원문 (EN): *"It appears to be a particularly strong model and has vision capabilities!"*
- 번역: "상당히 강한 모델로 보이고 비전 기능도 있어!"
- 출처: https://www.reddit.com/r/opencode/comments/1wv82yd/could_fledge_alpha_be_deepseek_v41_pro

### r/opencode / r/opencodeCLI — "Fledge Alpha is an updated Inkling?" (2개 스레드)
- 주장 A: Inkling이랑 연관 있어 보인다 (Tinker/reasoning 지문 연계).
- 주장 B (반론/관측): *"Inkling was available in my country, Fledge Alpha is not. Don't know if that means anything though."* (번역: "Inkling은 우리 나라에서 됐는데 Fledge Alpha는 안 돼. 이게 뭘 의미하는진 모르겠지만.")
- 주장 C (관측): *"Inkling is no longer available on NVIDIA NIM"* + *"OpenRouter has OpenCode listed as the only provider"* (번역: "Inkling이 NVIDIA NIM에서 내려갔고, OpenRouter에는 OpenCode가 유일한 제공자로 떠 있음") — 수급 교체 썰의 정황 근거.
- 출처: https://www.reddit.com/r/opencode/comments/1wvaxn8/fledge_alpha_is_an_updated_inkling / https://www.reddit.com/r/opencodeCLI/comments/1wvayj8/fledge_alpha_is_an_updated_inkling

### r/LocalLLaMA — "Now which lab is behind fledge alpha?"
- 주장: OC에 새 무료/트라이얼 모델 떴는데 디테일 없음. DeepSeek V4.1 Pro 아니냐는 질문으로 시작.
- 원문 (EN): *"New free/trial model dropped on OC. Details are yet to be provided. Could this be deepseek v4.1 pro?"*
- 번역: "OC에 새 무료/체험 모델 떴어. 디테일은 아직 없음. 이거 딥시크 v4.1 프로 아냐?"
- 출처: https://www.reddit.com/r/LocalLLaMA/comments/1wv7t3a/now_which_lab_is_behind_fledge_alpha

### r/opencode — "what's the best free model on opencode right now"
- 맥락: Space Bunny랑 Fledge Alpha 중에 뭘 써야 하냐는 질문글. 아직 결론 없음. 비교 섹션에서 다룸.
- 출처: https://www.reddit.com/r/opencode/comments/1ww6kn8/whats_the_best_free_model_on_opencode_right_now

### r/opencode — "Fledge Alpha" (지역 차단 관련)
- 요약에 따르면 "중국 전체가 Fledge Alpha 사용에서 막히지 않은 것 같다"는 관측. Data 페이지에 중국 5.5% 찍힌 거랑 일치. 단, 위 Inkling 스레드에서는 반대로 특정 국가에서 안 된다는 보고도 있어서 지역별 편차 있음.
- 출처: https://www.reddit.com/r/opencode/comments/1wvtr5v/fledge_alpha

**레딧 총평:** 긍정(공짜치고 쎄다) vs 경계(라우터냐, 누구냐, 데이터 쓰인다) 반반. Ox Alpha 때처럼 "며칠 써봤는데 인상적이다" 같은 장문 후기는 아직 안 나왔어. 다들 정체 파헤치는 중.

---

## 5. 리더보드 (Artificial Analysis / LMArena 등)

- **Artificial Analysis: 등재 없음.** 스텔스+OpenCode 전용이라 AA가 긁을 수 있는 퍼블릭 API가 없어. GLM-5.3(59점대), Claude Opus 4.7/4.8(55~56점) 같은 건 있지만 Fledge는 없음.
- **LMArena: 등재 없음.** 같은 이유. (참고로 LMArena 자체 신뢰성 논란 — provider가 프라이빗 모델 여러 개 돌려보고 좋은 것만 공개한다는 지적 — 은 별개 이슈. https://discuss.privacyguides.net/t/lmarena-artificial-analysis/27077)
- **있는 건 OpenCode Data 자체 랭킹뿐: 지난주 #15위 (302B 토큰).** 이건 성능 순위가 아니라 사용량 순위야. 착각 금지.
  - 출처: https://opencode.ai/data/unknown/fledge-alpha

---

## 6. 비교 언급 정리 (Space Bunny / LongCat 2.5 / GLM-5.3-Flash 등)

| 비교 대상 | 관계 / 언급 내용 | 출처 |
|---|---|---|
| Space Bunny Alpha/Free | 같은 Zen 무료 스텔스 라인업. 근데 **데이터 정책이 다름**: Space Bunny는 zero-retention(학습에 안 씀), Fledge는 free period 데이터가 개선에 쓰일 수 있음. OpenCode 공지 기준 Space Bunny는 5일 연속 OpenCode 1위·40T 토큰, 무료 연장(~10/05). Fledge는 출시 3일 만에 #15로 급상승 중. "둘 중 뭐 쓰냐" 레딧 질문글 존재 | https://opencode.ai/docs/zen, https://x.com/opencode, https://www.reddit.com/r/opencode/comments/1ww6kn8/whats_the_best_free_model_on_opencode_right_now |
| LongCat 2.5 Preview Free | 같은 Zen 무료 라인업 동료. 역시 zero-retention이라 프라이버시는 얘가 나음 | https://opencode.ai/docs/zen |
| GLM-5.3-Flash (Z.ai) | **Ox Alpha의 정체로 확정된 모델** (OpenRouter 공식 표기: "Ox Alpha was Z.ai GLM-5.3-Flash")이랑 헷갈리면 안 됨. Fledge 정체썰 중 "GLM 5.3 파인튜닝물 아니냐"(Seth Rose 댓글)는 있지만 확정 아님. 토크나이저 지문 대조법(Ox 때 GLM 5.3과 25개 프롬프트셋 매칭+75토큰 오프셋)이 Fledge에도 시도됐으나 텍스트 매칭 실패 | https://wavect.io/blog/ox-alpha-free-ai-model-guide-2026, https://x.com/aitrackerbot/status/2105751970107560102 |
| DeepSeek V4.1 / Kimi K3 | 라우터썰에서 "밑에 깔린 모델"로 지목됨. 단독 정체썰(DeepSeek V4.1 Pro?)도 있음. Zen 유료 라인업에 DeepSeek V4 Pro($1.74/$3.48), Kimi K3($3/$15)가 있는 걸 보면, 무료 Fledge로 맛만 보여주고 유료로 유도하는 구조일 수도 | https://www.reddit.com/r/opencode/comments/1wvfc2a/new_fledge_alpha_model_is_a_router, https://opencode.ai/docs/zen |
| Big Pickle | 같은 Zen 무료 스텔스. "rotating capabilities(능력 수시로 바뀜)"라는 설명이 있어서 Fledge 같은 라우터일 가능성 시사? 직접 비교글은 아직 없음 | https://opencode.ai/docs/zen |
| Inkling (Thinking Machines) | 스펙 비교: 975B MoE(41B 활성), 1M 컨텍, 45T 학습, Apache-2.0, Tinker 파인튜닝. Fledge가 이거 업뎃판이면 서구권 오픈웨이트 기반이라는 점에서 중국 모델 썰과 정면 배치 | https://thinkingmachines.ai/news/introducing-inkling |

---

## 7. 총평 (형님, 이거 읽고 판단해)

1. **쓸 만해?** — 응, 공짜 코딩 모델로는 현재 최상급 라인에 들어갈 듯. 출시 3일 만에 OpenCode 사용량 15위(302B 토큰, 5.7K 유저)가 그 증거야. "공짜치고 쎄다"는 목격담이 레딧·X 공통이야.
2. **정체는?** — 모른다, 진짜. Thinking Machines(Inkling 후속) 썰이 지문 근거로는 제일 구체적인데, 토크나이저 매칭 실패라 확정 아니야. 라우터(DeepSeek+Kimi+α 돌려막기) 썰도 만만찮아. 둘 다 맞을 수도 있어 (라우터 뒤에 Inkling 파인튜닝이 섞여 있다든가).
3. **조심할 점?** — 딱 하나. **Space Bunny/LongCat이랑 달리 Fledge는 zero-retention이 아니야.** 무료 기간 네 프롬프트가 학습에 쓰일 수 있어. 회사 레포·키·고객 데이터는 넣지 마. 테스트용·토이 프로젝트·공개 코드에만 써.
4. **언제까지 공짜?** — "limited time"이야. Ox Alpha가 일주일, Space Bunny가 연장+연장이었던 것처럼 Fledge도 예고 없이 끝나거나 유료 모델로 이름 바꿔서 나올 수 있어 (Ox → GLM-5.3-Flash 전례).
5. **리더보드는?** — AA/LMArena에 없어. "1위" 같은 말은 전부 사용량 순위(#15)지 성능 순위가 아니야. 누구 말 믿지 말고 형님이 직접 작은 태스크로 같은 프롬프트 돌려보고 판단해.

> ⚠️ 이 글은 투자조언 아님. 모델 선택 조언도 아니고, 그냥 공개 정보 모아본 리서치야. 코딩 모델 고르는 건 형님 책임. 돈 되는 결정은 형님이 해, 난 조사만 했어.

### 조사 한계 (솔직히 고백)
- Reddit이 봇 차단(403)을 뱉어서 스레드 본문 전문을 못 긁었어. 제목+검색 스니펫 기반 인용이라 댓글 여론 디테일은 놓쳤을 수 있어.
- X도 로그인 벽 때문에 AI Tracker Bot 트윗 + OpenCode 공식 계정 공개분까지만 확인. 인용 수·대규모 반응 수집은 못 함.
- Fledge 출시 3일차라 리더보드·벤치마크·장문 후기가 아직 없음. 일주일 뒤에 다시 긁으면 완전히 다른 그림일 수 있어.
