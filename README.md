# BULLET TIME

A top-down arena shooter where **the world only moves when your mouse moves**.

Stop your mouse → bullets freeze in mid-air. Move slowly → the world creeps forward. Move fast → full speed. Walk WASD between frozen bullets, reposition, then "play" the world forward when you're ready.

The asymmetry is the game.

## Play

Open `index.html` in a browser. No build step, no dependencies.

Or play it live: **[nekxxy.github.io/bullet](https://nekxxy.github.io/bullet)**

## Controls

| Input | Action |
|---|---|
| `WASD` / arrow keys | Move (real time, always) |
| Mouse movement | Advance world time |

Top-left HUD shows current time scale, mouse velocity, and live bullet count.

## How it works

World time is scaled by smoothed mouse velocity over a 150ms window. The player moves on real time; everything else (bullets, shooter cooldowns) moves on world time. The whole scaling rule lives in one function — `computeTimeScale()` in `index.html` — so it's easy to tune.

Key constants you can tweak at the top of the script:

- `MAX_MOUSE_VEL` — px/sec at which time scale clamps to 1.0
- `SMOOTH_WINDOW_MS` — averaging window for velocity (lower = snappier stops)
- `PLAYER_SPEED`, `BULLET_SPEED`, `SHOOT_INTERVAL` — gameplay feel

## Status

**Day 1 — core mechanic prototype.** Working:

- [x] Mouse-driven world time
- [x] WASD player movement (real time)
- [x] 3 stationary shooters, bullets aimed at player
- [x] Collision detection (logs `HIT` to console)
- [x] Debug HUD

Not yet:

- [ ] Game over / lives
- [ ] Score
- [ ] Waves / progression
- [ ] Menu / restart
- [ ] Sound
- [ ] Visual polish (trails, hit flashes, screen shake)

## Stack

Vanilla HTML5 Canvas. Single file. No frameworks, no build, no assets.

## License

MIT
