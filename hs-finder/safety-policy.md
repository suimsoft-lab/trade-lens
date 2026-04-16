---
title: "안전 정책"
permalink: /hs-finder/safety-policy/
layout: single
toc: true
toc_sticky: true
---

<section class="section-hero">
  <p class="page-chip">HS Finder</p>
  <h2>안전 정책</h2>
  <p>최종 수정일: 2026년 4월 16일</p>
</section>

HS Finder는 무역·통관 업무를 보조하는 도구로서, 이용자와 사회의 안전을 위해 아래 정책을 운영합니다.

## 1. 서비스 안전 사용 지침

### 1.1 결과 활용 원칙

HS Finder의 분류 결과는 **업무 보조 자료**로만 활용하세요.

✅ **권장 사용 방식**
- 초기 HS 코드 범위를 좁히는 참고 자료로 활용
- 관세사나 전문가와 상담 전 사전 검토용으로 사용
- 분류 후보군을 파악하여 전문가 상담 시 활용

❌ **권장하지 않는 사용 방식**
- AI 결과를 검토 없이 세관 신고서에 그대로 기재
- 전문가 확인 없이 고가 물품이나 규제 물품 분류에 단독 사용
- 법적 분쟁, 세관 심사 시 유일한 근거로 제출

### 1.2 이중 용도 물품 (Dual-Use Goods)

군사 전용 또는 민·군 겸용 물품은 특별 규제를 받습니다.

- 전략물자관리원 (KOSTI) 또는 해당 국가 규제기관에 반드시 확인하세요.
- 수출 허가가 필요한 물품은 HS Finder 결과만으로 판단하지 마세요.

### 1.3 규제 물품

다음 물품 카테고리는 특별 주의가 필요합니다.

| 카테고리 | 주의 사항 |
|----------|-----------|
| 의약품, 의료기기 | 식품의약품안전처 허가 및 특수 HS 코드 확인 필요 |
| 화학물질 | 화학물질관리법, 국제 규제 목록 확인 필요 |
| 식품 | 식품위생법 및 검역 요건 별도 확인 필요 |
| 동·식물 | CITES 협약, 검역 규정 별도 확인 필요 |
| 전략물자 | 전략물자관리원 수출 허가 여부 확인 필요 |

## 2. 데이터 보안

### 2.1 이미지 처리

- 업로드된 상품 이미지는 AI 분석 후 서버에 영구 저장되지 않습니다.
- 이미지는 Firebase Cloud Functions를 통해 OpenAI API로 전송되며, 처리 후 즉시 삭제됩니다.
- **주의**: 이미지에 개인정보, 기밀 정보가 포함되지 않도록 하세요.

### 2.2 계정 보안

- Google 계정 보안 설정을 최신 상태로 유지하세요.
- 2단계 인증을 활성화하세요.
- 공용 기기에서 사용 후 반드시 로그아웃하세요.

### 2.3 데이터 전송

- 모든 통신은 HTTPS (TLS 1.2 이상)로 암호화됩니다.
- Firebase Security Rules로 사용자별 데이터 접근이 제한됩니다.

## 3. AI 안전 사용

### 3.1 AI 결과의 신뢰도

HS Finder는 각 분류 후보에 신뢰도(%)를 함께 제공합니다.

| 신뢰도 | 권장 대응 |
|--------|-----------|
| 75% 이상 | 전문가 검토 후 참고 가능 |
| 50~74% | 추가 정보 입력 또는 전문가 상담 권장 |
| 50% 미만 | 전문가 직접 상담 강력 권장 |

### 3.2 AI 편향 및 오류 가능성

- AI 모델은 학습 데이터의 한계로 특정 상품 유형에 편향이 있을 수 있습니다.
- 신규 상품이나 혁신적인 제품은 기존 카테고리에 맞지 않을 수 있습니다.
- 오류가 발견된 경우 [GitHub Issues](https://github.com/suimsoft-lab/hs-code-assistant/issues)로 신고해 주세요.

## 4. 금지 사용

다음 목적으로의 서비스 사용을 금지합니다.

- 수출 통제 회피 또는 불법 물품 반입·반출
- 관세 포탈, 원산지 허위 신고 등 관세법 위반
- 허위 무역 서류 작성에 활용
- 서비스 자동화 도구를 통한 대량 요청 (서비스 약관 위반)

## 5. 신고 및 문의

서비스 이용 중 안전 관련 문제를 발견하셨나요?

- **오류 신고**: [GitHub Issues](https://github.com/suimsoft-lab/hs-code-assistant/issues)
- **보안 취약점**: GitHub 비공개 이슈로 신고해 주세요.

<div class="notice--info">
  <p>이 안전 정책은 이용자와 사회의 안전한 서비스 이용을 위해 지속적으로 업데이트됩니다.</p>
</div>

<div class="cta-wrap">
  <a class="btn btn--light-outline btn--small" href="/trade-lens/hs-finder/terms/">이용약관</a>
  <a class="btn btn--light-outline btn--small" href="/trade-lens/hs-finder/privacy-policy/">개인정보처리방침</a>
  <a class="btn btn--light-outline btn--small" href="/trade-lens/hs-finder/disclaimer/">면책조항</a>
</div>
