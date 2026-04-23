# Mochi

A kawaii jumping game built by Rae (age 9) with Claude, on Bring Your Child to Work Day.

## How to run it

Open `mochi.html` in any browser. That's it. Everything is self-contained in one file — no build step, no dependencies to install. Progress (bells, wallpapers, animals, difficulty) auto-saves to browser localStorage.

## What's in it

**Gameplay**
- A bunny with an umbrella hops on cookie platforms that scroll from right to left
- Tap anywhere on the game area to hop
- 3 hearts per game; fall off a cookie and lose one
- Lose-a-life menu with Continue + Shop (not an auto-countdown — Rae made that call)
- Checkpoint-style pause: resuming puts you back at the start of your current platform
- 3 difficulty modes (Easy / Normal / Hard) that change cookie scroll speed

**Progression**
- Collect bells during play (both floating mid-air bells to jump for, and roll-over bells at platform level)
- Bell counter in the HUD wiggles on collection (game-feel juice)
- Persistent bell currency across sessions

**Shop (tabbed)**
- **Wallpapers tab**: 10 backgrounds from free (Peach Dreams) to 30 bells (Starry Night). Several have emoji accent patterns (🌸, 🍓, 🥭, ⭐, 🫐, 🍎).
- **Animals tab**: 10 playable characters from free (🐰 Bunny) to 30 bells (🐲 Dragon).
- Purchases are permanent (survive death, app close, and localStorage)
- "Equipped" state clearly shown with border highlight + "Using ✓" label

**Design system**
- Peach + cream palette throughout (`#FFF5E6`, `#F5C4B3`, `#F0997B`, `#D85A30`, `#712B13`)
- Mochiy Pop One is the "logo font" — used ONLY for the Mochi wordmark so it stays special
- Fredoka is the "header font" — used for screen titles like "Ready, Rae?", "Shop", "Oh no!"
- System sans-serif for body + UI
- True-centered logo via grid layout (`1fr auto 1fr`)

## Key design decisions Rae made

- Solid continuous warm-up row of cookies at the start of each run (no gaps)
- Bells randomized between "low — grab while rolling" and "high — jump for it"
- Post-warmup platforms are 5 cookies wide with a fixed 50px gap between them
- Shop prices scale from 3 bells (Cotton Candy / Puppy) to 30 bells (Starry Night / Dragon)
- Pause button lives INSIDE the game stage, not outside

## Ideas for what to build next

**Quick wins (15–30 min each):**
1. **Sound effects** — a soft chime on bell collection, a "boop" on jump, a fanfare on wallpaper unlock. Use the Web Audio API.
2. **A stats screen** — total bells ever earned, games played, highest single-round score, favorite animal (most-used)
3. **More wallpapers / animals** — Rae will probably have lots of ideas here
4. **A "reset save" button** in the shop for when things get cluttered

**Medium lifts:**
5. **PWA manifest + service worker** — makes Mochi installable as a real app on Rae's iPad home screen. Custom icon, splash screen, works offline.
6. **Achievements** — "Collect your first bell", "Own all animals", "Beat Hard mode without losing a heart". Little toast notifications when unlocked.
7. **Daily login bonus** — 1 free bell for opening the app on a new day
8. **Round 3 content** — the cat dress-up game or the selfie-to-animal-twin feature from Rae's original ideas

**Bigger ambitions:**
9. **Deploy to the web** — GitHub Pages or Netlify, so Rae has a shareable URL for friends and family
10. **Leaderboard** — highest bell count in a single round, shared with friends
11. **Seasonal events** — a Halloween skin for October, a winter skin in December

## Code structure notes for future refactoring

Everything is currently in one file for portability. When Rae wants to add a LOT of features, consider splitting into:

```
mochi/
├── index.html
├── css/
│   └── styles.css
├── js/
│   ├── game.js       (canvas loop, physics, cookie spawning)
│   ├── shop.js       (wallpaper/animal definitions + rendering)
│   ├── state.js      (localStorage save/load)
│   └── ui.js         (overlay management, buttons)
└── assets/
    └── (sounds, icons, etc.)
```

CSS class prefix is currently `kp-` (a holdover from the original "Kawaii Peach" working title). A rename to `mo-` or `mochi-` at some point would be cleaner.

## Building with Claude Code

A natural next prompt to Claude Code:

> "Read mochi.html and add a sounds system — a short chime when a bell is collected, a soft boop on jump, and a little fanfare when a wallpaper is unlocked. Use the Web Audio API and keep everything in one file for now. Don't change any other game mechanics."

Claude Code is great at these kinds of additive, focused changes.
