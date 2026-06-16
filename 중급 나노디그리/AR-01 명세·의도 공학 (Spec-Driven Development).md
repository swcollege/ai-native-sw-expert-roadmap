# AR-01 명세·의도 공학 (Spec-Driven Development) — 중급 나노디그리

> 트랙 : **Architect** · 분류 : **트랙 전용** · 난이도 : 중급(L3)
> 학습시간 : 40h (10주 × 4h) · 배지 : *Spec-Driven Architect* · 선수 : 초급 AI 역량 인증 + CC-01·CC-02 권장
> 작성 : 2026-06-15 / SW 공학연구소(SW College) · 근거 : `1차 중간보고_v2.md` + 외부 현황(2026)

## 0. 과정 한 줄 정의
"내가 만들 것"을 **AI가 정확히 구현하도록 정형 명세·의도·제약(할 일/안 할 일)을 작성**하고, 명세→계획→태스크로 분해하는 Spec-Driven Development 역량을 기른다.

## 1. 대상 학습자 & 진입 역량
- **대상** : Architect 트랙 지망(설계·요구로 시프트-레프트하려는 개발자 포함).
- **진입 역량** : CC-01·CC-02, 요구공학·UML 기초.
- **왜 Architect 트랙 전용인가** : 베이스라인 명세는 공통이나, **추적성·구조·ADR로 이어지는 *심화* 명세공학**은 아키텍트 산출물의 핵심(코드→명세로의 이동). 데이터상 "요구를 정교하게 만들수록 다음 단계가 편하다"(플랫폼 아키텍트(E))는 *설계 책임* 영역.

## 2. 교수설계 근거
- **적용 방법론** : Backward Design · Bloom · Gagné · Merrill · CBE.
- **설계 데이터 근거**
  - (내부) "내가 구현할 **WHAT을 정확히 써주면 AI가 해준다 — Back to the Basic**"(요구공학 책임(G)) / "요구사항을 정교하게 만들수록 다음 단계가 편하다는 걸 AI 시대에 더 절감"(플랫폼 아키텍트(E)) / "프롬프트를 **아주 명확·구체적**으로(80%는 '다시 해 와')"(임베디드 리더(C)) / "WHAT + **AI가 할 일/안 할 일/제약**"(요구공학 책임(G)).
  - (외부) Sean Grove **"명세가 새롭게 희소해진 기술, 코드는 가치의 10~20%"** / GitHub **Spec Kit**(Specify→Plan→Tasks→Implement, 2025-09) / AWS Kiro·Cursor / arXiv **Intent** 축.

## 3. Stage 1 — 기대 성취
- **핵심 질문** : 모호한 요구가 어떻게 잘못된 코드를 부르는가? 무엇이 '실행 가능한 명세'인가?
- **전이 목표** : 현업 요구를 **버전관리되는 실행 가능 명세**로 작성, 계획·태스크로 분해해 AI 구현을 견인한다.
- **이해** : ① 명세가 *single source of truth* ② **비목표(non-goals)·제약**이 명세의 절반 ③ 추적성이 검증을 가능케 함.
- **학습목표(Bloom)**
  - LO1 (적용) WHAT/제약/비목표를 **정형 템플릿**으로 명세한다.
  - LO2 (분석) 모호·충돌 요구를 식별·정제한다(CSRS→SRS 류).
  - LO3 (평가) 명세-구현 **추적성(traceability)**을 점검한다.
  - LO4 (창안) **Spec→Plan→Tasks** 분해 파이프라인을 구성한다.

## 4. Stage 2 — 평가 증거 / DoD
- **수행과제** : 현업 기능 1건을 **실행 가능 명세(의도·제약·비목표·수용기준) → 계획 → 태스크**로 작성하고, Spec Kit류 도구로 AI 구현을 견인, 추적성 매트릭스 제출.
- **루브릭** : ① 명세 명확·완전성 ② 제약/비목표 적절성 ③ 추적성 ④ 명세→구현 일치.
- **이수 DoD** : 명세만으로 타인(또는 AI)이 **동일 의도를 재현** + 추적성 100% 매핑.
- **나노디그리 이수 조건** : 수행과제 + 명세 산출물 + 추적성 매트릭스.

## 5. Stage 3 — 학습 계획 (모듈)
- **M1. 의도·명세의 기초** — WHAT vs HOW, 명세가 희소 기술인 이유, 비목표·제약. *(선행조직자)*
- **M2. 정형 명세 작성** — 수용기준, CSRS→SRS 정제, 모호성 제거. *(시연→적용)*
- **M3. Spec-Driven Development** — Specify→Plan→Tasks→Implement, Spec Kit 실습. *(적용)*
- **M4. 추적성 & ADR 연계** — traceability, 의사결정 기록 연결. *(통합 / AR-02 연계)*

## 6. 도구 & 자원
- **도구** : GitHub Spec Kit, Claude Code/Cursor, 요구관리(ALM) 연계.
- **자원** : Sean Grove *The New Code*, Spec Kit 문서, arXiv *Rise of AI-Native SE*(Intent).

## 7. 인증 연계
- **이수 시** : Architect 전문가 인증 도전 **필수(AR-01)** — 자격 = 공통 2(CC-01·02) + AR-01·AR-02.
- **후행** : AR-02 선행 아키텍처.

## 8. 레퍼런스
- (내부) `1차 중간보고_v2.md` §Architect · §5 공통(WHAT 정의력).
- (외부) Sean Grove *The New Code*; GitHub Spec Kit; arXiv *Rise of AI-Native SE*.
