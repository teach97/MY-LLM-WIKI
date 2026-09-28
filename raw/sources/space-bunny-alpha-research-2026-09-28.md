# 스페이스버니(SpaceBunny) 리서치 — 형님용 정리

형님, 결론부터 말하면 지금 X랑 레딧에서 뜨는 "SpaceBunny"는 코인이 아니야. **AI 스텔스 모델 Space Bunny Alpha** 얘기야. 코인 쪽은 동명 잡코인들이便乘(편승)으로 붙은 거고, 본체는 OpenRouter + OpenCode발 AI 모델이야. 하나씩 구분해서 정리해줄게.

---

## 1. 스페이스버니가 뭔지 특정 — 동명 후보 구분

### 1-A. 본체: Space Bunny Alpha (AI 스텔스 모델) — 이게 지금 화제야

- 정체: OpenRouter 스텔스 슬롯에 올라온 익명 LLM. `stealth/space-bunny-alpha`라는 ID로 호출해. OpenRouter가 직접 만든 게 아니라 "third-party provider가 익명 유지 중"이라고 명시해놨어. 즉 라우팅만 OpenRouter가 하고 주인은 따로 있다는 거지.
  - 출처: https://openrouter.ai/stealth/space-bunny-alpha
  - 스텔스 모델 정책 설명: https://openrouter.ai/provider/stealth
- 출시일: 2026-09-22 ~ 23일. OpenRouter 페이지에 Released Sep 22, 2026으로 찍혀 있고, OpenCode 공지도 9월 23일이야.
  - 출처: https://openrouter.ai/stealth/space-bunny-alpha
  - 출처: https://x.com/opencode/status/2102767716666941864
  - 출처: https://didcodexreset.com/news/5d3729ae8d21495f801563f8.html
- 스펙 (공식 표기): 1M 컨텍스트, 최대 524k 컴플리션, 텍스트/이미지/비디오 입력 → 텍스트 출력, 툴콜링/JSON 지원, reasoning effort 5단계(low/medium/high/xhigh/max), 추론 필수, 무료 프리뷰.
  - 출처: https://openrouter.ai/stealth/space-bunny-alpha
  - 출처: https://docs.aimlapi.com/api-references/text-models-llm/stealth/space-bunny-alpha
  - 출처: https://aimlapi.com/models/space-bunny-alpha
  - 출처: https://kilo.ai/models/stealth-space-bunny-alpha
  - 출처: https://pi.dev/models/opencode/space-bunny-free
- OpenCode에서는 `space-bunny-free`로 일주일 무료 풀었어. 1M 컨텍스트, 멀티모달, Zero Data Retention 내세웠지.
  - 출처: https://x.com/opencode/status/2102767716666941864
  - 출처: https://pi.dev/models/opencode/space-bunny-free
  - 출처: https://www.linkedin.com/posts/hasantoxr_opencode-just-made-space-bunny-free-for-the-activity-7508585028516499456-tXjS
- OpenCode 쪽 사용량 데이터 페이지도 따로 있어. 비교 페이지에서 MiniMax-M3랑 나란히 놓고 비교하더라.
  - 출처: https://opencode.ai/data/compare/minimax/minimax-m3/unknown/space-bunny
  - 출처: https://opencode.ai/data/unknown/alpha-space-bunny-test

### 1-B. 유력 정체: MiniMax M3.1이라는 썰이 제일 세

- 형, 이게 핵심이야. 공식 확인은 없어. 근데 토크나이저 지문이 MiniMax M2/M3랑 50개 스트링 전부 정확히 일치한대. OpenRouter가 직접 돌린 테스트에서도 그렇고, 서드파티(@cheatyyyy)도 독립적으로 확인했어.
  - 출처: https://x.com/cheatyyyy/status/2102781392199565683
  - 출처: https://x.com/cheatyyyy/status/2102782294138491019
  - 출처: https://www.reddit.com/r/opencode/comments/1wp4kmi/m31_is_spacebunny
  - 출처: https://www.reddit.com/r/opencodeCLI/comments/1wpv45g/m31_is_space_bunny_alpha
- 타이밍도 맞아떨어져. MiniMax가 8월 26일에 M3.1 거의 다 됐다고 하고, 한 달도 안 돼서 9월 23일에 1M 멀티모달 익명 모델이 뜬 거야.
  - 출처: https://www.reddit.com/r/opencode/comments/1wp4kmi/m31_is_spacebunny
  - 출처: https://www.threads.com/@koltregaskes/post/Ddo2gbvGhWL/mini-max-m-release-soon-space-bunny-alpha-stealth-model-might-be-a-mini-max)
- 반론도 있어. HF 커뮤니티 글에서는 MiniMax설/OpenAI설 다 "확정 아니다, 스타일 모방·셀프리포트 오류·래퍼 프롬프트 왜곡 가능"이라 경고해. 그러니까 형, "유력하지만 미확정"으로 받아들여.
  - 출처: https://huggingface.co/blog/paidaxccc/space-bunny-alpha-ai-model-specs-api-benchmarks-an
- 다른 썰들: "Taco Bell 모델"이라는 농담성 댓글, Mistral 아니냐는 질문, 서양 모델처럼 느껴진다는 롤플 유저 평도 있어. 다 소수설이야.
  - 출처: https://www.reddit.com/r/opencode/comments/1wodncp/space_bunny_is_minimax_m31
  - 출처: https://www.reddit.com/r/MistralAI/comments/1wodh35/is_spacebunnyalpha_a_mistral_model
  - 출처: https://www.reddit.com/r/SillyTavernAI/comments/1wo8csn/new_stealth_model_in_openrouter_space_bunny_alpha

### 1-C. 헷갈리게 하는 애들: $SBA 밈코인 무더기 (Solana)

- 형, 이거 중요해. AI 모델 뜨자마자 Solana에 "Space Bunny Alpha / SBA" 이름 단 밈코인이 여러 개 박혔어. 정식 프로젝트 아냐, 펌프펀 식便乘 토큰들이야.
  - 예: Jupiter에 $0.0000027353, 24h 볼륨 $206K, -39.58% 찍힌 SBA가 있어: https://jup.ag/tokens/DAfkzSx4QRiM5P1kuSxYX3dV58FPy2gzGj55YuJgwinb
  - Solana Compass에도 SBA $0.0000033, 시총 $3.28K, 24h 볼륨 $10.24K짜리 있어: https://solanacompass.com/tokens/7eGukyFGJKXRPtHpPH22yjUaB4eegXDvktvxWgADZYVw
  - Solana Compass 같은 페이지에 동명 토큰 후보 6개가 시총 $160K부터 $1까지 따로 listed 돼 있어. 컨트랙트가 제각각이라는 거지: https://solanacompass.com/tokens/7eGukyFGJKXRPtHpPH22yjUaB4eegXDvktvxWgADZYVw
  - GeckoTerminal에도 SBA/SOL 풀 유동성 $2.02짜리 초저유동 풀 있어: https://www.geckoterminal.com/solana/pools/FEC6swG3FWX4oEFkMpqMUKhAr6xLxmD8FZbzFQp179e7
- 이 코인들은 AI 모델이랑 공식 연결 없어. 백서/공식 사이트/오디트 없어. 그냥 이름 하이재킹이야.
- 그 외 "Space Token(SPACE)" Final Autoclaim용 토큰이랑은 이름만 비슷하고 별개야. 형이 찾는 거랑 무관해.
  - 출처: https://coinmarketcap.com/currencies/space-token

### 1-D. spacebunny.app / spacebunnyalpha.com — 래퍼 사이트지 공식 주인 아님

- spacebunny.app라는 데가 플레이그라운드/문서/요금 페이지를 운영하는데, HF 글 본인도 "독립 product site"라고 밝혀. 모델 주인이 아니야.
  - 출처: https://huggingface.co/blog/paidaxccc/space-bunny-alpha-ai-model-specs-api-benchmarks-an
- 벤치마크 자칭 수치(GPQA Diamond 60문항 82%, MMLU-Pro 75%, HLE 300문항 46.1%, AI BENCHY 7.0/10)는 spacebunnyalpha.com발 독립 테스트야. 풀셋이 아니라 서브셋이라 직접 비교하면 안 돼.
  - 출처: https://huggingface.co/blog/paidaxccc/space-bunny-alpha-ai-model-specs-api-benchmarks-an

---

## 2. X(트위터) 분위기

형, X는 "기대 + 까기" 반반이야. 스캠 의심은 AI 모델 자체에 대한 게 아니라, 나중에 가격 매기거나 가짜 코인 낚시 뜰 거 조심하라는 쪽이야.

### 긍정 / 호기심

- OpenCode 공식: "Space Bunny (stealth model) is free for the next week - 1M Context - Multi-modal - Zero Data Retention." 2026-09-23 07:31. 이게 도화선이야.
  - 출처: https://x.com/opencode/status/2102767716666941864
- @AiBattle_: MiniMax M3.1 아니냐는 추측 포스팅. 커뮤니티에서 인용돼.
  - 출처: https://x.com/AiBattle_/status/2102775779054502289 (via https://www.threads.com/@koltregaskes/post/Ddo2gbvGhWL/mini-max-m-release-soon-space-bunny-alpha-stealth-model-might-be-a-mini-max) )
- @cheatyyyy: "most certainly MiniMax M3.1. text tokenizer perfectly matches" — 토크나이저 확정 타령. 비전 토크나이저는 다르대, 개량 가능성 언급.
  - 출처: https://x.com/cheatyyyy/status/2102781392199565683
  - 출처: https://x.com/cheatyyyy/status/2102782294138491019
- @reachvaldo: Zero Data Retention이라 클라이언트 코드에 쓰기 좋다는 호평.
  - 출처: https://x.com/reachvaldo/status/2103420693492977783
- 유튜버들도 "무료니까 어서 써봐, 벤치 유망해" 톤이야. AI Coding Daily는 effort 레벨 따라 다르지만 promising이래.
  - 출처: https://www.youtube.com/watch?v=GSl3QfvN1W4
  - 출처: https://www.youtube.com/watch?v=ECKZe6rMKx0

### 부정 / 까임 / 경고

- @rohanpaul_ai: "@aimlapi 5-scene physics test에서 GLM-5.3이 Space Bunny Alpha 이겼다. 뉴턴 요람 테스트, 토네이도·물방울은 둘 다 못 했다." 비전/피직스 약점 지적이야.
  - 출처: https://x.com/rohanpaul_ai/status/2102918415979823222
- @LuminaBench발 "as bad as the last few were?" — 직전 스텔스 모델들이 구렸으니 이번에도 기대 낮추라는 냉소. 프롬프트블루프린트가 "벤치 없이 의견만 있다"고 정리했어.
  - 출처: https://promptblueprints.tech/news-article/space-bunny-what-the-opencode-report-says
- 일시 오프라인 사태 있었어. "provider is working through an issue" — 프리뷰 인프라 불안정 인증이지.
  - 출처: https://www.youtube.com/watch?v=7B8TFJoDpRU (16:55~17:14 구간 언급)
- 스캠 관련: AI 모델 자체를 스캠이라 까는 X 글은 못 찾았어. 대신 조심할 건 ① 무료 끝나고 가격 폭탄/유료 전환, ② 동명 SBA 밈코인 러그, ③ 프롬프트 로깅(스텔스 약관상 provider가 보관 가능) 이야. OpenRouter도 "prompts may be retained, not used for training"이라 써놨어.
  - 출처: https://openrouter.ai/stealth/space-bunny-alpha
  - 출처: https://huggingface.co/blog/paidaxccc/space-bunny-alpha-ai-model-specs-api-benchmarks-an

---

## 3. Reddit 평가 — 서브레딧별 정리

형, 레딧이 X보다 훨씬 솔직해. 코딩용으로는 호평, 롤플/웹디자인은 호불호, 운영 리스크 지적이 핵심이야.

### r/opencodeCLI — `Another free model in OpenCode: Space Bunny` (123 votes, 35 comments)

- 톤: 기대감. "새 스텔스 떴다, 무료 멀티모달, 써보자"가 대세.
  - 출처: https://www.reddit.com/r/opencodeCLI/comments/1wotanq/another_free_model_in_opencode_space_bunny

### r/opencode — `Space Bunny thoughts?`

- 톤: 탐색전. "써봤냐, 뭘 시켰고 얼마나 고쳤냐" 묻는 스레드. 아직 정량 벤치 없이 체감 공유 중.
  - 출처: https://www.reddit.com/r/opencode/comments/1wocn5s/space_bunny_thoughts

### r/opencode — `New stealth model: Space Bunny`

- "X랑 같은 날 떴다, 일주일 무료" 정보 공유 스레드.
  - 출처: https://www.reddit.com/r/opencode/comments/1wo903y/new_stealth_model_space_bunny

### r/opencode — `M3.1 is SpaceBunny` / `Space bunny is MiniMax M3.1`

- 제일 기술적인 스레드. 토크나이저 델타 비교(Qwen, DeepSeek, GLM, Kimi, Hunyuan 등 중국 팸 돌려서 비교)해서 MiniMax 지목. 댓글에 "opus 5.5가 시작한 일 이어받는데 실수 없이 같은 퀄리티", "hallucination 낮다, 가격만 맞으면 간다" 호평 있어. 반면 "Taco Bell 모델" 드립도 있어.
  - 출처: https://www.reddit.com/r/opencode/comments/1wp4kmi/m31_is_spacebunny
  - 출처: https://www.reddit.com/r/opencode/comments/1wodncp/space_bunny_is_minimax_m31
  - 출처: https://www.reddit.com/r/opencodeCLI/comments/1wpv45g/m31_is_space_bunny_alpha

### r/opencode — `Space Bunny is better than I expected` (6 upvotes, 15 comments)

- "생각보다 solid, intelligence 높다, reasoning Max로 밀어라" 조언.
  - 출처: https://www.reddit.com/r/opencode/comments/1wprfba/space_bunny_is_better_than_i_expected

### r/opencode — `My honest opinion about Space-Bunny`

- "문제 찾는 건 잘하는데, context flaw 때문에 리서치 끝에서 까먹고 안 고친다" — 롱컨텍스트 회상 결함 지적. 1M 숫자는 큰데 실사용 체감이 안 따라간다는 거지.
  - 출처: https://www.reddit.com/r/opencode/comments/1wqi4a8/my_honest_opinion_about_spacebunny

### r/opencode — `Space Bunny Alpha is too verbose, isn't?`

- "너무 장황하고 단순한 일도 오버띵킹한다" 불만 스레드.
  - 출처: https://www.reddit.com/r/opencode/comments/1woi31e/space_bunny_alpha_is_too_verbose_isnt

### r/openrouter — `Space Bunny first impressions: surprisingly good at web design, a bit inconsistent` (126 upvotes, 17 comments)

- 제일 핫한 스레드야. 웹디자인 잘 뽑는데 들쭉날쭉하대. 어떤 댓글은 "웹 UI 디자인은 absolute shit"이라 박살 내기도 해. 온도차 커.
  - 출처: https://www.reddit.com/r/openrouter/comments/1wq3ojp/space_bunny_first_impressions_surprisingly_good

### r/SillyTavernAI — `New Stealth model in Openrouter (Space Bunny Alpha)`

- 롤플 유저들 평: "GLM 5.3 flash랑 비등, 빠르다", "context awareness 제일 낫다", "vanilla RP coherence decent", 근데 "verbose하다, 검열/거절 있다", "중국 모델 아니냐 vs 서양 모델 같다"로 갈려.
  - 출처: https://www.reddit.com/r/SillyTavernAI/comments/1wo8csn/new_stealth_model_in_openrouter_space_bunny_alpha

### r/LocalLLaMA — `MiniMax M3.1 (Space Bunny Alpha) thinks in caveman mode`

- CoT가 토큰 아끼려고 동굴인 모드(짧게 끊어 말함)라는 관찰. 최종 출력엔 지장 없대.
  - 출처: https://www.reddit.com/r/LocalLLaMA/comments/1wp0c0t/minimax_m31_space_bunny_alpha_thinks_in_caveman)

### r/MistralAI — `Is space-bunny-alpha a mistral model?`

- Mistral이냐 묻고, 대만 존재 부정 테스트 돌렸대. Union Alpha랑 비교하며 서양/중국 판별 시도. 결론 없음.
  - 출처: https://www.reddit.com/r/MistralAI/comments/1wodh35/is_spacebunnyalpha_a_mistral_model

### r/AgentsOfAI — `Space Bunny: what would you check before using it...`

- 긴 워크플로우 넣기 전에 작은 태스크로 추종성 검증하라는 신중론.
  - 출처: https://www.reddit.com/r/AgentsOfAI/comments/1wotpu8/space_bunny_what_would_you_check_before_using_it)

### r/opencode — `New Stealth model: Space Bunny` 외 자잘한 핑거프린팅

- "US vs CN origin 핑거프린팅했더니 Western, CN 검열 아님" 주장도 있어. MiniMax설이랑 정면충돌하지. 아직 확정자 없음.
  - 출처: https://www.reddit.com/r/opencode/comments/1wo903y/new_stealth_model_space_bunny

---

## 4. 1차 소스 모음 (형, 확인할 거면 여기만 봐)

- OpenRouter 모델 페이지: https://openrouter.ai/stealth/space-bunny-alpha
- OpenRouter 스텔스 정책: https://openrouter.ai/provider/stealth
- OpenCode 공식 X 공지: https://x.com/opencode/status/2102767716666941864
- OpenCode 모델 비교 데이터: https://opencode.ai/data/compare/minimax/minimax-m3/unknown/space-bunny
- AI/ML API 문서: https://docs.aimlapi.com/api-references/text-models-llm/stealth/space-bunny-alpha
- AI/ML API 모델 페이지: https://aimlapi.com/models/space-bunny-alpha
- Kilo Code 벤치/스펙: https://kilo.ai/models/stealth-space-bunny-alpha (Code #81, Debug #64 표기)
- Pi 모델 정의: https://pi.dev/models/opencode/space-bunny-free
- 토크나이저 확인 X: https://x.com/cheatyyyy/status/2102781392199565683 / https://x.com/cheatyyyy/status/2102782294138491019
- 물리 테스트 패배 X: https://x.com/rohanpaul_ai/status/2102918415979823222
- HF 커뮤니티 정리글(2차지만 스펙/리스크 총정리): https://huggingface.co/blog/paidaxccc/space-bunny-alpha-ai-model-specs-api-benchmarks-an
- SBA 밈코인 예시: https://jup.ag/tokens/DAfkzSx4QRiM5P1kuSxYX3dV58FPy2gzGj55YuJgwinb / https://solanacompass.com/tokens/7eGukyFGJKXRPtHpPH22yjUaB4eegXDvktvxWgADZYVw / https://www.geckoterminal.com/solana/pools/FEC6swG3FWX4oEFkMpqMUKhAr6xLxmD8FZbzFQp179e7

---

## 5. 총평 — 리스크 평가 (형, 투자조언 아냐, 정보 정리야)

형, 이거 투자 관점이 아니라 **"써볼 거냐, 돈 넣을 거냐"** 관점으로 정리해줄게. 이 글은 투자조언 아니야, 그냥 정보 모음이야.

1. **AI 모델로서는 써볼 만해.** 무료, 1M, 멀티모달, 코딩 에이전트 호환. 속도가 빠르다는 평이 X·레딧 양쪽에 있어. 단기 테스트용으론 가성비 끝판이야.
2. **근데 프로덕션에 박기엔 리스크 커.** 주인 미공개, 학습데이터·컷오프 미공개, 프리뷰라 언제 유료·Throttle·내려갈지 몰라. 스텔스 약관상 프롬프트 보관 가능이라 비밀코드·고객정보 넣으면 안 돼.
3. **품질 편차가 커.** 잘 뽑을 땐 opus급 이어받기·웹디자인 호평인데, 못 뽑을 땐 장황·오버띵킹·컨텍스트 까먹기·물리/비전 약체·검열/거절·caveman CoT 지적이 나와. effort 레벨(low→max) 손으로 튜닝해야 해.
4. **정체 리스크:** MiniMax M3.1설이 제일 유력(토크나이저 50/50 일치)인데 미확정이야. 중국계면 나중에 검열·거버넌스·데이터 귀속 이슈 생길 수 있고, 서양설이랑도 충돌해. 컴플라이언스 빡센 곳은 쓰지 마.
5. **코인 쪽은 손대지 마.** $SBA 동명 토큰들은 유동성 몇 달러~수천 달러짜리 짝퉁 무더기야. 공식 컨트랙트·백서·팀 없어. AI 모델이랑 무관해. 잘못 사면 러그 직행이야.
6. **형이 할 거면 이렇게 해:** ① 코인은 쳐다도 보지 마, ② AI는 비밀정보 빼고 테스트만 해, ③ 무료 끝난 뒤 가격 보고 결정해, ④ 중요 워크플로우는 폴백 모델(네가 원래 쓰던 거) 반드시 둬.

다시 말하지만 이건 투자조언 아니고, 형이 판단하라고 모아준 거야. 돈 넣는 얘기면 무조건 공식 컨트랙트·팀·감사부터 확인하고, 없으면 거르는 게 맞아.
