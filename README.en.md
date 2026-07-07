# 🍮 jelly-tetris

> Matter.js soft-body physics reimagining of Tetris — blocks wobble, squash, and deform

A reimagining of classic 10×20 Tetris where every block is rendered as a **soft body** mesh of particles wired together with distance constraints. Pieces wobble, squash, and bulge on impact and under load. The standard 7-bag rotation rules (I/O/T/S/Z/J/L), hard-drop, and scoring system are preserved — the satisfaction lives in the physics.

[🇰🇷 한국어](./README.md) · [🇺🇸 English (default)](#)

---

## 🎬 Live Demo

> **👉 [https://jelly-tetris.vercel.app/](https://jelly-tetris.vercel.app/)** — runs in any modern browser at 60fps

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fjelly--tetris-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/jelly-tetris) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-Matter.js%20(CDN)-E10098?style=flat-square) |

### 🎮 Quick Start
1. Click the demo link above to open in your browser
2. **← →** — move left / right
3. **↓ (hold)** — soft drop
4. **↑ / X** — rotate
5. **Space** — hard drop
6. **R** — restart

---

## 🤖 Attribution

This project was generated automatically using the model and prompt below.

| Item | Value |
|---|---|
| **Model** | MiniMax-M3 |
| **Runtime** | OpenCode CLI |
| **Repository** | [`sigco3111/jelly-tetris`](https://github.com/sigco3111/jelly-tetris) |
| **License** | MIT |
| **Dependency** | Matter.js v0.20.0 (CDN, jsDelivr with unpkg fallback) |

### 📝 Prompt used (verbatim)

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

## ✨ Features

- 🍮 **Soft-body blocks** — every tetromino is a particle mesh with internal constraints
- 💧 **Wobble & squash** — impact and stacked weight visibly deform pieces
- 🎯 **Standard 7-bag** — I, O, T, S, Z, J, L rotation rules preserved
- 🧱 **10×20 grid** — classic board dimensions
- ⚡ **Real-time rendering** — traces deformed mesh outlines onto Canvas 2D each frame
- 🎒 **Hold / Next / Preview** — full queue UI on the right panel
- 📊 **Score & level** — line-clear scoring with level-up progression
- 📦 **Single HTML file** — only external dependency is the Matter.js CDN
- 🔒 **On-device** — physics + rendering all run in the browser

---

## 🚀 Quick Start

### Option 1: open the file directly
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

> Some browsers block local file access for security reasons. If that happens, use option 2.

### Option 2: local server (recommended)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### Option 3: live demo (Vercel)
Visit the Live Demo link at the top — no install required.

---

## 🎮 Controls

| Input | Effect |
|---|---|
| **← / →** | move left / right |
| **↓ (hold)** | soft drop (accelerated fall while held) |
| **↑ / X** | rotate (clockwise, SRS-style) |
| **Space** | hard drop (instant drop to floor) |
| **R** | restart (works during play or at game-over) |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Rendering** | HTML5 Canvas 2D Context |
| **Physics** | [Matter.js](https://brm.io/matter-js/) v0.20.0 (CDN) |
| **Soft bodies** | particle meshes + `Constraint` distance joints |
| **Loop** | `Matter.Engine.update` + `requestAnimationFrame` |
| **Dependency** | Matter.js (CDN, jsDelivr → unpkg fallback) |

### Soft-body implementation notes

- Each tetromino = 4 cells × N particles in a mesh layout
- Adjacent particles are wired via `Constraint.create({ stiffness, damping })`
- `Composite.addBody` / `addConstraint` register the piece in the world
- Render path: query particle positions → trace mesh outline → fill to Canvas 2D
- `Sleeping` integration skips simulation cost on settled pieces

---

## 📂 Project structure

```
jelly-tetris/
├── index.html      # single HTML with Matter.js CDN, rendering and input inlined
├── README.md       # Korean (default)
├── README.en.md    # English
└── LICENSE         # MIT
```

---

## 🎨 Design Choices

Four decisions made during brainstorming:

| Decision | Choice | Reason |
|---|---|---|
| **Physics engine** | Matter.js (built-in soft bodies) | stable, well-documented, mesh constraint API ready out of the box |
| **Rendering** | Canvas 2D (mesh-outline fill) | minimal dependencies, fits in a single HTML inline |
| **CDN fallback** | jsDelivr → unpkg sequential fallback | resilient to CDN outages |
| **Game rules** | standard 7-bag on 10×20 board | keep classic feel; variation lives in the physics |

### Customizing

Tune these constants near the top of `index.html` to change the look and feel:

```js
const GRID_W = 10;            // board width in cells
const GRID_H = 20;            // board height in cells
const CELL_SIZE = 30;         // pixels per cell (performance vs visual tradeoff)
const PARTICLE_R = CELL_SIZE * 0.42;  // particle radius
```

To adjust wobble intensity, change the `stiffness` value passed to `Constraint.create`. **Lower values = more jelly**.

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

This project uses the open-source physics engine [Matter.js](https://brm.io/matter-js/). Core capabilities — soft bodies, distance constraints, sleeping — are built on the Matter.js team's research.

Generation pipeline: [MiniMax-M3](https://example.com) model + OpenCode CLI. Prompt engineering and design choices made by the repository owner.

- **Coding mission reference**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
