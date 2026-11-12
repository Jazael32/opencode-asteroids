# AGENTS.md

Vanilla JS arcade game (Asteroids). No framework, no bundler, no dependencies — there is no `package.json`, no build, no lint, no tests. Don't invent tooling; verify changes by running the game.

## Run / verify

- Open `index.html` directly in a browser, or `npx serve .` → http://localhost:3000.
- Verification is manual: open the game and play. There are no automated tests to run.

## Architecture

- Everything lives in a single file `game.js` (~360 lines), loaded by `index.html` as a **plain classic script** (not an ES module). It uses top-level globals: `canvas`/`ctx`, constants `W`/`H`, `keys`/`justPressed`, classes `Bullet`/`Asteroid`/`Ship`/`Particle`, and game-state globals (`ship`, `asteroids`, `state`, `score`, `lives`, `level`). Keep this structure — don't introduce modules or imports.
- `index.html` hardcodes the canvas at `width="800" height="600"`, matching `const W = 800; const H = 600;` in `game.js`. **If you change the game size, update both files.**
- Single-press keys (e.g. shooting) are detected via the `justPressed` object + `pressed(code)` helper, cleared at end of `update(dt)` — reuse this pattern instead of `keys` for one-shot actions.

## Conventions

- Spanish throughout: README, UI text, comments. Match this in new strings and comments.
- Sizes and points are size-indexed tables: `SPEEDS = [0, 85, 55, 32]`, `POINTS = [0, 100, 50, 20]` (index 3 = large … 1 = small). Changing gameplay balance means editing these arrays, not per-class literals.
