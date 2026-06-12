# HTML VAULT — 작업 로그

---

## 2026-06-12

### 공통 Navbar 디자인 확정

**작업자**: Claude (claude-sonnet-4-6)

**변경 파일**
- `pages/_navbar-preview.html` — 신규 생성 (navbar 초안 미리보기용)
- `CLAUDE.md` — 신규 생성 (프로젝트 작업 지침)
- `LOG.md` — 신규 생성 (이 파일)
- `HANDOFF.md` — 신규 생성 (현황 및 인수인계)

**결정 사항**
- `weather_dashboard.html`의 `home-btn`과 `israel-kings-timeline.html`의 `home-btn` 디자인이 서로 달라 통일 필요성 확인
- 라이트형(A형) / 다크형(B형) 두 가지 navbar 변형 확정
- 디자인 방향: 배경 없는 텍스트 버튼, `text-shadow` 만 사용, 대문자 `HOME / TOP / BOTTOM`, `letter-spacing: .08em`
- 로고 이모지·아이콘 없이 `HTML VAULT` 텍스트만 (VAULT는 accent 색상)
- 버튼 구분선: 1px 세로 `vsep`

**미적용 항목** (다음 작업 시 진행)
- `weather_dashboard.html` — 라이트형 navbar 실제 적용, 기존 `.home-btn` 제거
- `israel-kings-timeline.html` — 다크형 navbar 실제 적용, 기존 `.home-btn` 제거

---

## 2026-06-12 (8)

### weather_dashboard — 강수 배경색 다크 톤다운

**변경 파일**
- `pages/life/weather_dashboard.html`

**변경 내용**
- `rainBg()` 반환값 전체 교체: 밝은 파란색 → 어두운 네이비 계열
  - 약한 비(1–5mm): `#dbeafe` → `#0a1c33`
  - 보통 비(5–15mm): `#93c5fd` → `#0b2847`
  - 강한 비(15mm+): `#3b82f6` → `#0d3464`
- `dark` 플래그: 강한 비 한정 → 강수 있는 모든 셀로 확장 (어두운 배경에서 텍스트 가독성 유지)
- 오전/오후 슬롯 내 비 강조색 조건 동일하게 확장
- 범례 스와치 3종 및 오후 스와치 색상 일치 업데이트
- 오전/오후 슬롯 배경 opacity: `0.1` → `0.07` (더 은은하게)

---

## 2026-06-12 (7)

### weather_dashboard — JS/HTML 인라인 컬러 다크 테마 완료

**변경 파일**
- `pages/life/weather_dashboard.html` — `makeCellHtml()` 및 HTML 인라인 컬러 전체 교체

**변경 내용**
- 온도 구분 슬래시 `/`: `#d1d1d6` → `#494949`
- 강수 확률%, 풍속 텍스트: `#8e8e93` → `#7D7D7D`
- 강수량 텍스트 (비-dark 셀): `#1a56db` → `#93c5fd`
- 범례 스와치 배경: `#f5f5f7`→`#181818`, `#f0f7ff`→`#0d1b2a`, `#f5f3ff`→`#1a0d2e`
- 범례 스와치 테두리: `#d1d1d6` → `#494949`
- 필터 패널 모드 라벨 (무료/크레딧 필요): `#8e8e93` → `#7D7D7D`
- modeDesc 텍스트, apiSaveStatus: `#8e8e93` → `#7D7D7D`
- JS `desc.style.color`: `#8e8e93` → `#7D7D7D`
- 예보 범위 초과 셀: `#8e8e93` → `#7D7D7D`
- 최근 검색 라벨: `#8e8e93` → `#7D7D7D`

---

## 2026-06-12 (6)

### 페이지 전체 디자인 — DESIGN_Lamborghini.md 기준 재설계

**변경 파일**
- `pages/life/weather_dashboard.html` — CSS 전체 교체, 차트 grid/tick 색상 업데이트
- `pages/bible/summary/israel-kings-timeline.html` — CSS 전체 교체

**공통 적용 사항**
- body background `#000` (Absolute Black)
- 패널 `#181818`, 카드 `#202020`, 구분선 `#313131`
- 모든 border-radius 0px
- 액센트 `#007aff` → `#FFC000` (Lamborghini Gold)
- 버튼 `.btn-primary`: gold/black, 슬라이더·스피너·프로그레스도 gold
- 상태바/테이블 헤더: dark 버전으로 전환
- 반응형 미디어쿼리 추가 (≤768px, ≤600px)
- JavaScript 무변경

**israel-kings-timeline 특이 사항**
- 왕 등급 g0~g4: 어두운 dark 버전 (green/blue/orange/red/purple)
- kbar.sel: Lamborghini Gold glow `rgba(255,192,0,.5)`
- 상세 패널 dark 스타일 전체 적용

---

## 2026-06-12 (5)

### 기존 페이지 navbar 적용

**변경 파일**
- `pages/life/weather_dashboard.html` — vault-nav 삽입, 기존 `.home-btn` 제거, `.filter-panel` top `0→44px`
- `pages/bible/summary/israel-kings-timeline.html` — vault-nav 삽입, 기존 `.home-btn` 제거

**특이 사항**
- `israel-kings-timeline.html`: body가 `height:100dvh;overflow:hidden` flex 구조이므로 vault-nav를 `position:relative;flex-shrink:0`로 설정, TOP/BOTTOM 버튼은 `#sarea` 내부 스크롤 대상으로 커스텀 처리

---

## 2026-06-12 (4)

### Navbar 디자인 최종 확정 — DESIGN_Lamborghini.md 기준

**변경 파일**
- `pages/_navbar-preview.html` — Lamborghini 디자인 시스템으로 전면 재설계
- `CLAUDE.md` — navbar 코드 최종 버전으로 교체 (A형/B형 2종 → 단일 통합)

**확정 사항**
- 라이트/다크 2종 navbar → **단일 블랙 navbar** 통합 (`#000000`)
- 높이: 56px → **44px** (모바일 40px)
- 로고 accent: `#FFC000` (Lamborghini Gold)
- 버튼: `#7D7D7D` 기본 / `#FFC000` hover, 대문자, `letter-spacing:.12em`
- 구분선: `#202020`, border-radius: 0px

---

## 2026-06-12 (3)

### 폴더 구조 정리

**변경 파일**
- `pages/sample-1.html` — 삭제
- `pages/sample-2.html` — 삭제
- `pages/sample-3.html` — 삭제

**결정 사항**
- `bible/summary/` depth 유지 — 향후 `bible/maps/`, `bible/prophecy/` 등 추가 예정
- `pages/pwa_generator.html` — 정리 방향 미결 (추후 결정)

---

## 2026-06-12 (2)

### index.html 리뉴얼 — DESIGN_Lamborghini.md 기준 적용

**변경 파일**
- `index.html` — 전면 리뉴얼

**적용 내용**
- 배경: `#0d1117` → Absolute Black `#000000`
- 타이틀: `HTML VAULT` 대문자, `clamp(36px,6vw,64px)`, VAULT는 Lamborghini Gold `#FFC000`
- 서브타이틀: 11px 대문자, `#7D7D7D`, `letter-spacing:.14em`
- 카드: `#181818` 배경, 좌측 2px 골드 border hover accent, 0px border-radius
- 아이템 레이블: `Folder` / `HTML` 소구분 + 파일명 bold
- 화살표: `→` 기본 `#313131`, hover `#FFC000`
- `_`로 시작하는 파일·폴더 목록에서 자동 제외

---
