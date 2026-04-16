# Release Notes

## v1.1.0 — 2026-04-16

### 추가
- `hs-finder/privacy-policy.md` — 앱 전용 개인정보처리방침 (v2.0, 수집 항목 표 · 제3자 벤더 목록 · 이용자 권리 포함)
- `hs-finder/terms.md` — 이용약관 (서비스 정의 · 요금제 · 환불 · 면책 등 10개 조항)
- `hs-finder/disclaimer.md` — 법적 고지 (AI 한계 · 전문가 확인 권고 · 책임 제한)
- `hs-finder/safety-policy.md` — 안전 이용 정책 (사용 지침 · 데이터 보안 · 규제 품목 경고)

### 변경
- 푸터에 개인정보처리방침 링크 추가 (`_config.yml`)

---

## v1.0.0 — 2026-04-16

### 추가 (최초 릴리스)

#### 사이트 구조
- Jekyll + Minimal Mistakes 테마 기반 사이트 초기 구성
- `index.md` — 스플래시 레이아웃 홈페이지 (핵심 기능 그리드 · 5단계 워크플로 · 기술 스택 · CTA 버튼)
- `about.md` — 앱 상세 소개 (아키텍처 · 기능 · 요금제 · 다국어 지원)
- `blog.md` — 블로그 목록 페이지
- `privacy-policy.md` — 루트 개인정보처리방침

#### 블로그 포스트
- `_posts/2026-04-16-hs-finder-intro.md` — HS Finder 프로젝트 소개 (동기 · 핵심 기술 결정사항 · 로드맵)
- `_posts/2026-04-16-tech-stack-firebase-openai.md` — 기술 스택 심층 분석 (AI 파이프라인 · 이미지 전처리 · Cloud Functions 흐름 · 크레딧 차감)

#### 스타일
- `_sass/minimal-mistakes/_custom.scss` — 커스텀 SCSS (컬러 변수 · 버튼 · 그리드 · 5단계 플로우 시각화 · 반응형)

---

## 앱 버전 대응표

| 사이트 버전 | HS Finder 앱 버전 | 주요 내용 |
|------------|------------------|-----------|
| v1.1.0 | v1.0.x | 정책 페이지 완비 (스토어 심사 대응) |
| v1.0.0 | v1.0.0 | 사이트 최초 공개 |
