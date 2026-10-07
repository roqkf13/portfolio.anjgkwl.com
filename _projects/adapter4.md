---
title: "문화유산 관광 가이드"
subtitle: "전국의 문화유산과 관광지를 지도와 AI 가이드로 안내하는 관광 사이트"
summary: "문화유산과 관광지를 지도와 AI 가이드로 안내하는 관광 사이트입니다. 문화유산 퀴즈 · 포인트의 서버 로직을 만들었습니다."
order: 2
period: "2026.06"
team: "4명 팀 프로젝트"
role: "백엔드"
thumbnail: /assets/img/adapter4/home.webp
stack: ["FastAPI", "SQLite", "React", "Leaflet", "Vercel", "SQLAlchemy", "TypeScript", "Vite"]
links:
  - label: "사이트"
    url: "https://gaonai.cloud"
  - label: "팀 저장소"
    url: "https://github.com/pmhllll12/cloud.harrypoter"

# 페이지 본문 — 그림 7 : 글 3. 절마다 text(왼쪽 글)와 blocks(오른쪽 그림 — _includes/vblocks.html)
# 🔴 「내가 한 일」은 팀 저장소의 내 커밋(2026-06-22 ~ 06-25)으로 확인되는 것만 적는다(2026-10-07 대조)
sections:
  - title: "어떤 서비스인가"
    text: "전국의 문화유산과 관광지를 한곳에서 찾아보는 관광 사이트입니다. 지도에서 명소를 고르고, 소개와 운영 정보를 읽고, AI 가이드에게 물어볼 수 있습니다. Super-Sub 를 만든 네 사람이 그보다 앞서 함께 만들었습니다."
    blocks:
      - { type: tiles, items: ["관광정보 — 명소 소개 · 운영 정보", "관광동선 — 지도에서 찾기", "스토어 · 체험 티켓", "AI 관광 가이드"] }
      - { type: image, src: "/assets/img/adapter4/map.webp", alt: "관광동선 화면 — 지도와 추천 명소", caption: "관광동선 화면 — 지도에서 명소를 찾는다(화면의 숫자는 시연 데이터)" }

  - title: "서비스 구성"
    text: "화면과 서버를 나눠 만들었습니다."
    blocks:
      - type: cards
        items:
          - title: "화면"
            blocks:
              - { type: tiles, items: ["관광정보", "관광동선", "스토어", "티켓 · 예약", "AI 채팅"] }
              - { type: facts, items: ["React 19 · TypeScript · Vite", "Leaflet 지도", "Vercel 배포"] }
          - title: "AI 관광 가이드"
            blocks:
              - { type: flow, items: ["질문", "질문에 나온 명소의 사이트 자료", "LLM 답변"] }
              - { type: facts, items: ["Vercel 서버리스 함수"] }
          - title: "서버"
            blocks:
              - { type: tiles, items: ["문화유산 퀴즈 · 포인트", "티켓 예약", "지도 파일", "관광 챗"] }
              - { type: facts, items: ["FastAPI — 헥사고날 계층", "SQLAlchemy · SQLite"] }

  - title: "내가 한 일"
    text: "서버에서 문화유산 퀴즈와 포인트 적립을 맡았고, 화면의 대상을 충북에서 전국으로 넓혔습니다. 팀 저장소의 기록으로 확인되는 것만 적었습니다."
    blocks:
      - type: cards
        items:
          - title: "문화유산 퀴즈 · 포인트"
            blocks:
              - { type: flow, items: ["유산을 고른다", "아직 못 맞힌 문제 하나", "답을 낸다", "맞히면 포인트"] }
              - { type: facts, items: ["사용자별로 맞힌 문제를 기록", "유스케이스 · 포트 · 저장소 · ORM — 계층을 따라"] }
          - title: "퀴즈 데이터"
            blocks:
              - { type: tiles, items: ["성균관 문묘", "보은 법주사"] }
              - { type: facts, items: ["유산마다 문제를 채우는 스크립트", "다시 돌려도 겹쳐 들어가지 않게"] }
          - title: "화면 — 충북에서 전국으로"
            blocks:
              - type: compare
                from_title: "앞"
                to_title: "뒤"
                items:
                  - { from: "충북 관광을 AI와 함께", to: "대한민국 구석구석을 AI와 함께" }
                  - { from: "청주부터 단양까지", to: "서울부터 제주까지" }
              - { type: facts, items: ["첫 화면 · 관광정보 · 지도 · 스토어 · 티켓의 문구와 지역 표기"] }
---
