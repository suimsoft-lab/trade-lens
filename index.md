---
layout: splash
title: "AI로 HS 코드를 찾는 가장 스마트한 방법"
author_profile: false
header:
  overlay_color: "#111827"
  overlay_filter: 0.6
  actions:
    - label: "앱 소개 보기"
      url: "/trade-lens/about/"
      class: "btn btn--primary"
    - label: "최신 업데이트"
      url: "/trade-lens/blog/"
      class: "btn btn--inverse"
---

<section class="section-hero">
  <p class="page-chip">HS Finder</p>
  <h2>무역·통관 실무자를 위한 AI HS 코드 분류 앱</h2>
  <p>상품 사진 한 장으로 HS 코드 후보를 즉시 확인하세요.<br>
  AI 분석 → 추가 질문 → 신뢰도 순 결과까지, 5단계로 완료됩니다.</p>
</section>

## 핵심 기능

<div class="app-grid">
  <article class="app-card">
    <h3>📷 이미지 AI 분석</h3>
    <p>상품 사진에서 카테고리, 소재, 용도를 자동으로 추출합니다. 카메라 촬영 또는 갤러리 선택 모두 지원합니다.</p>
  </article>
  <article class="app-card">
    <h3>🤖 GPT 기반 HS 코드 검색</h3>
    <p>OpenAI gpt-4.1-mini 모델이 의미 기반으로 HS 코드를 분류하고, 신뢰도와 근거를 함께 제공합니다.</p>
  </article>
  <article class="app-card">
    <h3>💬 맞춤 질문 응답</h3>
    <p>소재, 용도, 산업군, 포장 형태 등 분류에 필요한 핵심 질문에 답하면 더욱 정확한 결과를 얻을 수 있습니다.</p>
  </article>
  <article class="app-card">
    <h3>📋 상품 프로파일</h3>
    <p>분석 결과와 답변을 구조화된 프로파일로 정리하여 검토하고, HS 코드 근거를 명확하게 확인할 수 있습니다.</p>
  </article>
</div>

## 5단계 분류 플로우

<div class="flow-steps">
  <div class="flow-step">
    <span class="step-num">1</span>
    <div>
      <strong>사진 촬영</strong>
      <p>카메라로 촬영하거나 갤러리에서 상품 이미지를 선택합니다.</p>
    </div>
  </div>
  <div class="flow-step">
    <span class="step-num">2</span>
    <div>
      <strong>AI 분석</strong>
      <p>AI가 상품 카테고리와 특징을 자동으로 분석합니다.</p>
    </div>
  </div>
  <div class="flow-step">
    <span class="step-num">3</span>
    <div>
      <strong>질문 응답</strong>
      <p>소재, 용도, 산업군, 포장 형태 등 추가 질문에 답합니다.</p>
    </div>
  </div>
  <div class="flow-step">
    <span class="step-num">4</span>
    <div>
      <strong>상품 프로파일</strong>
      <p>분석 결과와 답변을 구조화된 프로파일로 검토합니다.</p>
    </div>
  </div>
  <div class="flow-step">
    <span class="step-num">5</span>
    <div>
      <strong>HS 코드 결과</strong>
      <p>신뢰도 순으로 정렬된 HS 코드 후보와 선택 이유를 확인합니다.</p>
    </div>
  </div>
</div>

## 기술 스택

<div class="latest-grid">
  <article class="latest-card">
    <p class="latest-card__meta"><span class="category-badge">Frontend</span></p>
    <h3>Flutter 3.x / Dart 3.x</h3>
    <p>iOS · Android 동시 지원, Riverpod 상태 관리, GoRouter 라우팅</p>
  </article>
  <article class="latest-card">
    <p class="latest-card__meta"><span class="category-badge">Backend</span></p>
    <h3>Firebase + OpenAI</h3>
    <p>Firebase Auth · Firestore · Cloud Functions, gpt-4.1-mini 기반 AI 분류</p>
  </article>
  <article class="latest-card">
    <p class="latest-card__meta"><span class="category-badge">결제</span></p>
    <h3>RevenueCat</h3>
    <p>무료 3회/월 + 크레딧 충전 (20 / 50 / 150), Google Play · App Store 연동</p>
  </article>
  <article class="latest-card">
    <p class="latest-card__meta"><span class="category-badge">다국어</span></p>
    <h3>한국어 / 영어</h3>
    <p>flutter_localizations 기반, 기본 언어 한국어, 앱 내 언어 전환 지원</p>
  </article>
</div>

## 면책 조항

<div class="notice--warning">
  <p>⚠️ <strong>이 앱은 의사결정 보조 도구입니다.</strong><br>
  최종 HS 코드 분류는 반드시 관세사 또는 통관 전문 인력과 확인하세요.</p>
</div>

<div class="cta-wrap">
  <a class="btn btn--primary" href="/trade-lens/about/">앱 상세 소개</a>
  <a class="btn btn--inverse" href="/trade-lens/blog/">개발 블로그</a>
</div>
