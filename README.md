# 🍮 jelly-tetris

> Matter.js 소프트 바디 물리 기반 젤리 테트리스 — 블록이 출렁이고 찌그러집니다

고전 10×20 테트리스를 재해석한 프로젝트입니다. 모든 블록은 파티클 메시 + 거리 제약(`Constraint`)으로 이루어진 **소프트 바디**로 렌더링되어, 착지·적층·라인 클리어 시점이 출렁이고 찌그러집니다. 표준 7-bag (I/O/T/S/Z/J/L) 회전·하드드롭·점수 시스템을 그대로 유지하면서 시각·물리 만족감을 극대화한 1인 데모입니다.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](./README.en.md)

---

## 🎬 라이브 데모

> **👉 [https://jelly-tetris.vercel.app/](https://jelly-tetris.vercel.app/)** — 브라우저에서 바로 실행 (60fps)

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fjelly--tetris-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/jelly-tetris) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-Matter.js%20(CDN)-E10098?style=flat-square) |

### 🎮 빠른 사용법
1. 위 데모 링크 클릭 → 브라우저에서 페이지 열기
2. **← →** — 좌우 이동
3. **↓ (홀드)** — 소프트드롭
4. **↑ / X** — 회전
5. **Space** — 하드드롭
6. **R** — 재시작

---

## 🤖 생성 정보

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**되었습니다.

| 항목 | 값 |
|---|---|
| **모델** | MiniMax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/jelly-tetris`](https://github.com/sigco3111/jelly-tetris) |
| **라이선스** | MIT |
| **의존성** | Matter.js v0.20.0 (CDN, jsDelivr, unpkg 폴백) |

### 📝 사용된 프롬프트 (원문)

```
고전 테트리스 게임을 재해석하여 블록들이 딱딱하지 않고 젤리처럼 출렁거리는
소프트 바디(Soft Body) 물리학을 적용하고, 블록이 바닥에 떨어져 쌓일 때마다
찌그러지며 서로의 무게에 눌려 형태가 변형되는 물리 엔진 기반의 퍼즐 게임을
만들어줘.
Implementation Advice: Use Matter.js. It has built-in support for
"soft bodies" (mesh constrained bodies). You will need to map the
Tetris shapes to these soft body structures. Rendering can be done via
Canvas or p5.js. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.
```

---

## ✨ 주요 특징

- 🍮 **소프트 바디 블록** — 모든 테트로미노가 파티클 + 거리 제약 기반 메시
- 💧 **출렁임 & 찌그러짐** — 착지·적층 시 하단 블록이 무게에 눌려 변형
- 🎯 **표준 7-bag** — I, O, T, S, Z, J, L 회전 규칙 그대로
- 🧱 **10×20 그리드** — 클래식 보드 크기 유지
- ⚡ **실시간 렌더링** — 매 프레임 메시 윤곽을 추적해 Canvas 2D로 채움
- 🎒 **Hold / Next / Preview** — 다음·홀드 큐 표시 UI 포함
- 📊 **점수 & 레벨** — 라인 클리어 점수 + 레벨업 시스템
- 📦 **단일 HTML** — 외부 의존성은 Matter.js CDN만 사용
- 🔒 **온디바이스** — 모든 물리·렌더링이 브라우저 안에서 처리

---

## 🚀 실행 방법

### 방법 1: 그냥 브라우저로 열기 (가장 간단)
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

> 브라우저 보안 정책상 일부 브라우저에서는 로컬 파일 직접 열기가 안 될 수 있어요. 그 경우 방법 2를 권장합니다.

### 방법 2: 로컬 서버 (권장)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### 방법 3: 라이브 데모 (Vercel)
배포 후 위 라이브 데모 링크에서 바로 확인 가능합니다.

---

## 🎮 조작법

| 입력 | 효과 |
|---|---|
| **← / →** | 좌우 이동 |
| **↓ (홀드)** | 소프트드롭 (누르고 있으면 가속 낙하) |
| **↑ / X** | 회전 (SRS 스타일 시계 방향) |
| **Space** | 하드드롭 (즉시 바닥까지) |
| **R** | 게임오버 시 / 진행 중 재시작 |

---

## 🛠️ 기술 스택

| 영역 | 사용 기술 |
|---|---|
| **렌더링** | HTML5 Canvas 2D Context |
| **물리 엔진** | [Matter.js](https://brm.io/matter-js/) v0.20.0 (CDN) |
| **소프트 바디** | 파티클 메시 + `Constraint` 거리 제약 |
| **루프** | `Matter.Engine.update` + `requestAnimationFrame` |
| **의존성** | Matter.js (CDN, jsDelivr → unpkg 폴백) |

### Matter.js 소프트 바디 구현 요약

- 각 테트로미노 = 4셀 × N 파티클의 메쉬
- 인접 파티클을 `Constraint.create({ stiffness, damping })` 로 와이어업
- `Composite.addBody / addConstraint` 로 월드에 등록
- 렌더 패스: 파티클 좌표 질의 → 메시 외곽 채움 → Canvas 2D에 그리기
- 정지 상태(`Sleeping`) 도달 시 시뮬레이션 비용 절감

---

## 📂 프로젝트 구조

```
jelly-tetris/
├── index.html      # 단일 HTML (Matter.js CDN + 렌더링 + 입력 모두 인라인)
├── README.md       # 한국어 (기본)
├── README.en.md    # English
└── LICENSE         # MIT
```

---

## 🎨 디자인 결정

브레인스토밍 단계에서 내린 결정 4가지:

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **물리 엔진** | Matter.js (소프트 바디 내장) | 자체 충돌 엔진 대비 검증·안정성, 메시 제약 API 즉시 사용 |
| **렌더링** | Canvas 2D (메시 윤곽 채움) | p5.js 대비 의존성 최소화, 단일 HTML에 인라인 가능 |
| **CDN 폴백** | jsDelivr → unpkg 순차 시도 | 네트워크 차단·장애에서도 로드 보장 |
| **게임 규칙** | 표준 7-bag + 10×20 | 클래식 직관 유지, 변형은 물리만 |

### 직접 커스터마이즈하고 싶다면

`index.html` 상단에서 다음 상수를 조정하면 분위기를 바꿀 수 있어요:

```js
const GRID_W = 10;            // 보드 가로 셀
const GRID_H = 20;            // 보드 세로 셀
const CELL_SIZE = 30;         // 1셀 픽셀 크기 (성능·시각 트레이드오프)
const PARTICLE_R = CELL_SIZE * 0.42;  // 파티클 반경
```

소프트 바디 강도(찌그러짐 정도)를 조절하려면 `Constraint.create({ stiffness, damping })` 의 `stiffness` 값을 바꾸면 됩니다. **값을 낮출수록** 더 출렁이고 찌그러져요.

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 [Matter.js](https://brm.io/matter-js/) 오픈소스 물리 엔진을 사용합니다. 소프트 바디·거리 제약·수면 처리 등 핵심 기능은 Matter.js 팀의 연구에 기반합니다.

생성 파이프라인: [MiniMax-M3](https://example.com) 모델 + OpenCode CLI 환경. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행했습니다.

- **코딩미션 참조 페이지**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
