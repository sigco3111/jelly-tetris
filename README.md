# Jelly Tetris

A re-imagined classic Tetris where the blocks are not rigid — they **wobble, squish, and deform** like jelly. Built with **Matter.js** soft-body physics: each Tetromino is rendered as a constrained mesh of particles, and pieces settle, squash, and bulge under their own weight.

## Overview

Standard 7-piece Tetris on a 10×20 grid, but every block is a soft body made of particles wired together with constraints. When a piece lands, it deforms against the floor and against pieces below it. Stacked weight visibly compresses lower pieces. Lines still clear the same way — but the satisfying thuds and jiggles are different.

## Features

- **Matter.js soft bodies** — each tetromino rendered as a particle mesh with internal constraints
- **Squash & bulge** — pieces visibly deform on impact and under load
- **Standard 7-bag Tetris** — I, O, T, S, Z, J, L rotation rules
- **Single HTML file** — Matter.js (CDN) + rendering + input all inlined
- **Canvas 2D** rendering — fills traced from the deformed mesh each frame

## Tech Notes

- Matter.js `Bodies.fromVertices` + custom constraint meshes for soft bodies
- Each tetromino = 4 cells × N particles each, wired with distance + stiffness constraints
- Render path: query particle positions → triangulate / fill → draw to Canvas
- Game loop reuses Matter's `Engine.update` for physics; rendering on `requestAnimationFrame`

## Attribution

This project was generated using **OpenCode** with the **MiniMax M3** model (provider: `minimax`, model id: `MiniMax-M3`).

The exact prompt used:

> 고전 테트리스 게임을 재해석하여 블록들이 딱딱하지 않고 젤리처럼 출렁거리는 소프트 바디(Soft Body) 물리학을 적용하고, 블록이 바닥에 떨어져 쌓일 때마다 찌그러지며 서로의 무게에 눌려 형태가 변형되는 물리 엔진 기반의 퍼즐 게임을 만들어줘.
>
> Implementation Advice: Use Matter.js. It has built-in support for "soft bodies" (mesh constrained bodies). You will need to map the Tetris shapes to these soft body structures. Rendering can be done via Canvas or p5.js. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.

## Usage

```bash
# Just open it
open index.html

# Or serve locally
python3 -m http.server 8000
# then visit http://localhost:8000
```

## License

MIT