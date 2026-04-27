# BULLET TIME

**Superhot in 2D, controlled by mouse velocity.** Time only advances when you move your mouse. Stop → bullets freeze. Walk WASD between them, pre-aim, then flick the mouse to "play" the world forward.

🎮 **Live:** https://nekxxy.github.io/bullet/

Built for **Cursor Vibe Jam 2026**.

## Controls

- **WASD / arrows** — move (real time, always)
- **Mouse movement** — advance world time
- **Left click** — fire (cycle 2+)
- **R** — restart on death
- **M** — mute audio
- **`** — debug overlay

## Scoring

`kills × 100 + survival_seconds × 5 + near_misses × 10`

A "near miss" is an enemy bullet passing within 30px of you without hitting.

## Stack

Vanilla HTML5 Canvas + Web Audio. Single `index.html`. No build step, no npm, no bundler. Procedural everything.

## License

MIT
