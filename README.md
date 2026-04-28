# BULLET TIME

**Superhot in 2D, controlled by mouse velocity.** Time only advances when you move your mouse. Stop → bullets freeze. Walk WASD between them, pre-aim, then flick the mouse to "play" the world forward.

🎮 **Live:** https://nekxxy.github.io/bullet/

Built for **Cursor Vibe Jam 2026** → https://vibejam.cc/2026/

## Controls

- **WASD / arrows** — move (real time, always)
- **Mouse movement** — advance world time
- **Left click** — fire
- **R** — restart on death
- **M** — mute audio
- **`** — debug overlay (hitboxes + curve graph)

## Scoring

`kills × 100 + survival_seconds × 5 + near_misses × 10`

A near-miss is an enemy bullet passing within 30px of you without hitting.

## Set up your own leaderboard (optional)

The game works fully without a backend — it falls back to a localStorage-only personal high score. To enable a real online leaderboard:

1. Create a free Supabase project.
2. Run this SQL in the Supabase SQL editor:

```sql
create table bullet_time_scores (
  id bigserial primary key,
  initials text not null,
  score int not null,
  wave_reached int not null,
  created_at timestamptz not null default now()
);

alter table bullet_time_scores enable row level security;

create policy "anyone can read"
  on bullet_time_scores for select
  using (true);

create policy "anyone can insert"
  on bullet_time_scores for insert
  with check (
    char_length(initials) = 3
    and score >= 0
    and score < 10000000
  );
```

3. Copy `config.example.js` → `config.js` and fill in your project URL and anon key.
4. Refresh the page.

`config.js` is gitignored. Never commit it.

## Stack

Vanilla HTML5 Canvas + Web Audio. Single `index.html`. No build step, no npm, no bundler. Procedural everything.

## AI tools used

Vibe-coded with Claude.

## License

MIT
