# portfolio_sowon_2026 프로젝트 규칙

공통 코드 스타일은 `~/.claude/CLAUDE.md`를 따르고, 이 파일에는 이 프로젝트가 실제로 쓰는 방식과 값을 적는다. 이 프로젝트의 기존 방식을 우선하고, 다른 프로젝트 방식으로 바꾸거나 기존 코드를 옮기지 않는다.

## 이 프로젝트가 쓰는 방식
- 단위: rem 중심 (rem 1016곳, px 104곳, vw 63곳, vh 28곳). `html, body { font-size: 62.5% }`라서 1rem = 10px, 1440px 이하에서는 50%
- 미디어쿼리: 섹션마다 흩어져 있고 파일 끝(`/* 반응형 */`)에도 있음. 형식은 `@media (max-width: 1100px)` / `@media (min-width: 1101px)`처럼 `screen and` 없이 쓰고, 일부는 min-width(PC 전용)
- 클래스 이름: 기본은 snake_case + kebab-case(`main_visual`, `text_box`, `section-01`), 최근 추가한 영역(배너, 실무, 개인프로젝트 등)은 BEM(`banner__stage`, `feature__img`, `work__tabs--named`)
- JS 시작 방식: `index.html` `<head>` 인라인 스크립트를 `$(function () { ... })` 안에 작성하고, 일부 기능은 문서 끝에 `(function () { ... })();` 블록으로 분리. 랜야드 효과만 `js/lanyard.js`(three.js 모듈)
- CSS 들여쓰기는 2칸 (예전 SCSS를 컴파일한 형태). 선택자는 HTML 계층을 이어 쓰는 방식

## 폴더 구조
- `index.html` 한 페이지, 스크립트는 `<head>` 인라인 + 문서 끝 IIFE 블록 + `js/lanyard.js`
- `css/` : `reset.css` → `common.css` → `main.css`, 추가로 `effects.css`, `projects.css` (index.html에서 `<link>`로 각각 불러오고 `?v=날짜` 캐시 버스터를 붙임)
- `img/` : 사용 이미지·PDF 전부, `lib/` : GSAP 플러그인(ScrollToPlugin, ScrollTrigger, SplitText), jquery, jquery-ui
- 예전에 SCSS(`main.scss`, 중첩 문법)로 작성했다가 제거했고, 지금은 CSS만 쓴다.

## 브레이크포인트
1440 / 1101(1100) / 1024 / 900 / 760 / 400px
- PC·모바일 경계는 1100px 근처 (`min-width: 1101px` / `max-width: 1100px`)
- `body { min-width: 1400px }`

## 색상
- 배경 `#D9CFFF`, 포인트 보라 `--deep: #3B2A7A`, 메인 비주얼 그라데이션 `#B6D3FF` → `#D9CFFF`
- 자주 쓰는 색: `#F1FFC0`, `#11004E`, `#2F74FF`, `#0284C7`

## 폰트
- 본문 `Paperozi`(500/700), 헤더 `Cafe24MeongiWhite`, 장식 `OgRenaissanceSecret`, `dancingscript`
- Google Fonts: Manrope, Nunito, Playfair Display

## 쓰는 라이브러리
- jQuery 3.7.1, AOS 2.3.4, Lenis 1.0.27(스무스 스크롤), GSAP 3.12.3 + ScrollTrigger + SplitText, three.js(lanyard.js)
