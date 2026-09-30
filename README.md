# portfolio.anjgkwl.com

개인 포트폴리오 — <https://portfolio.anjgkwl.com>
`main` 에 push 하면 GitHub Actions 가 빌드해 GitHub Pages 로 배포한다(약 1분).

## 고치는 곳

| 무엇 | 파일 |
|---|---|
| 홈 소개(이름 · 한 줄 · 소개 · 링크 · 기술 · 해 본 일) | `_data/profile.yml` — 비워 둔 값(`""`)은 화면에 안 나온다 |
| 프로젝트 | `_projects/<이름>.md` — 파일 하나가 홈 카드 하나 + `/projects/<이름>/` 페이지 하나 |
| 모양 | `assets/css/site.css` · `_layouts/` |

## 프로젝트 추가하는 법

`_projects/<영문-이름>.md` 를 만든다. 주소는 파일 이름을 따른다(`_projects/scout.md` → `/projects/scout/`).

```markdown
---
title: "프로젝트 이름"
subtitle: "상세 페이지 제목 아래 한 줄"
summary: "홈 카드에 들어갈 두세 줄 설명"
order: 2                     # 홈 카드 순서 — 작을수록 앞
period: "2026.10 – 2026.12"
team: "개인 프로젝트"
role: "기획 · 개발"
thumbnail: /assets/img/<이름>/home.webp   # 없으면 빼도 된다(카드에 그림이 안 들어간다)
stack: ["Python", "Next.js"]              # 카드에는 앞의 5개만 나온다
links:                                     # 첫 번째가 강조 단추가 된다
  - label: "데모"
    url: "https://..."
    note: "링크 아래 작은 안내(없으면 빼도 된다)"
  - label: "저장소"
    url: "https://github.com/..."
---

## 어떤 서비스인가

## 내가 한 일

### 소제목
- ...
```

캡처는 `assets/img/<이름>/` 에 webp 로 둔다(가로 1200px 이면 충분하다). PNG 가 있으면:

```bash
ffmpeg -i shot.png -vf scale=1200:-1 -c:v libwebp -quality 78 assets/img/<이름>/home.webp
```

## 로컬에서 보기

```bash
export PATH="$HOME/.rbenv/shims:$HOME/.rbenv/bin:$PATH"   # 비대화형 셸이면(rbenv 초기화가 ~/.bashrc 에만 있다)
bundle exec jekyll serve      # http://localhost:4000
```

`_config.yml` 을 고쳤으면 서버를 다시 띄워야 반영된다. Sass 경고는 원래 난다(테마 minima 의 옛 문법 — 회귀가 아니다).
