# Neon Snake

A modern, single-file Snake game with a cyberpunk/neon aesthetic, built with vanilla HTML5 Canvas, CSS3, and JavaScript. No frameworks, build step, external libraries, images, or sound files.

## Play

No build step is required. Open [`snake.html`](./snake.html) directly in a browser, or serve the folder locally:

```bash
# Option 1 — open directly
xdg-open snake.html

# Option 2 — local server (recommended)
python3 -m http.server 8000
# then visit http://localhost:8000/snake.html
```

> Sound starts after the first click or key press, as required by browser autoplay policies.

## Features

- **20×20 grid** rendered on HTML5 Canvas at 60 FPS with `requestAnimationFrame`
- **Smooth movement** — fixed-step logic with interpolated rendering between cells
- **Input buffer** — rapid key presses are queued and validated so the snake can never reverse into itself
- **Three difficulty modes** with different speeds and obstacles
- **Food and power-ups** — standard food, plus a timed golden apple with a 2× score multiplier
- **Particles, score popups, and screen shake** for game feel
- **Procedural arcade audio** synthesized with the Web Audio API, including a persisted mute toggle
- **Glassmorphism overlays** for Start, Paused, and Game Over screens
- **Persistent high scores** per difficulty via `localStorage`
- **Fully responsive** — keyboard, swipe, and an on-screen D-pad; no page scrolling

## Controls

| Action | Input |
| --- | --- |
| Move | Arrow keys or `W` `A` `S` `D` |
| Move (mobile) | Swipe on the board or use the D-pad |
| Pause / Resume | `Space` or `P` |
| Mute / Unmute | `M` |
| Start / Restart | `Enter` |

## Difficulty modes

| Mode | Tick speed | Notes |
| --- | --- | --- |
| Easy | 190 ms | Slow and steady |
| Medium | 140 ms → 70 ms | Speeds up as the score grows |
| Hard | 95 ms | Fast, with 10 obstacle blocks |

## Scoring

| Item | Points | Effect |
| --- | --- | --- |
| Standard food | +10 | Grows the snake by one segment |
| Golden apple | +50 | Grants a 2× score multiplier for 8 seconds |

The golden apple has a countdown ring and bar. Food and bonuses never spawn on the snake, obstacles, or each other.

## Tech stack

- HTML5 Canvas 2D
- CSS3 (custom properties, grid/flex layout, glassmorphism, responsive media queries)
- Vanilla JavaScript (ES2022)
- Web Audio API for synthesized sound effects
- `localStorage` for high scores and mute state

## Project structure

```
.
├── index.html   # Tic-Tac-Toe game
├── snake.html   # Neon Snake (self-contained game)
└── README.md
```

`snake.html` contains all of its HTML, CSS, and JavaScript inline.

## Notes

- High scores are stored per difficulty under the `neonSnake.best.v1` key.
- The game respects `prefers-reduced-motion` by disabling screen shake.
- The layout adapts from small phones to desktop, including short landscape viewports, without scrollbars.
