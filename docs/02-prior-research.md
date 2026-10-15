# 사전 조사: "인간이 이해하기 좋은 LLM 답변"을 얻기 위한 요청 방식

> 작성일: 2026-10-15 · 조사 방법: 웹 리서치 에이전트가 2023–2026년 논문·프리프린트·공식 가이드 검토
> 본 문서는 각 연구의 주장과 이 문서의 해석을 구분해 서술한다.

## 핵심 결론 (결론부터)

**"그냥 쉽게 써줘"보다, 답변의 종류와 상세 수준을 명시적으로 지정하는 것이 가장 탄탄한 근거를 가진 방식이다.**

지원 강도별 정리:

| 요청 방식 | 근거 강도 | 요약 |
|---|---|---|
| 독자의 배경지식 수준에 맞춘 설명 복잡도 조절 | **강함** (참가자 실험 3건) | 무조건 쉽게 하면 오히려 정보가 잘린다 |
| 처음 나오는 어려운 용어를 맥락 안에서 정의 | **강함** (2024년 연구 이상의 근거) | 단순히 쉬운 단어로 바꾸는 것보다 우월 |
| 구조·형식 명시 (제목, 목록, 표) | **중간** (일반 평서문 연구 근거 + 공급사 권고) | LLM 출력에 직접 실험한 결과는 드물다 |
| 정보 순서 지정 (결론 먼저 등) | **약함** (LLM 설명 대상 실증 연구 미발견) | 실용적 선호로 보는 것이 타당 |
| 페르소나 부여 ("너는 전문가다") | **약함~주의** (벤치마크 연구) | 정확도 향상 보장 안 됨 |

이 표는 근거 강도 요약이며, 상세 내용과 주의점은 아래 근거 목록을 따른다.

## 근거가 강한 연구 (실제 참가자 실험 있음)

- **Know Your Audience** (Tal August, Kyle Lo, Noah A. Smith, Katharina Reinecke; CHI 2024)
  - 참가자 199/191/203명 규모의 실험 3건에서, 배경지식 수준에 따라 요약 난도의 효과가 달라짐
  - 주제에 익숙한 독자는 지나치게 쉬운 요약에서, 특히 한계·제약 부분을 건너뛰는 경향
  - 정보를 유지하면서 쉽게 설명하면 문장이 길어지더라도, 익숙하지 않은 독자에게 도움이 될 수 있음
  - https://arxiv.org/html/2403.04979 · https://doi.org/10.1145/3613904.3642289

- **Evaluating LLMs for Targeted Concept Simplification for Domain-Specific Texts**
  - (Sumit Asthana, Hannah Rashkin 외; EMNLP 2024) 사전(preliminary) 인간 평가에서: 어려운 용어를 "쉬운 단어로 바꾸는 것"보다 "맥락 안에서 정의·설명"하는 방식을 선호
  - 자동 지표와 인간 평가의 상관이 낮음 → 자동 점수만으로는 어휘 난도를 판단하기 어려움
  - https://aclanthology.org/2024.emnlp-main.357/

- **Improving understanding of clinical notes with LLM augmentation**
  - (Niklas Mannhardt 외; 2024 arXiv preprint) 200명 랜덤 설문: GPT-4가 생성한 "정의 + 쉬운 말 단순화" 추가가 이해 점수를 향상시킴 (0.63 vs. 0.54, p=.002)
  - 단, 임상 노트라는 좁은 범위의 실험이며, 임상의 검토에서 오해 소지 오류가 발견됨
  - https://arxiv.org/html/2401.09637v1

- **Are LLM-generated plain language summaries truly understandable?**
  - (Yue Guo 외; 2025 preprint) 150명 크라우드소싱 평가: LLM이 쓴 "쉬운 언어" 요약은 인간이 쓴 요약과 주관적 평가는 비슷하지만, 실제 이해는 유의하게 낮았음
  - → "명료해 보인다(가독성·선호)"와 "실제로 이해된다"를 구분해야 한다
  - https://arxiv.org/html/2505.10409v1

- **Enhancing the Readability of Online Patient Education Materials Using LLMs** (Will 외; JMIR 2025)
  - "초등학교 5학년 읽기 수준으로" 프롬프트: 가독성 지표 개선, 이해도(PEMAT) 유지 확인. 단, Gemini·Claude 재작성의 3.3%가 부정확하다는 평가 존재 (ChatGPT 재작성은 없음)
  - 평가 방식이 내용 전문가 기준이라는 점 유의. 환자 이해 실험은 아님
  - https://pmc.ncbi.nlm.nih.gov/articles/PMC12177420/

- **Note-taking and LLM use: A randomized experiment in secondary schools** (Kreijkes 외; Computers & Education 2025, 사전 등록)
  - 405명 14–15세 학생 대상: LLM 단독 사용보다 노트 작성(단독 또는 LLM 병용)이 이해·기억에 유리
  - → LLM은 초기 접근에 도움이 되지만, 이해와 기억을 위해서는 능동적 학습(노트 작성 등)이 필요
  - https://www.microsoft.com/en-us/research/publication/effects-of-llm-use-and-note-taking-on-reading-comprehension-and-memory-a-randomised-experiment-in-secondary-schools/

## 오해 방지 주의사항

- **"아이에게 설명하듯" 프롬프트는 안전장치가 아니다**: 의학 보고서 단순화에서 방사선 전문의 15인이 부정확·누락·잠재적 위해 소재를 발견 (Jeblick 외; European Radiology). https://pmc.ncbi.nlm.nih.gov/articles/PMC11126432/
- **페르소나 부여 ("너는 전문가다")는 성능을 높이지 않는다**: 2,410개 질문 벤치마크에서 역할 페르소나가 객관적 성능을 일관되게 개선하지 못함 (Zheng 외; 2024 preprint). https://arxiv.org/html/2311.10054v3
  - 도메인 문서 페르소나 요약 연구(Mullick 외; Findings of ACL 2024)는 대상(의사·환자·일반인)별 요약이 실용적일 수 있음을 보임 — 다만 "casual하게 act as a doctor라고 지시하면 이해가 높아진다"는 직접 증거는 아님. https://aclanthology.org/2024.findings-acl.849/
- **프롬프트 입력 형식(MD/JSON/YAML)은 모델 성능 연구이며 독자 이해 연구가 아니다**: 형식에 따른 성능 변동은 과제·모델에 따라 다르며 보편적으로 최선인 형식은 없음. 이를 "Markdown이 가독성에 좋다"의 증거로 쓰지 말 것. https://arxiv.org/html/2411.10541v1/
- **결론-우선/역피라미드 같은 정보 순서의 실증 비교는 2023–2026 LLM 설명 연구에서 발견되지 않음**: "짧은 답을 먼저 달라"는 요청은 검증 가능한 실용적 선호이며, 그 자체를 확립된 근거로 취급하지 말 것.

## 구조·형식에 대한 정확한 위치

- 구조화 출력(제목·핵심 메시지·목록)을 독자가 선호하고 이해에 도움이 될 수 있다는 근거는, 주로 일반 문서 대상 plain language 연구(위 CHI 논문이 인용한 배경)에 기반.
- LLM 출력의 Markdown 형식에 대한 이해/읽는 시간 직접 실험은 찾지 못함 → 미확인 사항.
- LLM 회사의 공식 가이드(Anthropic, Google, OpenAI)는 명확한 지시·예시·섹션 구분·응답 형식 지정을 권고하지만, 이는 독립적인 인간 이해 실험 근거가 아닌 업계 권고로 취급해야 함.
  - https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices
  - https://ai.google.dev/gemini-api/docs/prompting-strategies
  - https://developers.openai.com/api/docs/guides/prompt-engineering

## 근거 기반 프롬프트 템플릿 (연구 결과 합성)

> **[주제]**을 **[구체적 독자 + 이미 아는 것]** 기준으로 설명해줘.
> **짧은 답**부터 시작하고, 이후 **3–5단계 번호 설명**을 붙여줘.
> 처음 나온 전문 용어는 그 자리에서 **간단한 정의 + 예시**로 설명해줘.
> 쉬운 언어를 쓰되, **중요한 한계·예외·부정확 가능성은 빼지 말고 유지**해줘.
> 확립된 사실과 불확실한 추측을 구분하고, 모르면 모른다고 말해줘.

## 이 저장소(용도별 튜닝)에 적용할 시사점

1. **용도별 프로필에는 반드시 (a) 독자의 배경지식, (b) 설명 난도, (c) 용어 처리 방식, (d) 우선 순위(결론/상세), (e) 유지할 제약·한계 명시 여부**를 지정문으로 포함.
2. **페르소나는 스타일/관점 목적으로만**, "정확성 보호 장치"로는 사용하지 않기. 고위험 주제(의학, 법률, 재무)에는 "한계 유지 + 검증 유도" 지시를 추가.
3. **가독성·선호가 아니라 실제 이해를 목표 지표로 삼기.** 사용자가 읽고 스스로 설명·적용하는 것으로 검증.
4. **"쉽게 써줘"를 단독 지시로 쓰지 않기** — 정보 손실로 이어질 수 있음 (CHI 2024 근거).
5. 형식 실험(예: 이 저장소의 프로필 유효 확인)에서 결과를 기록할 때, **해석·신뢰 수준**을 명시.
