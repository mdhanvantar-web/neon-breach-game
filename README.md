# NEON BREACH

A fast 3D arena shooter that runs in the browser. No build step, no install, no
dependencies to fetch — open `index.html` and play.

Survive escalating waves of hostile drones in a neon arena. Pick them apart with
the pulse carbine; aim for the glowing core for critical hits.

![Neon Breach](logo-wordmark.png)

## Play

Open `index.html` in a modern desktop browser (Chrome, Edge, Firefox, Safari).
Everything runs locally, including the 3D engine — it plays offline.

### Live

| Host | URL |
| --- | --- |
| Vercel | https://neon-breach-game-three.vercel.app |
| GitHub Pages | https://mdhanvantar-web.github.io/neon-breach-game/ |
| Source | https://github.com/mdhanvantar-web/neon-breach-game |

## Controls

| Input | Action |
| --- | --- |
| `W` `A` `S` `D` | Move |
| Mouse | Look |
| Left click | Fire |
| Right click | Focus aim (zoom + tighter spread) |
| `Shift` | Sprint |
| `Space` | Jump |
| `R` | Reload |
| `Esc` or `P` | Pause |

**Desktop only.** The game requires a mouse and keyboard (pointer lock), so it
does not work on phones or tablets.

## Scoring

- Base kill: 100, **core hit: 180**, brutes are worth 1.8x
- Consecutive kills build a killstreak multiplier, up to **x3.25**
- New personal bests are stored in `localStorage`

## How it works

Everything is hand-written vanilla JavaScript using the three.js WebGL renderer:

- `index.html` contains the markup, HUD styling, and the entire game
- `vendor/three.min.js` — three.js r128, bundled so there is no CDN dependency
- Geometry, arena layout, and all textures are generated procedurally at load
  (canvas-drawn floor grid and wall panels); there are no binary assets beyond
  the logo
- Enemies, projectiles, tracers, and impact debris are pooled and recycled
- Lighting is budgeted to 8 real-time lights (1 hemisphere, 1 ambient, 1
  directional with shadows, 2 fills, 1 muzzle, 3 pooled explosion lights);
  everything else uses emissive materials and additive sprites
- Player collision resolves against axis-aligned obstacle boxes

## Project layout

```
index.html            the game (markup + styles + all game code)
logo.svg              emblem, vector
logo.png              emblem, 1024x1024
logo-256.png          emblem, 256x256
logo-wordmark.svg     emblem + title lockup
logo-wordmark.png     emblem + title lockup, 2400x800
vendor/three.min.js   three.js r128 (MIT, see vendor/THREE-LICENSE.txt)
```

## Credits

Game code and artwork are original. Bundled third-party software:

- [three.js](https://threejs.org/) r128 — MIT License — © 2010-2021 three.js authors

## License

MIT — see [LICENSE](LICENSE).
