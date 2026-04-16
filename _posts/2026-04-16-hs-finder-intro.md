---
layout: single
title: "HS Finder 프로젝트 소개: AI로 HS 코드 분류를 더 빠르게"
date: 2026-04-16 10:00:00 +0900
categories: [project]
tags: [flutter, firebase, openai, hs-code, trade, customs]
toc: true
toc_sticky: true
---

`HS Finder`는 무역·통관 실무자를 위한 AI 기반 HS 코드 분류 앱입니다.
상품 사진 한 장으로 시작해 5단계를 거치면 신뢰도 순으로 정렬된 HS 코드 후보를 확인할 수 있습니다.

## 만들게 된 이유

HS 코드(Harmonized System Code)는 국제 무역에서 상품을 분류하는 표준 코드입니다.
6자리 이상의 체계로 구성되며 전 세계 98%의 상품이 이 코드로 분류됩니다.

문제는 **코드 체계가 방대하고 복잡**하다는 것입니다.

- 코드 체계가 수만 개에 달해 전문가도 찾는 데 시간이 걸림
- 상품 특성(소재, 용도, 산업군)을 종합적으로 고려해야 함
- 오분류 시 통관 지연, 관세 오납 등의 리스크 발생

이 문제를 AI로 보조할 수 있다면 실무자의 시간을 크게 절약할 수 있겠다는 생각에서 시작했습니다.

## 핵심 기술 결정

### AI 분석: Firebase Cloud Functions + OpenAI

이미지 분석과 HS 코드 검색 모두 서버 사이드 Cloud Functions에서 처리합니다.

```
클라이언트 (Flutter)
  → Firebase Cloud Functions
    → OpenAI gpt-4.1-mini
      → HS 코드 후보 + 신뢰도 + 근거
```

클라이언트에 API 키를 노출하지 않고, Functions에서 OpenAI를 호출하는 구조입니다.
이미지는 base64로 변환해 전송하고, GPT가 상품 특성을 분석한 뒤 HS 코드를 추론합니다.

### 상태 관리: Riverpod

Flutter 앱에서 Riverpod 2.x를 사용합니다.
각 feature가 독립적인 Provider를 갖는 구조로, 기능 간 의존성을 최소화했습니다.

```dart
// 분석 상태 예시
final analysisProvider = StateNotifierProvider<AnalysisNotifier, AnalysisState>(
  (ref) => AnalysisNotifier(ref),
);
```

### 결제: RevenueCat

인앱 결제는 RevenueCat Flutter SDK를 통해 처리합니다.

```
구매 버튼
  → RevenueCat SDK
    → Google Play / App Store
      → RevenueCat Webhook
        → Firebase Functions
          → Firestore users/{uid}.credits 증가
```

RevenueCat Webhook이 결제 완료를 감지하면 Firebase Functions가 Firestore의 크레딧을 증가시킵니다.

## 아키텍처: Clean Architecture + Feature-First

```
lib/
├── app/              # AppWidget, Router, Theme
├── core/             # Constants, Config, Utils
├── shared/           # 공용 Models, Widgets
└── features/
    ├── auth/
    ├── product_analysis/
    ├── qa_session/
    ├── hs_search/
    ├── purchase/
    └── settings/
```

각 feature 내부는 `domain → data → presentation` 레이어로 구성됩니다.
인터페이스(domain)와 구현체(data)를 분리해 Mock 서비스로 개발·테스트가 가능합니다.

## 다국어 지원

`flutter_localizations`를 사용해 한국어/영어를 지원합니다.
ARB 파일 기반으로, 앱 내에서 언어를 전환할 수 있습니다.

```
l10n/
├── app_ko.arb   # 한국어
└── app_en.arb   # English
```

## 면책 조항

> ⚠️ **이 앱은 의사결정 보조 도구입니다.**
> 최종 HS 코드 분류는 반드시 관세사 또는 통관 전문 인력과 확인하세요.

AI가 제시하는 코드는 참고용이며, 공식 분류 결과를 대체하지 않습니다.

## 다음 계획

- 검색 히스토리 클라우드 동기화
- 즐겨찾기 기능
- HS 코드 변경 이력 알림
- 웹 버전 개발

---

앱에 대한 질문이나 피드백은 [GitHub Issues](https://github.com/suimsoft-lab/hs-code-assistant/issues)로 남겨주세요.
