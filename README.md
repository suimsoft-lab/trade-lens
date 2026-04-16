# Trade Lens

> **HS Finder** 앱 소개 & 정책 문서 사이트
> AI로 HS 코드를 찾는 가장 스마트한 방법 — 무역·통관 실무자를 위한 Jekyll 블로그

**사이트 URL:** https://suimsoft-lab.github.io/trade-lens

---

## 개요

이 저장소는 Flutter 모바일 앱 **HS Finder**의 마케팅 사이트 및 정책 문서 허브입니다.
Jekyll + GitHub Pages 로 정적 사이트로 배포되며, 앱 소개 · 기술 블로그 · 법적 정책 페이지를 포함합니다.

---

## 기술 스택

| 구분 | 기술 |
|------|------|
| 정적 사이트 | Jekyll (GitHub Pages 호환) |
| 테마 | [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) |
| 스타일 | Custom SCSS (`_sass/minimal-mistakes/_custom.scss`) |
| 마크다운 | Kramdown |
| 배포 | GitHub Pages (master 브랜치 자동 배포) |

---

## 디렉토리 구조

```
trade-lens/
├── _config.yml                  # Jekyll 설정 (URL, 테마, 작성자 정보)
├── _posts/                      # 기술 블로그 포스트
│   ├── 2026-04-16-hs-finder-intro.md
│   └── 2026-04-16-tech-stack-firebase-openai.md
├── _sass/
│   └── minimal-mistakes/
│       └── _custom.scss         # 커스텀 스타일
├── hs-finder/                   # 앱 전용 정책 페이지
│   ├── privacy-policy.md        # 개인정보처리방침
│   ├── terms.md                 # 이용약관
│   ├── disclaimer.md            # 법적 고지
│   └── safety-policy.md        # 안전 이용 정책
├── index.md                     # 홈페이지
├── about.md                     # 앱 상세 소개
├── blog.md                      # 블로그 목록
├── privacy-policy.md            # 루트 개인정보처리방침
└── Gemfile                      # Ruby 의존성
```

---

## 로컬 개발 환경 설정

### 사전 요구사항
- Ruby 3.x
- Bundler (`gem install bundler`)

### 실행

```bash
# 의존성 설치
bundle install

# 로컬 서버 실행 (http://localhost:4000/trade-lens)
bundle exec jekyll serve
```

---

## 배포

`master` 브랜치에 push하면 GitHub Pages가 자동으로 사이트를 빌드·배포합니다.

```bash
git push origin master
```

배포 완료까지 약 1~3분 소요됩니다.

---

## 관련 링크

| 항목 | URL |
|------|-----|
| 사이트 | https://suimsoft-lab.github.io/trade-lens |
| GitHub | https://github.com/suimsoft-lab |
| 앱 (Flutter) | https://github.com/suimsoft-lab/hs-code-assistant |

---

## 라이선스

© 2026 suimsoft-lab. All rights reserved.
