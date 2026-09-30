---
title: "Super-Sub"
subtitle: "생활체육 경기 영상으로 실력을 검증하고, 팀에 필요한 용병을 찾아 주는 플랫폼"
summary: "경기 영상을 올리면 자세를 분석해 실력 리포트를 만들고, 그 결과로 팀의 빈 자리를 채울 사람을 찾아 줍니다."
order: 1
period: "2026.08 – 2026.10 (10주)"
team: "4명 팀 프로젝트"
role: "백엔드"
thumbnail: /assets/img/supersub/home.webp
stack: ["Python", "FastAPI", "PostgreSQL", "Next.js", "Flutter", "pgvector", "ViTPose", "EXAONE", "vLLM", "k3s", "AWS", "Cloudflare"]
links:
  - label: "데모"
    url: "https://supersub.anjgkwl.com"
    note: "화면 · 서버 · 영상 분석이 모두 개인 PC 에서 돌아서, PC 가 꺼져 있으면 데모만 열리지 않습니다. 이 페이지와 팀 저장소는 늘 열립니다."
  - label: "팀 저장소"
    url: "https://github.com/pmhllll12/super-sub.cloud"

# 페이지 본문 — 그림 7 : 글 3(사용자, 2026-09-30). 절마다 text(왼쪽 글)와 blocks(오른쪽 그림 — _includes/vblocks.html)
# 🔴 그림의 말 · 숫자는 팀 문서 · 저장소로 확인된 것만. 팀 main 에 들어간 것만 「내가 한 일」에 적는다(09-29)
sections:
  - title: "어떤 서비스인가"
    text: "생활체육 팀(풋살 · 축구 등)은 사람이 모자랄 때 용병을 구하지만, 처음 보는 사람의 실력은 알 길이 없습니다. Super-Sub 는 그 사람이 올린 경기 영상을 근거로 삼습니다."
    blocks:
      - type: flow
        items: ["경기 영상", "관절(자세) 추출", "항목별 점수", "실력 리포트 — 등급 · 판정 문장"]
      - type: flow
        items: ["선수 카드", "포메이션 빈 자리 — AI 추천 · 지인 찾기", "경기 신청 · 수락", "알림"]

  - title: "서비스 구성"
    text: "4명이 영역을 나눠 맡았습니다. 수치는 팀 문서의 2026-09-23 기준입니다."
    blocks:
      - type: people
        items:
          - { name: "박민호", role: "PM · QA" }
          - { name: "백성검", role: "웹 · 앱" }
          - { name: "나", role: "백엔드 · 파이프라인 · 배포", me: true }
          - { name: "정상호", role: "AI 분석" }
      - type: cards
        items:
          - title: "영상 분석 AI"
            blocks:
              - { type: flow, items: ["사람 검출(RT-DETR)", "자세 추정(ViTPose)", "동작 특징", "규칙(루브릭) 채점"] }
              - type: stats
                items:
                  - { num: "0.00", label: "같은 영상 다섯 번 — 총점 표준편차(영상 4편)" }
                  - { num: "약 1분 6초", label: "한 편 분석, S3 입출력까지(T4 · vLLM)" }
              - { type: facts, items: ["등급은 코드가 결정론적으로", "EXAONE 4.0 1.2B 는 근거 문장만", "GPU 워커가 큐에서 가져간다"] }
              - { type: note, text: "한계 — 채점 기준은 축구 인스텝 슈팅 하나, 임계값은 지도자 검수 전 잠정치" }
          - title: "웹 · 앱"
            blocks:
              - { type: tiles, items: ["분석 리포트 — 등급 · 레이더 차트", "선수 카드 · 공개 링크", "포메이션 판", "AI 추천"] }
              - { type: flow, items: ["팀 매칭 — 조건", "후보", "신청", "수락"] }
              - { type: facts, items: ["Next.js 16 · React 19", "서버 쪽 중계(BFF) · httpOnly 쿠키", "Flutter · Riverpod — 계약 시험 · 실서버 연결(스토어 배포 전)"] }
          - title: "백엔드 · 데이터"
            blocks:
              - type: stats
                items:
                  - { num: "7", label: "컨텍스트(헥사고날)" }
                  - { num: "100", label: "API 엔드포인트" }
                  - { num: "48", label: "DB 마이그레이션" }
              - { type: tiles, items: ["사용자", "카드", "분석", "매칭", "평가", "과금", "알림"] }
          - title: "운영 · 협업"
            blocks:
              - { type: flow, items: ["이미지가 올라옴", "2분 안에 서버가 스스로 갱신", "파드가 뜰 때 마이그레이션"] }
              - { type: facts, items: ["API — EC2 의 k3s", "영상 — S3", "분석 — 필요할 때만 켜는 GPU 서버", "웹 — Vercel · 앞단 — Cloudflare"] }
              - type: stats
                items:
                  - { num: "1,126", label: "백엔드 시험" }
                  - { num: "446", label: "AI 시험" }
                  - { num: "1,085", label: "웹 시험" }
                  - { num: "419", label: "앱 시험" }
              - { type: facts, items: ["GitHub Actions — 백엔드(실제 DB) · 앱 시험 · 이미지 빌드", "제안서 9장 · 부록 · 개발 로그를 문서 사이트로"] }

  - title: "내가 맡은 일 — 백엔드"
    text: "팀에서 백엔드를 맡았습니다. 커밋 439건 중 175건이 백엔드 코드(fastapi/)이고, 나머지는 대부분 API 계약 · 요구사항 같은 설계 · 진행 문서입니다(2026-09-29 기준)."
    blocks:
      - { type: bar, label: "백엔드 코드 커밋", value: 175, total: 439 }
      - type: cards
        items:
          - title: "서버의 뼈대와 규칙"
            blocks:
              - { type: tiles, items: ["바운디드 컨텍스트 × 계층(헥사고날)", "API 계약 문서 + pytest", "PostgreSQL · SQLAlchemy · Alembic"] }
              - { type: facts, items: ["스키마 변경은 마이그레이션으로"] }
          - title: "회원과 보안"
            blocks:
              - { type: tiles, items: ["가입 · 로그인 — bcrypt · 서명된 JWT"] }
              - { type: flow, items: ["구글 ID 토큰 검증", "계정 생성"] }
              - { type: facts, items: ["인증 사건 로깅", "인증 엔드포인트 요청 제한", "운영에서 API 문서(/docs) 닫기"] }
          - title: "영상 분석 파이프라인"
            blocks:
              - { type: flow, items: ["업로드 — S3 사전 서명 URL", "작업 큐", "워커", "S3 결과 → DB 적재", "리포트 API"] }
              - { type: facts, items: ["멈춘 작업 회수", "프로필 보관", "DB · S3 연쇄 삭제", "저장 안 한 임시 영상 정리", "재업로드 감지"] }
          - title: "팀과 매칭"
            blocks:
              - { type: flow, items: ["팀 초대 · 수락", "팀↔팀 경기 신청 · 수락", "알림"] }
              - { type: facts, items: ["매칭 조건 · 상대 후보", "빈 자리 추천 후보", "서로 지인 신청"] }
          - title: "운영"
            blocks:
              - { type: tiles, items: ["/metrics 엔드포인트", "k3s 배포 매니페스트", "시연용 자동 수락 봇"] }

  - title: "맡은 영역 밖에서 한 일"
    text: "맡은 영역은 백엔드였지만, 기능이 화면 끝까지 이어지도록 다른 사람의 영역도 필요한 만큼 고쳤습니다. 팀 main 에 들어간 것만 적었습니다."
    blocks:
      - type: cards
        items:
          - title: "웹 화면 — 백성검 님 영역"
            blocks:
              - { type: tiles, items: ["오버롤 등급 · 레이더 차트", "진행 표시가 실제 완료를 따라감 · 실패는 따로", "관리자 페이지(/admin/videos)", "매칭 · 경기 화면이 페이지를 옮겨도 이어짐", "「경기 완료」 흐름 · 시간 겹침 규칙 + 시험", "시연용 심사위원 계정 배정"] }
              - { type: note, text: "화면 ⇄ 서버 — 어긋나던 결함(초대를 수락해도 판에 안 서던 것 · 뺀 사람이 새로고침하면 되살아나던 것)을 양쪽을 함께 고쳐 풀었다" }
          - title: "협업 도구"
            blocks:
              - { type: flow, items: ["push · PR", "CI", "백엔드(실제 PostgreSQL · pgvector) · Flutter 시험"] }
              - { type: facts, items: ["시험을 도는 CI 를 처음 걸었다", "문서 사이트 그림 · ERD 생성기를 저장소로"] }

  - title: "끝난 뒤에도 돌게 — 개인 사본"
    text: "팀 서비스는 AWS 에서 돌았습니다. 프로젝트가 끝나도 링크 하나로 보여 줄 수 있도록, 팀 코드는 한 줄도 고치지 않고 전체를 내 PC 로 옮긴 사본을 따로 운영합니다 — 위 「데모」가 그것입니다."
    blocks:
      - type: compare
        from_title: "팀(AWS)"
        to_title: "개인 사본(내 PC)"
        items:
          - { from: "EC2", to: "k3s — PostgreSQL · 백엔드 · 화면" }
          - { from: "S3", to: "MinIO — 환경 변수 하나(AWS_ENDPOINT_URL_S3)" }
          - { from: "공인 IP", to: "Cloudflare 터널" }
          - { from: "GPU 서버 T4 16GB", to: "RTX 3050 8GB — 추론 서버 없이 GPU 를 차례로" }
      - { type: flow, items: ["백업 하나(비밀 값 · 데이터)", "새로 클론한 저장소", "깨끗한 환경에서 전체 복구"] }
      - type: stats
        items:
          - { num: "약 1분 30초", label: "되살리기(기계 준비물이 있는 상태)" }
      - { type: facts, items: ["첫 HEAD 요청만 403 → 백엔드만 클러스터 안에서 MinIO 에 직결", "화면 개인화는 빌드 때 패치로 — 「팀분석」 화면"] }
      - { type: image, src: "/assets/img/supersub/team.webp", alt: "팀분석 화면 — 팀장·팀원 알약과 포메이션 판", caption: "팀분석 화면 — 팀장이 포메이션 판의 빈 자리를 채운다(시연 데이터)" }
---
