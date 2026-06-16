# AI Native SW Expert Roadmap — 직군 육성체계 설계 (1차안)

> 작성일 : 2026-06-15 / SW 공학연구소(SW College)
> 근거 : `1차 중간보고_v2.md`(현업 인터뷰 8건, 2026-06-09~06-15) + 외부 현황 조사(2026년 1월 이후 기준, §9)
> 한 줄 요약 : **WHAT(전문가 영역·V모델 골격)은 불변, HOW(일하는 방식)는 전환된다.** 3대 전문가(Architect·SDET·Security)는 그대로 두되 *AI 활용 HOW*를 채우고, **Harness/컨텍스트·토큰효율은 별도 직군이 아닌 전원 공통역량**으로 깔며, **검증·DoD·도메인·SW공학 기본기**를 토대로 재설계한다.

---

## 0. 설계 목표와 제약

CTO 코멘트("조금 AI 활용하는 수준의 개선으로는 변화 속도를 못 따라간다 → **전면 재설계**, 현업 체감 효용 필수")를 출발점으로, 본 로드맵은 다음을 동시에 만족하도록 설계한다.

- **(목표)** 초급→중급→전문가→전파에 이르는 **단일 육성·인증 체계**를 정의하고, 각 레벨·트랙에서 *무엇을(역량)*, *어떻게(육성 HOW)*, *어떤 기준으로(인증)* 키울지 명세한다.
- **(제약 1) 글로벌 스탠다드 용어 유지** — 신조어(예: Define Engineer)는 전 인터뷰 공통 거부. Architect / SDET / Security 명칭을 유지하고, *대상자*만 시프트-레프트한다(일반 개발자 → 앞단 역할).
- **(제약 2) 전문가 정의는 보존 + HOW 추가** — "기존 전문가 정의를 바꾸면 안 된다. 백투더베이직(기존 전문성) + AI 활용 역량을 더하는 구조"(보안 책임(B)). 현재안의 약점("역할 뒤에 'AI 자동화' 한 단어만 붙어 추상적")을 *구체적 워크플로우*로 메운다.
- **(제약 3) 교육 시차 한계 인정** — "체계화→전파는 항상 늦다"(PO 리더(A)). 매년 리뉴얼·외부기관 활용을 전제한 **"한 템포 늦게, 빠르게 개척"** 전략을 내장한다.

---

## 1. 핵심 설계 원칙 (6대 원칙 = 내부 인터뷰 × 외부 근거)

| # | 원칙 | 내부 근거(v2 인터뷰) | 외부 근거(2026, §9) |
|---|---|---|---|
| P1 | **WHAT 불변, HOW 변화** — V모델·역할 골격 유지, 수행방식만 '작업자→기준정의자·오케스트레이터·리뷰어'로 전환 | "소프트웨어 공학 틀은 안 바뀜, 바뀐 건 HOW"(PO 리더(A))·"세 영역은 변함없다"(보안 책임(B)) | arXiv *Rise of AI-Native SE*의 3축 **Intent·Collaboration·Verification** / Spec-Driven Development |
| P2 | **Back to the Basic + 실무형** — SW공학·도메인이 결과를 좌우, 희소역량은 '판단력' | "엔지니어링 역량 높을수록 AI도 잘한다"(요구공학 책임(G))·5과목 기본기(임베디드 리더(C)) | Thoughtworks Radar v34 "**fundamentals 회귀로 cognitive debt 대응**" / arXiv "scarce capability = **judgment**" |
| P3 | **검증·DoD가 생존조건** — AI는 "테스트 통과를 위해 수단·방법 안 가림". 비판적 검증을 전 레벨 필수 탑재 | "DoD 정의가 SDET의 시작, 리뷰가 제일 중요"(PO 리더(A)) | Spec Kit(Specify→Plan→Tasks→Implement) / AI fluency 베이스라인 4질문 中 "verify what AI produces" |
| P4 | **Harness = 공통역량 + 도메인결합 전문기능 + 거버넌스 조직 (독립 직군 ✕)** | "무슨 전문성? 개발자가 다 한다. AI역량은 본연의 역량"(보안 책임(B))·"개인화기"(로봇제어 책임(I)) | Fowler/Böckeler "**practice requiring deliberate design, not a specialist role**" / Nestr "harness ↔ **organizational governance**" |
| P5 | **토큰·컨텍스트 효율 = 새 기본기** — 추론 최소화·커맨드化가 비용 생존선 | "하네스 구축하면 하루 만에 토큰 소진"(임베디드 리더(C))·"자연어·추론 과다가 토큰을 가장 많이 먹는다 → 커맨드化"(보안 책임(B)) | FinOps-for-AI "**Inference Bill Shock**", *cost-per-token*·*cost-per-successful-interaction* (FinOps X 2026) |
| P6 | **본부 규모별 차등 + 주니어 사다리 재설계** | 요구공학 전담조직 분리 시도 **실패**(소규모 본부)·"인턴 안 뽑는 모순"(거버넌스 책임(D)) | SSRN *Broken Ladder*(GenAI 도입 후 6분기 내 주니어 고용 −9~10%) / WEF Future of Jobs 2026 |

---

## 2. 육성체계 매트릭스 (Core)

`이미지 틀(레벨 × 트랙 + 인증 컬럼)`을 충실히 따르되, v2 결론으로 채운다. **세로축 = 레벨**(초급→중급→전문가→전파), **가로축 = 3대 전문 트랙**(Architect·SDET·Security), 그리고 **트랙을 관통하는 공통역량 밴드**와 **전 레벨을 떠받치는 SW공학 토대바**로 구성한다.

| 레벨 | 인증 | **Architect** | **SDET** | **Security** |
|---|---|---|---|---|
| **전파**<br>*(전문가 이후)* | 전문가 인증 후 | ◀── 컨퍼런스 참가·발표 지원 + **전파 교육(사내 전파 채널)** + **리텐션**(조직에 하네스를 지속 구축·배포하는 과제) — 전 트랙 공통 ──▶ |||
| **전문가**<br>**(Expert · L4)**<br>*조직 단위* | **전문가**<br>(조직 단위 인증) | 현업과제 수행(**하네스**)<br>+ 팀 배포 + 인증심사 | 현업과제 수행(**하네스**)<br>+ 팀 배포 + 인증심사 | 현업과제 수행(**하네스**)<br>+ 팀 배포 + 인증심사 |
| **중급**<br>**(Intermediate · L3)**<br>*개인 단위* | **AX 인증**(개인)<br>≈ Function Architect | 전 모듈 이슈<br>+ 교육내 실습과제 | 전 모듈 이슈<br>+ 교육내 실습과제 | 전 모듈 이슈<br>+ 교육내 실습과제 |
| ▸ **공통역량 밴드**<br>*(중급, 3트랙 관통)* | | ◀── **하네스·컨텍스트 엔지니어링 · 토큰효율(커맨드化) · PM형 오케스트레이션 · E2E 워크플로우 연결** = *신규 세미나 + 실습과제* ──▶ |||
| **초급**<br>**(Foundation)** | **AI 역량 인증**<br>(검증 문제 + 커맨드/시킬 수 있는 문제) | ◀── **AI Native SW Bootcamp** : 코어 + 기초 모듈 (전 트랙 공통) ──▶ |||
| **토대**<br>*(전 레벨 관통)* | | ◀── **SW공학** · 도메인 · 보안 기초(Secure-by-default) · 네트워크/OS/플랫폼(도커) ──▶ |||

**우측 주석 — 거버넌스/운영 조직 (인증 직군 아님):** 토큰·예산 배분, 스킬·기능 **중복 제거**, 사용법 **교육·전파(Enablement)**를 담당. **과도기적**(시스템 성숙 시 축소)이며 **본부 규모별 차등** 적용(§8).

### 이미지 대비 변경점 (왜 이렇게 바꿨나)

- **PM 컬럼 → 공통역량으로 흡수.** "PM형 역량(에이전트 조율 + 산출물 판단)"은 특정 전문가가 아니라 *전 개발자*의 일하는 방식이다(거버넌스 책임(D) "개발자=에이전트 조율자+산출물 판단자"). 외부에서도 "AI 엔지니어링은 *역할이자 동시에 모든 개발자의 베이스라인 스킬*"로 수렴.
- **Harness 컬럼 → 공통역량 밴드 + 전문가 셀의 '현업과제(하네스)'로 이원화.** *기본기로서의 하네스*는 전원 공통(중급 밴드), *시스템 설계로서의 하네스*는 각 도메인 전문가가 현업과제로 수행(전문가 셀). 별도 '하네스 전문가 컬럼'은 두지 않는다(P4).
- **전문가 레벨에는 Arch/SDET/Security 3트랙만.** "전문 하네스는 독립적이지 않고 도메인 위에 얹힌다"(보안 거버넌스 리더(F)·보안 책임(B)) → 하네스는 트랙이 아니라 *각 전문가가 수행하는 과제의 형식*.

---

## 3. 레벨별 상세

### 3-1. 초급 (Foundation) — "AI Native SW Bootcamp"

- **대상 / 목적** : 전 개발자(신입 포함). AI Native 시대의 *공통 기본기*를 '깔리는' 실무형으로 체득.
- **구성(코어 + 기초 모듈)** :
  1. **SW공학 5과목 토대** — SW공학·디자인패턴·네트워크·OS(플랫폼)·보안 기초(임베디드 리더(C) 5과목).
  2. **WHAT 정의력(명세/요구)** — "내가 만들 것"을 정형적으로 + AI가 *할 일/안 할 일/제약*까지 명시(요구공학 책임(G)). → Spec-Driven 사고.
  3. **AI 협업·하네스 기본기** — 컨텍스트 관리, **토큰효율(추론 최소화·커맨드化)**, 스킬(.md), 자기 환경 테일러링, **피드백 루프** 구성.
  4. **검증·DoD 사고 입문** — 패스/페일·종료조건 상상, AI 산출물 비판검증.
  5. **플랫폼 기초** — 도커 등 컨테이너, 에이전트 간 네트워크 통신 개념("앱이 한 컨텍스트에 담길 크기로 규격화"·ES 임베디드 리더(C)).
- **인증 = AI 역량 인증** : *코딩 가능 여부*가 아니라 **① 검증 문제(AI 산출물의 결함·할루시네이션·부정행위 적발)** + **② 커맨드/시킬 수 있는 문제(명세·오케스트레이션·토큰효율)**로 평가(PO 리더(A) "역량인증을 토큰·공학적 사고 평가로 개편").
- **주니어 사다리 장치** : AI 의존으로 인한 '체득 공동화'를 막기 위해, 부트캠프 내 **'피로 쓴 규칙'을 직접 겪는 구간**(AI 보조 제한 + 손코딩 + 코드 추적·구술 평가)을 의도적으로 배치(로봇제어 책임(I)·로봇제어 책임(H) / arXiv Phase 1 "restrict AI on core skill-building").
- **외부 정합** : arXiv 4단계 커리큘럼 Phase 1~2, AWS AI&ML Scholars의 'Challenge → Nanodegree' 진입 구조, Andela AI Academy의 GitHub Copilot 기반 공통 트랙.

### 3-2. 중급 (Intermediate · L3) — 역할별 심화 + 공통 워크플로우

- **목적** : 초급 공통기 위에 ① 역할별(트랙) 심화와 ② 트랙을 관통하는 **공통역량 밴드**(하네스/컨텍스트·토큰효율·PM형 오케스트레이션·E2E 연결)를 얹는다.
- **트랙 모듈(Arch/SDET/Security 공통 형식)** : *전 모듈 이슈 + 교육내 실습과제*. 단, 콘텐츠는 **AI 아웃풋 기준으로 업데이트**(역할은 그대로, 평가 기준이 'AI를 써서 어떻게 잘하느냐'로 이동).
- **공통역량 밴드(신규 세미나 + 실습과제)** : "다 개별로 흩어져 있는"(PO 리더(A)) 워크플로우를 *직접 연결*해 보는 실습. Guides(피드포워드: AGENTS.md·제약문서)·Sensors(피드백: 테스트·평가 루프) 구성, 토큰 예산 안에서 커맨드化, 멀티에이전트 역할 분해.
- **인증 = AX 인증(개인 · Level 3)** : "*내 일을 자동화*"(예: 반복 작업을 자동화하는 에이전트 개발). 이미지의 **Function Architect / PM역량인증**이 이 층에 대응. **AX 인증과 AI 역량 인증은 중복 영역 → 동시 취득** 협의(식스시그마 인증 운영과 유사·VS 보안 책임(B)).
- **외부 정합** : arXiv Phase 3(human–AI teams·agent orchestration), Google '5-Day AI Agents Intensive'(models·tools·orchestration·memory·evaluation), 컨텍스트 엔지니어링 교육 과정의 확산.

### 3-3. 전문가 (Expert · L4) — 조직 단위 현업과제

- **목적** : "조직 차원의 변화·발제"(보안 책임(B)). 개인 자동화(L3)를 넘어 **조직에 하네스를 구축·배포**하고 그 효용을 입증.
- **수행(전 트랙 공통 형식)** : **현업과제 수행(하네스) + 팀 배포 + 인증심사**. 각 전문가가 *자기 도메인 위에* 하네스(E2E 오케스트레이션·게이팅 자동화·도메인 특화 에이전트)를 구축하고 팀에 배포·전파한다.
- **"도메인 × 하네스" 결합** : 하네스는 독립 과제가 아니라 Architect(설계 일치율·아키 적합성 fitness function), SDET(게이팅·CT 피드백 루프), Security(위협모델링·자동 패치 가드레일) **각 도메인에 얹혀** 수행된다(Fowler: 하네스 ↔ 아키텍처/테스트/플랫폼 연결).
- **인증 = 전문가(조직 단위)** : 리텐션형 — 1회성 수료가 아니라 *조직에 효용을 배포·심사*받는 형태. "아키텍트 인증 수료자 다수가 실제 역할을 안 한다"(플랫폼 아키텍트(E)·임베디드 리더(C))는 문제를 막기 위해 **'정말 필요한 사람'에게 제도가 가도록 선발·활용을 연계**.
- **외부 정합** : arXiv Phase 4(repository-scale agentic projects + public defense with contribution evidence), Microsoft 'AI Agent Builder Associate'급 *프로덕션 에이전트 구축* 인증.

### 3-4. 전파 (전문가 이후) — 확산과 리텐션

- **컨퍼런스 참가·발표 지원** + **전파 교육(사내 전파 채널)** : 전문가의 지식을 사내로 환류.
- **리텐션** : 전문가는 *조직에 하네스를 지속 구축·배포하는 과제*를 계속 수행·심사받는다(인증의 유지·갱신).

---

## 4. 트랙별 상세 — AS-IS → TO-BE → 역량 → 육성(HOW)

> 각 트랙은 **"기존 전문성(불변) + AI 활용 HOW(신규)"** 구조. AS-IS는 v2 인터뷰 원문, TO-BE는 외부 리더 + 2026 현황.

### 4-1. Architect — "코드 작성자"에서 "의도·구조의 정의자"로

- **AI Native 역할** : ① 선행 설계자(바이브코딩 스파게티화 방지) ② 제약·컨텍스트 주입자 ③ 옵션 판단·게이트키퍼(무엇을 더하고 뺄지) ④ 에이전트 오케스트레이션 설계자.
- **AS-IS(v2)** : "선행 설계가 돼야 하고 그건 아키텍처가 해줘야"(거버넌스 책임(D))·"설계 합의는 사람, ADR↔Code 일치율은 AI로 점수화"(플랫폼 아키텍트(E))·"기존 아키텍트가 AI를 제일 잘 쓴다 — 구조적으로 쓰니까(스트럭처 이해=컨텍스트 강점)"(임베디드 리더(C)). *한계*: "구조가 다른 신규 프로젝트엔 에이전트 재사용 불가 → 챗 모드 회귀"(보안 책임(B)).
- **TO-BE(외부)** : Karpathy "아이언맨 로봇이 아니라 **슈트**(부분 자율·자율성 슬라이더)"·Sean Grove "코드는 가치의 10~20%, 나머지는 **명세**". 2026 현황: **Spec-Driven Development**(GitHub Spec Kit·AWS Kiro·Cursor)가 아키텍트의 산출물을 *코드→명세·계획·ADR*로 이동시킴.
- **역량** : 정형 명세·아키텍처·시스템 분해, 제약 표현력, 옵션 판단력, (전문가) 아키텍처 적합성 하네스(fitness function).
- **육성(HOW)** : SW공학 기본기 재강화 + **경험·맥락은 현업 과제로**("육성한다는 개념을 버려야"·플랫폼 아키텍트(E)) + **시프트-레프트**(구현 특화 개발자를 앞단으로).

### 4-2. SDET — "테스트 수행자"에서 "기준 정의자·최종 게이트키퍼"로

- **AI Native 역할** : ① DoD/Exit Criteria 정의자 ② AI 산출물 검증·리뷰어(누락·할루시네이션·부정행위 적발) ③ 테스트 설계자(전략·하네스·피드백 루프) ④ 게이팅 자동화 에이전트 설계자.
- **AS-IS(v2)** : "DoD 정의가 SDET의 시작, 리뷰가 제일 중요"(PO 리더(A))·"비용 때문에 못 하던 V모델·뮤테이션 테스트를 1인이 수분 내"(로봇제어 책임(H))·"검증의 핵심은 **CICD/CT 자동화와 피드백 루프**, 제품·피처 레벨 CT가 중요"(임베디드 리더(C)).
- **TO-BE(외부)** : Kent Beck "지니가 **테스트를 비활성화·삭제하면 부정행위 신호** … 코드·복잡도·테스트·커버리지를 챙겨라"·Karpathy "생성–검증 루프를 매우 빠르게". 2026 현황: QA→SDET가 "**결함 적발에서 결함 예방(quality engineering at scale)**"으로, **Agentic Testing**(의도 기반, Selenium/Playwright 위에 얹힘)으로 진화. "**자동화를 만드는 사람은 자동화할 수 없다**"(SDET 직무 안정성).
- **역량** : 테스트 디자인(어떤 기준으로), 테스트 하네스·CT 파이프라인·피드백 루프, 게이팅 자동화 에이전트, 표준(ISO 29119) 기반 실무.
- **육성(HOW)** : DoD/게이팅 사고를 *전 개발자 기본 탑재*(PO 리더(A)) + SDET 전문가는 그 문화·프로세스 리딩 + "정신적으로 남아 있어야"(품질을 볼 수 있는 사람이 사라지지 않게).

### 4-3. Security — "사후 점검자"에서 "AI 시대 공방(攻防) 운영자"로

- **AI Native 역할** : ① Security-for-AI 설계자(인젝션·RAG 포이즈닝·적대적 공격 위협모델링·SDL) ② AI-for-Security 운영자(자동 탐지·패치·리그레션) ③ 개발자 보안 역량 전파자(시큐어 코딩·가드레일·ML-BOM).
- **AS-IS(v2)** : "AI 기능 없는 자사 제품은 없다 → **Security-for-AI 디폴트**"·"창과 방패"·"개발자 수준으로 내려와야"·"표준이 기술을 못 따라옴 → **개발자 보안 과정이 전문가 과정보다 우선**"(보안 거버넌스 리더(F))·"Security·SDET는 **개발 전 과정에 걸쳐** 있다 → 게이팅이 워크플로우 전반에 내장"(보안 책임(B)).
- **TO-BE(외부)** : Simon Willison "**치명적 3요소**(프라이빗 데이터 + 비신뢰 콘텐츠 + 외부 통신)"·Google **Big Sleep**/**XBOW**(자율 에이전트가 HackerOne 1위). 2026 현황: **OWASP Top 10 for LLM Apps** + **OWASP Agentic Apps Top 10**, **MITRE ATLAS**, **AI용 STRIDE 위협모델링**, *개발자 주도 위협모델링*.
- **역량** : AI 공격표면·위협모델링, 시큐어 코딩, 가드레일·SBOM/ML-BOM, (전문가) 보안 특화 하네스.
- **육성(HOW)** : **보안을 공통 필수로**(전 과정에 CQT 기본 탑재·보안 거버넌스 리더(F)) + **개발자 과정 먼저, 전문가 과정은 단계적**(표준 미정립) + "원래 일이 보안이어야 하고 하네스는 배워서 습득"(보안 거버넌스 리더(F)) = **'도메인 × 하네스' 결합형**.

---

## 5. 공통 필수 역량 층 (전 개발자 베이스라인)

> 특정 전문가가 아니라 **AI Native 시대 전 개발자**가 갖춰야 하는 역량. 이미지의 PM/Harness가 흡수된 층.

| 역량 | 수준 | 정의/HOW | 근거 |
|---|---|---|---|
| **SW Engineering 기본기** | 필수(전원) | 설계·요구공학·테스트·구조화 등 불변의 원칙 | "엔지니어링 역량 높을수록 AI도 잘한다"(요구공학 책임(G)) / Thoughtworks Radar v34 |
| **도메인 지식** | 필수(전원) | 실현 가능한 사양·제약의 원천. 경험·체득으로만 | "도메인을 AI가 모름"(요구공학 책임(G)) / "제품 정의는 도메인 전문가"(임베디드 리더(C)) |
| **WHAT 정의력(명세)** | 필수(전원) | 정형 명세 + AI 할 일/안 할 일/제약 | "Back to the Basic"(요구공학 책임(G)) / Spec-Driven Development |
| **검증·DoD 사고** | 필수(전원) | 패스/페일·종료조건, 비판적 검증 | "DoD는 SDET의 시작"(PO 리더(A)) / arXiv Verification 축 |
| **AI 협업·하네스 기본기 (토큰/컨텍스트 효율)** | 초·중급(전원) | 컨텍스트·**토큰효율(커맨드化)**, 스킬(.md), 피드백 루프, 에이전트 조율(PM형) | "하루 만에 토큰 소진"(임베디드 리더(C))·"커맨드化로 추론↓"(보안 책임(B)) / FinOps-for-AI |
| **PM형 오케스트레이션** | 중급(전원) | 에이전트에 일 시키고 산출물 판단·최종 책임 | "개발자=조율자+판단자"(거버넌스 책임(D)) / "AI engineering = role *and* baseline skill" |
| **보안 (Secure-by-default)** | 필수(전원) | 시큐어 코딩·기본 위협 인식 | "전 과정에 CQT 기본"(보안 거버넌스 리더(F)) / OWASP LLM·Agentic Top 10 |
| **플랫폼·네트워크·OS 기초** | 중급(전원) | 에이전트 통신·실행환경, 컨테이너(도커) | "에이전트는 네트워크로 통신"(임베디드 리더(C)) / Platform Engineering shift-down |
| **업무범위 확장(T자형)** | 중급(전원) | 인접 영역 커버리지 확장 | "임베디드 개발자가 웹도 AI로"(임베디드 리더(C)) |
| **추상화·시프트레프트** | 중·고급 | 구현 디테일→의도·구조로 추상화 레벨 상승 | "코딩 고수도 추상화 레벨을 올려야"(요구공학 책임(G)) / arXiv "engineer moves upward in abstraction" |

**공통 육성 원칙(HOW)** : ① Back to Basic + 실무형('깔리는' 교육) ② 경험은 강의가 아니라 **현업 과제·풀사이클 1인 프로젝트(원플싹)**로 ③ 단편 학습이 아니라 **'연결'을 직접 설계**(플랫폼·OS 위에서 관심사 분리) ④ **주니어 체득 경로** 별도 설계 ⑤ **빠른 캐치업**(외부 전문기관·선진사 활용, 매년 리뉴얼).

### 5-1. 역량 ↔ arXiv 9역량 매핑 (학술 정합성)

arXiv *Rise of AI-Native SE*(2026-06)의 9역량(C1~C9)을 본 체계에 매핑해 누락을 검증:

- C1 명세·의도공학 → **WHAT 정의력** · C2 AI 산출물 비판평가 / C3 AI 보조 디버깅·검증 → **검증·DoD** · C5 에이전트 오케스트레이션·툴 사용 → **AI 협업·PM형** · C6 CS·시스템 사고 → **SW공학·플랫폼 기초** · C7 보안·윤리·책임 → **보안** · C8 Human–AI 협업·소통 → **PM형 오케스트레이션** · C4 메타인지 / C9 지속학습 → **전 레벨 관통(전파·리텐션)**.

---

## 6. 인증 체계 (3단 + 층위 분리)

```
[초급] AI 역량 인증            검증 문제 + 커맨드/시킬 수 있는 문제
   │                          (코딩 가능 여부 ✕ → 토큰·공학적 사고 ○)
   ▼
[중급] AX 인증 (개인 · L3)      "내 일을 자동화"  ≈ Function Architect / PM역량인증
   │                          ※ AI 역량 인증과 중복 → 동시 취득 (식스시그마 유사)
   ▼
[전문가] 전문가 (조직 · L4)     조직에 하네스 구축·배포·심사 (리텐션형)
   │                          "정말 필요한 사람"에게 가도록 선발·활용 연계
   ▼
[전파] 컨퍼런스·사내 전파 채널 전파 + 지속 하네스 과제
```

- **층위 분리(핵심)** : **AX(개인·L3)** = 내 일 자동화 / **전문가(조직·L4)** = 조직 차원 변화. 둘의 차이는 *"개인 단위냐 조직 단위냐"*(보안 책임(B)).
- **중복 정리** : AX 인증과 AI 역량 인증은 영역이 겹치므로 **동시 취득** 협의.
- **외부 정합** : 산업 인증은 *기반(AWS AI Practitioner)→실무(DataCamp AI Engineer for Developers)→프로덕션 에이전트(Microsoft AI Agent Builder Associate)*로 단계화되는 추세와 일치(※ Azure AI-102는 2026-06-30 은퇴 → 에이전트 중심으로 재편).

---

## 7. Harness 논점 — SW College 최종 판단

**결론 : "공통 역량(개인화기) + 도메인결합 전문기능(시스템 설계) + 거버넌스/운영 조직 — 단, 셋 다 '독립 전문가 직군'은 아니다."**

1. **공통 역량 층(개인화기)** : 컨텍스트 관리·**토큰효율(커맨드化·추론 최소화)**·스킬(.md)·피드백 루프는 **모든 개발자의 기본기**. → 중급 공통역량 밴드. *(보안 거버넌스 리더(F)·로봇제어 책임(I)·PO 리더(A)·임베디드 리더(C)·보안 책임(B) 공통 / Fowler "practice, not a role")*
2. **전문 기능 층(시스템 설계)** : E2E 멀티에이전트 오케스트레이션·게이팅 자동화·IDP는 전담 전문성을 요하나 **독립 직군이 아니라 Architect/SDET/Security 도메인 위에 얹히는 능력**. → 전문가 셀의 '현업과제(하네스)'. *(거버넌스 책임(D)·PO 리더(A) / Fowler: 하네스 ↔ 아키텍처·테스트·플랫폼)*
3. **거버넌스/운영 조직 ≠ 전문가 직군** : 토큰·예산 배분, 스킬·기능 중복 제거, 사용법 교육·전파를 담당하는 **운영 조직은 필요**하되 *인증 대상 직군이 아니며 과도기적*(성숙 시 축소). *(보안 책임(B) 사내 AI 거버넌스 조직 사례 / Nestr "harness ↔ governance" / FinOps-for-AI)*
4. **재사용성 한계 인정** : 에이전트/하네스는 *제품 구조가 다르면 재사용 안 됨*(임베디드 리더(C)·보안 책임(B)) → "도메인 × 하네스" 결합형으로 육성, **별도 독립 직군화는 보류**.
5. **층위 분리** : 하네스 역량은 AX(개인·L3)로 전원 습득, 전문가는 조직 단위(L4)로 구축·배포·심사.

---

## 8. 조직·운영 전략 (본부 규모별 차등)

- **(교훈) "역할을 떼어 전담조직화"는 소규모 본부에서 실패한다.** ES의 요구공학 전담조직 분리 시도은 "아키텍트 대부분이 이미 팀장"이라 작동 불가 → 철저히 실패(임베디드 리더(C)). 신규 역할(특히 Harness)을 별도 직군/조직으로 떼어내려는 설계에 대한 직접 경고.
- **대규모·B2B 본부** : 본부별 거버넌스·플랫폼(IDP) 전담 조직으로 추진. *(Gartner: 2026년 SW조직 80%가 플랫폼팀/IDP 보유, golden path로 shift-down)*
- **소규모·연구 본부** : 강제 조직화 대신 **인프라 개방 + 관심 인재 모티베이션 + 공학연(SW College)·외부 기관 지원**. "소규모 본부엔 그런 조직이 없다(타 본부 의존) → **공학연이 해줘야**"(임베디드 리더(C)).
- **산출물 다이어트** : AI워싱 검증·국가별 규제 문서로 산출물이 *오히려 증가* → 개인 생산성↑이 전체 생산성으로 안 이어짐. **무엇을 없앨지**를 거버넌스 과제로.

---

## 9. 외부 레퍼런스 — 2026년 현황 (insane-search/WebSearch 기반, 2026-01 이후)

> 본 로드맵의 각 설계 결정이 외부 현황과 정합함을 입증하는 근거. 모두 2026년 기준(일부 2025년 토대 자료 포함).

### A. 빅테크/SW 회사의 실제 교육 체계 (레벨·트랙·인증)
- **Andela AI Academy** — 2026년까지 기술자 15,000명 양성 목표, GitHub Copilot 교육에서 출발해 다중 트랙으로 확장. [PR Newswire](https://www.prnewswire.com/news-releases/andela-scales-ai-academy-to-support-enterprise-upskilling-and-ai-fluent-talent-pipelines-302683367.html)
- **AWS AI & ML Scholars 2026** — Challenge(3/24~6/24) → 상위 4,500명 Udacity Nanodegree, 트랙 = *AI Programmer / Agentic AI Business Pro / Agent Developer*. [AWS Training Blog](https://aws.amazon.com/blogs/training-and-certification/aws-ai-ml-scholars-is-open-for-2026-get-started-on-your-ai-learning-journey/)
- **Microsoft Certified: AI Agent Builder Associate** — 프로덕션 Copilot Studio·멀티에이전트, 시험 AB-620(2026-06 라이브). [Microsoft Skills Hub](https://techcommunity.microsoft.com/blog/skills-hub-blog/the-ai-job-boom-continues-build-the-skills-that-move-business-forward/4494139) · [AI Engineer Path](https://learn.microsoft.com/en-us/training/career-paths/ai-engineer)
- **JPMorgan** — 65,000 엔지니어의 **AI 툴 사용을 인사평가에 연동**. [Let's Data Science](https://letsdatascience.com/blog/jpmorgan-tracks-65000-engineers-ai-usage-performance-reviews)
- **AI fluency = 2026 베이스라인** — 채용 기준 4질문(문제를 스스로 찾기 / 비즈 맥락 연결 / AI로 솔루션 지시 / **산출물 검증**). [WindowsForum(Udemy 2026 Trends)](https://windowsforum.com/threads/ai-fluency-becomes-baseline-in-enterprise-learning-udemy-2026-trends.382533/) · [FutureCIO](https://futurecio.tech/ai-fluency-will-become-baseline-skill-but-employees-shouldnt-treat-it-as-tool/)
- **Gartner / IDC** — 2027년까지 SW 엔지니어 80%가 AI-assisted 개발 툴 업스킬 필요 / 2026년 기업 90%가 AI 스킬 부족.

### B. AI Native 개발 역량·역할·인증 트렌드
- **arXiv — *The Rise of AI-Native Software Engineering*** (2026-06) — 3축 **Intent·Collaboration·Verification** + 9역량(Bloom 매핑) + **4단계 커리큘럼**. "engineer moves **upward in abstraction**"·"scarce capability = **judgment**". [abs](https://arxiv.org/abs/2606.12986) · [html](https://arxiv.org/html/2606.12986)
- **Thoughtworks Technology Radar Vol. 34** (2026-04-15) — AI 복잡도 → "**fundamentals 회귀로 cognitive debt 대응**", zero-trust·DORA·testability 부상, agent coding swarm은 신중. [Thoughtworks](https://www.thoughtworks.com/about-us/news/2026/combat-ai-cognitive-debt-radar-v34)
- **Spec-Driven Development** — 실행 가능한 *버전관리 명세가 single source of truth*. GitHub **Spec Kit**(2025-09 오픈소스, Specify→Plan→Tasks→Implement), AWS Kiro·Cursor·Claude Code 등 확산. [Microsoft Dev Blog](https://developer.microsoft.com/blog/spec-driven-development-spec-kit) · [SDD 2026 Guide](https://thebcms.com/blog/spec-driven-development)
- **SDET/QA 진화** — "결함 적발→예방(quality engineering at scale)", **Agentic Testing**(의도 기반, Selenium/Playwright 위), WQR 2025: 기업 58%가 QA AI 업스킬. [QA→SDET 2026](https://quashbugs.com/blog/qa-to-sdet-ai-2026) · [Agentic Testing](https://aitestingguide.com/agentic-testing/)
- **"AI 엔지니어링 = 역할이자 동시에 모든 개발자의 베이스라인 스킬"** (역할 vs 공통 논쟁의 외부 수렴). [NetCom](https://www.netcomlearning.com/blog/how-to-become-an-ai-engineer)
- **AI 인증 단계화** — 기반(AWS AI Practitioner)→실무(DataCamp AI Engineer for Developers)→에이전트(Agent Builder). [DataCamp](https://www.datacamp.com/blog/top-ai-certifications) · [Azure AI-102(2026-06-30 은퇴)](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-engineer/)

### C. 하네스/컨텍스트 엔지니어링 · 플랫폼 · 토큰 효율
- **Harness Engineering (Fowler/Böckeler, Thoughtworks)** — **Agent = Model + Harness**, **Guides(피드포워드) + Sensors(피드백)** 사이버네틱 거버너. "**a practice requiring deliberate design, not a specialist role**", 아키텍처(fitness function)·테스트(sensor)·플랫폼(template)과 연결. [Fowler](https://martinfowler.com/articles/harness-engineering.html) · [Thoughtworks Podcast](https://www.thoughtworks.com/en-es/insights/podcasts/technology-podcasts/what-harness-engineering) · [Nestr "↔ governance"](https://nestr.io/blog/harness-engineering-ai-agents)
- **프롬프트→컨텍스트→하네스 3시대** — 공학적 엄밀함은 사라진 게 아니라 *이동*. [Medium "Three Eras"](https://mohamed-hendawy.medium.com/from-prompts-to-harnesses-the-three-eras-of-ai-agent-engineering-fbd0e6168b21) · [Atlan 2026 Guide](https://atlan.com/know/what-is-harness-engineering/)
- **Context Engineering** — Karpathy "2026 핵심 코딩 스킬". 교육: Google '5-Day AI Agents Intensive'(models·tools·orchestration·memory·evaluation). [Fowler: Context Eng for Coding Agents](https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html) · [Google 5-Day](https://www.kaggle.com/learn-guide/5-day-agents) · [DataCamp](https://www.datacamp.com/blog/context-engineering)
- **Platform Engineering / IDP "shift-down"** — Gartner 2026년 SW조직 80% 플랫폼팀(2025년 55%), golden path(CLI 한 번에 repo+CI/CD+관측+가드레일), 73% 플랫폼팀이 AI 어시스턴트 통합. [WebProNews](https://www.webpronews.com/platform-engineerings-2026-reckoning-shift-down-ai-fusion-and-the-80-mandate/) · [State of Platform Eng Vol4](https://platformengineering.org/blog/announcing-the-state-of-platform-engineering-vol-4)
- **FinOps for AI (토큰 효율)** — "**Inference Bill Shock**", 토큰은 대시보드에 안 보이는 비용 단위, 골든 메트릭 = *cost-per-token·cost-per-successful-interaction*. [FinOps Foundation](https://www.finops.org/wg/finops-for-ai-overview/) · [Optimizing GenAI](https://www.finops.org/wg/optimizing-genai-usage/) · [FinOps X 2026 "Token Panic"](https://www.nops.io/blog/finops-x-2026-day-1-keynote/)

### D. 보안 (Security-for-AI)
- **OWASP Top 10 for LLM Apps / Agentic Apps (2026)**, **MITRE ATLAS**, AI용 STRIDE. [OWASP LLM Top10 2026](https://elevateconsult.com/insights/owasp-llm-top-10-security-vulnerabilities-every-ai-developer-must-know-in-2026/) · [OWASP Agentic](https://www.practical-devsecops.com/owasp-top-10-agentic-applications/) · [AI Security Engineer Roadmap](https://www.practical-devsecops.com/ai-security-engineer-roadmap/) · [개발자 주도 위협모델링](https://securityboulevard.com/2026/03/threat-modeling-with-ai-a-developer-driven-boon-for-enterprise-security/)

### E. 주니어 사다리 (Broken Ladder)
- **SSRN — *The Broken Ladder*** (Lambert & Schindler) — GenAI 도입 후 6분기 내 주니어 고용 −9~10%, "paid learning curve" 종료. [SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6787638) · [ThinkPol](https://thinkpol.ca/2026/03/24/the-junior-developer-pipeline-is-broken-and-nobody-has-a-plan-to-fix-it/)
- **WEF Future of Jobs 2026** — "Software developers are the **vanguard** of how AI is redefining work", 주니어 핵심 업무 70%+ 자동화 가능, 신규 진입 = day1부터 *orchestrate·verify·leverage*. [WEF](https://www.weforum.org/stories/2026/01/software-developers-ai-work/)

### F. 보고서가 인용한 외부 토대 (v2 §부록)
- Karpathy "Software Is Changing (Again)"(YC 2025) · Sean Grove "The New Code"(2025) · Kent Beck "Augmented Coding"(2025) · Simon Willison "Lethal Trifecta"(2025) · Google Big Sleep·XBOW HackerOne 1위(2025~26) · Anthropic "Harness design for long-running apps"·"Effective Context Engineering"(2026) · "Evolution of AI Agentic Patterns: Prompt→Context→Harness"(2026).

---

### 부록 — 설계↔근거 추적표 (요약)

| 설계 요소 | 내부(v2) | 외부(2026) |
|---|---|---|
| 매트릭스 레벨 4단(초급→중급→전문가→전파) | 인증 3단+층위 분리(보안 책임(B)) | arXiv 4단계 커리큘럼 / AWS·Andela 트랙 구조 |
| 3트랙 유지(Arch/SDET/Security) | "세 영역 불변"(보안 책임(B)·PO 리더(A)) | Thoughtworks fundamentals 회귀 |
| Harness=공통+도메인결합(직군 ✕) | "개인화기"(로봇제어 책임(I))·"개발자가 다 함"(보안 책임(B)) | Fowler "practice not a role" / Nestr governance |
| 토큰효율 공통기본기 | "하루 만에 소진"(임베디드 리더(C))·"커맨드化"(보안 책임(B)) | FinOps-for-AI / token panic |
| 검증·DoD 전원 필수 | "DoD는 SDET의 시작"(PO 리더(A)) | Spec Kit / AI fluency 검증 |
| 본부 규모별 차등 | RM 실패(임베디드 리더(C)) | Gartner IDP 80% (대규모 적합) |
| 주니어 체득 경로 | "빡세게 체득"(로봇제어 책임(I)·로봇제어 책임(H)) | SSRN/WEF Broken Ladder |
