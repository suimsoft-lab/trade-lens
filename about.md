---
title: "HS Finder 앱 소개"
permalink: /about/
layout: single
toc: true
toc_sticky: true
---

<section class="section-hero">
  <p class="page-chip">About HS Finder</p>
  <h2>무역·통관 실무자를 위한 AI HS 코드 분류 앱</h2>
  <p>상품 사진 한 장으로 HS 코드 후보를 즉시 확인하세요.</p>
</section>

## 왜 만들었나요?

HS 코드 분류는 무역 실무에서 반복적으로 발생하지만, 코드 체계가 방대하고 복잡해 전문가도 시간이 많이 걸립니다.
**HS Finder**는 AI를 활용해 이 과정을 빠르고 정확하게 보조하기 위해 만들어졌습니다.

- 사진 한 장으로 상품을 인식하고
- 추가 질문으로 정보를 보완하며
- 신뢰도와 근거가 포함된 HS 코드 후보를 제시합니다.

> ⚠️ **면책 조항**: 이 앱은 의사결정 보조 도구입니다. 최종 HS 코드 분류는 반드시 관세사 또는 통관 전문 인력과 확인하세요.

## 주요 기능

### 1. 이미지 AI 분석

카메라로 촬영하거나 갤러리에서 상품 이미지를 선택하면, AI가 자동으로 카테고리, 소재, 용도를 분석합니다.

### 2. GPT 기반 HS 코드 검색

Firebase Cloud Functions + OpenAI `gpt-4.1-mini` 모델이 의미 기반으로 HS 코드를 분류합니다.
단순 키워드 검색이 아닌, 상품 특성을 종합적으로 해석하여 가장 적합한 코드를 추천합니다.

### 3. 맞춤 질문 응답 (Q&A)

AI 분석 이후 소재, 용도, 산업군, 포장 형태 등 분류에 필요한 추가 질문이 제시됩니다.
답변할수록 결과의 정확도가 높아집니다.

### 4. 상품 프로파일

모든 분석 결과와 Q&A 답변이 구조화된 상품 프로파일로 정리됩니다.
HS 코드를 요청하기 전 내용을 검토하고 수정할 수 있습니다.

### 5. 신뢰도 순 결과

HS 코드 후보가 신뢰도(%)와 함께 정렬되어 제시됩니다.
각 코드에는 선택 이유와 관련 세번 설명이 포함됩니다.

## 결제 구조

| 플랜 | 크레딧 | 비용 |
|------|--------|------|
| 기본 | 월 3회 무료 | 무료 |
| 소형 | 20크레딧 | 인앱 결제 |
| 중형 | 50크레딧 | 인앱 결제 |
| 대형 | 150크레딧 | 인앱 결제 |

- 무료 크레딧은 매월 1일 자동 리셋
- Google Play / App Store RevenueCat 연동

## 기술 스택

| 영역 | 기술 |
|------|------|
| 프레임워크 | Flutter 3.x / Dart 3.x |
| 상태 관리 | Riverpod 2.x |
| 라우팅 | GoRouter 13.x |
| 인증 | Firebase Auth (Google Sign-In) |
| DB | Cloud Firestore |
| AI 분석 | Firebase Cloud Functions + OpenAI gpt-4.1-mini |
| 결제 | RevenueCat Flutter SDK |
| 다국어 | flutter_localizations (ko / en) |

## 아키텍처

```
Clean Architecture + Feature-First

lib/
├── app/              # AppWidget, Router, Theme
├── core/             # Constants, Config, Utils
├── shared/           # Models, Providers, Widgets
├── l10n/             # ARB 다국어 파일
└── features/
    ├── auth/         # Google 로그인
    ├── home/         # 홈 화면
    ├── product_analysis/   # 이미지 AI 분석
    ├── qa_session/   # Q&A 및 프로파일 생성
    ├── hs_search/    # HS 코드 검색 (AI Cloud Function)
    ├── purchase/     # RevenueCat 결제
    ├── usage/        # 사용량 추적
    └── settings/     # 언어 전환, 면책 조항
```

<div class="cta-wrap">
  <a class="btn btn--primary" href="/trade-lens/blog/">개발 블로그 보기</a>
  <a class="btn btn--light-outline" href="https://github.com/suimsoft-lab/hs-code-assistant">GitHub 소스 코드</a>
</div>
