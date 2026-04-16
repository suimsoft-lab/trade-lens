---
layout: single
title: "Firebase + OpenAI로 HS 코드 AI 분류 시스템 구축하기"
date: 2026-04-16 11:00:00 +0900
categories: [devlog]
tags: [firebase, openai, cloud-functions, flutter, architecture]
toc: true
toc_sticky: true
---

HS Finder의 핵심은 AI 분류 파이프라인입니다.
이미지를 업로드하면 어떤 과정을 거쳐 HS 코드 후보가 나오는지 설명합니다.

## 전체 흐름

```
Flutter 앱
  1. 이미지 선택 (카메라 / 갤러리)
  2. base64 변환 + 압축
  3. Firebase Cloud Functions 호출

Cloud Functions (analyzeImage)
  4. OpenAI Vision API로 이미지 분석
  5. 카테고리, 소재, 용도 추출
  6. 결과를 Flutter로 반환

Flutter 앱
  7. Q&A 질문 표시 → 사용자 답변 수집
  8. 상품 프로파일 구성

Cloud Functions (searchHSCode)
  9. 상품 프로파일 + 이미지 분석 결과를 GPT에 전달
  10. HS 코드 후보 + 신뢰도 + 근거 반환

Flutter 앱
  11. 결과 화면 표시
```

## 이미지 전처리

Flutter에서 이미지를 Functions로 보내기 전 압축을 적용합니다.

```dart
// flutter_image_compress 사용
final compressed = await FlutterImageCompress.compressWithFile(
  path,
  quality: 75,
  minWidth: 800,
  minHeight: 800,
);
final base64Image = base64Encode(compressed!);
```

이미지 크기를 줄여 Functions 처리 시간과 비용을 절약합니다.

## Cloud Functions: 이미지 분석

```javascript
// analyzeImage (Node.js)
const response = await openai.chat.completions.create({
  model: "gpt-4.1-mini",
  messages: [{
    role: "user",
    content: [
      { type: "image_url", image_url: { url: `data:image/jpeg;base64,${imageBase64}` } },
      { type: "text", text: "이 상품의 카테고리, 소재, 주요 용도를 JSON으로 분석해줘." }
    ]
  }]
});
```

GPT Vision이 이미지를 보고 카테고리, 소재, 용도를 구조화된 JSON으로 반환합니다.

## Cloud Functions: HS 코드 검색

```javascript
// searchHSCode
const prompt = buildHSPrompt(productProfile); // 상품 프로파일 → 프롬프트
const response = await openai.chat.completions.create({
  model: "gpt-4.1-mini",
  messages: [
    { role: "system", content: "당신은 HS 코드 분류 전문가입니다..." },
    { role: "user", content: prompt }
  ],
  response_format: { type: "json_object" }
});
```

`response_format: json_object`로 JSON 형식의 응답을 강제해 파싱 오류를 방지합니다.

## API 키 보안

클라이언트(Flutter)에는 API 키를 절대 노출하지 않습니다.
모든 OpenAI 호출은 서버 사이드 Cloud Functions에서만 이루어집니다.

```
Flutter → Firebase Functions (HTTPS callable) → OpenAI
                    ↑
              환경 변수로 API 키 관리
              firebase functions:config:set openai.key="sk-..."
```

## 크레딧 차감 흐름

Functions 호출 성공 시 Firestore의 크레딧을 트랜잭션으로 차감합니다.

```javascript
await db.runTransaction(async (t) => {
  const userRef = db.doc(`users/${uid}`);
  const snap = await t.get(userRef);
  const current = snap.data().credits;
  if (current < 1) throw new Error("크레딧 부족");
  t.update(userRef, { credits: current - 1 });
});
```

트랜잭션을 사용해 동시 요청에서도 크레딧이 정확하게 차감됩니다.

---

다음 포스트에서는 RevenueCat 결제 연동 과정을 다룰 예정입니다.
