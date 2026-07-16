# 🎸 열대야 :: 260627 연합공연

인디밴드 연합공연 **"열대야"**의 공식 소개 웹페이지입니다.
공연 정보, 라인업, 타임테이블, 오시는 길, 응원(후원) 안내를 한 페이지에 담은 순수 HTML/CSS/JS 랜딩 페이지입니다.

**🔗 Live Site:** https://thimxokeit.github.io/tropical-night/

---

## 📌 공연 정보

| 항목 | 내용 |
|---|---|
| 일시 | 2026.06.27 (SAT) 16:45 OPEN / 17:00 START |
| 장소 | 펄스라이브홀 (서울 서초구 주흥길 12) |
| 입장 | 무료 (Free Entry) |
| 라인업 | holywater, ㅊㅁㄷㅁ, Downdog, 경쟁대응, 예랑도랑 |

---

## ✨ 주요 기능

- **실시간 카운트다운** — 공연 시작까지 남은 시간을 일/시/분/초로 표시하고, 공연 시작 후에는 "🎸 공연 중!", 종료 시각(`concertEndDate`) 이후에는 "🎉 공연 완료!"로 자동 전환
- **밴드 라인업 카드** — 밴드별 이미지, Instagram/YouTube 링크를 데이터 속성(`data-instagram`, `data-youtube`) 기반으로 조건부 렌더링
- **타임테이블 아코디언** — 밴드별 공연 시간을 클릭하면 셋리스트(곡 목록)가 펼쳐지는 인터랙션
- **오시는 길** — Google Maps 임베드 + 네이버맵/카카오맵 바로가기 버튼
- **FAQ 아코디언** — 자주 묻는 질문 토글 UI
- **응원(후원) 섹션** — QR코드 노출 + 클립보드 복사 버튼(`navigator.clipboard`)으로 계좌번호 복사
- **플레이리스트** — YouTube 재생목록 임베드
- **반응형 내비게이션** — 데스크톱 상단 메뉴 + 모바일 햄버거 드로어 메뉴
- **스크롤 리빌 애니메이션** — `IntersectionObserver` 기반으로 섹션 진입 시 페이드인
- **플로팅 응원 버튼** — Hero 섹션을 벗어나면 나타나는 고정 버튼
- **Open Graph / Twitter Card** — 링크 공유 시 썸네일 노출
- **Google Analytics(gtag.js)** 연동

---

## 🛠 기술 스택

- **HTML5 / CSS3 / Vanilla JavaScript** (프레임워크·빌드 도구 없음)
- **Pretendard Variable** — 한글 웹폰트 (CDN)
- **Space Mono** — 카운트다운 등 숫자 표기용 모노스페이스 폰트 (Google Fonts)
- **Google Maps Embed** — 오시는 길 지도
- **YouTube Embed** — 미리듣기 플레이리스트
- **Google Analytics (gtag.js)** — 방문자 트래킹
- **GitHub Pages** — 정적 호스팅

---

## 📁 파일 구조

```
tropical-night/
├── index.html                 # 메인 페이지 (구조 + 인라인 스크립트)
├── style.css                  # 전체 스타일
├── tropical_poster_bg.png     # Hero 배경 이미지
├── tropical_poster_title.png  # 타이틀 로고 이미지
├── tropical_poster_hero.png   # Hero 메인 이미지
├── competition.jpeg           # 밴드 "경쟁대응" 이미지
├── yerangnarang.png           # 밴드 "예랑도랑" 이미지
├── instagram.png              # 밴드 링크 아이콘
├── youtube.png                # 밴드 링크 아이콘
├── qr.png                     # 후원 계좌 QR 코드
└── tropical_night_thumbnail.png  # OG(공유) 썸네일
```

> ⚠️ 위 이미지 파일들은 저장소 루트에 함께 존재해야 페이지가 정상적으로 렌더링됩니다.

---

## 🚀 실행 방법

### 로컬에서 미리보기

별도의 빌드 과정 없이 정적 파일이므로, 아래 중 편한 방법으로 열면 됩니다.

```bash
# 방법 1: 그냥 파일 더블클릭 / 브라우저로 열기
open index.html

# 방법 2: 로컬 서버로 실행 (일부 기능은 로컬 서버 환경을 권장)
npx serve .
# 또는
python3 -m http.server 8000
```

### GitHub Pages 배포

1. `main` 브랜치(또는 배포용 브랜치)에 `index.html`, `style.css`, 이미지 파일들을 푸시
2. 저장소 **Settings → Pages**에서 배포 브랜치를 지정
3. `https://thimxokeit.github.io/tropical-night/` 로 접속 확인

---

## 🔧 커스터마이징 가이드

### 공연 날짜 / 카운트다운 종료 시각 변경

`index.html` 하단 `<script>` 내부의 아래 변수를 수정하세요.

```javascript
const concertDate = new Date('2026-06-27T17:00:00+09:00');   // 공연 시작 시각
const concertEndDate = new Date('2026-06-27T19:00:00+09:00'); // 공연 종료(예상) 시각
```

- `concertDate` 이전 → 남은 시간 카운트다운
- `concertDate` ~ `concertEndDate` 사이 → "🎸 공연 중!"
- `concertEndDate` 이후 → "🎉 공연 완료!"

### 밴드 라인업 추가/수정

`<section id="bands">` 내 `.band-card` 블록을 복사해 추가하고, `data-instagram` / `data-youtube` 속성에 링크를 넣으면 자동으로 아이콘이 노출됩니다(둘 다 없으면 링크 영역이 자동 제거됩니다).

### 타임테이블 / 셋리스트 수정

`<section id="timetable">` 내 `.tt-group` 블록의 `<span class="tt-time">`, `<span class="tt-act">`와 내부 `.setlist-songs` 목록을 수정하세요.

### 후원 계좌 / QR 변경

`support` 섹션의 `qr.png`를 교체하고, 스크립트 내 아래 문자열을 수정하세요.

```javascript
const text = '토스뱅크 1002-2528-3603 예랑나랑';
```

---

## 📄 라이선스

이 프로젝트는 "열대야" 연합공연 홍보를 위해 제작되었습니다. 별도 라이선스 표기가 없다면 소스 재사용 전 제작자에게 문의해주세요.
