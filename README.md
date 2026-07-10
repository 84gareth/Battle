# Endless Saga — Battle Square

A single-file, HD-2D roguelike battle arena inspired by the Gold Saucer Battle Square in *Final Fantasy VII*.
One fighter, eight battles, then Endless Mode. Between fights the **handicap reels** deal you three
risk/reward wagers — luck sets the table, you choose how to play the hand.

Built with plain HTML5 Canvas + Web Audio. No build step, no dependencies, no framework.

## Play

Just open `index.html` in a browser, or visit the hosted version once Pages is live.

Controls: **↑ ↓** move · **Enter / Z** confirm · **Esc / X** back — or simply tap. Landscape only.

## Deploy to GitHub Pages

This is a static site — nothing to build.

**Own repo:**
1. Push these files to the repo root (`index.html`, `manifest.json`, `sw.js`, `icon.svg`,
   `icon-192.png`, `icon-512.png`, `icon-180.png`, `preview.png`).
2. Repo **Settings → Pages → Build and deployment → Deploy from a branch**, pick `main` / `root`.
3. Live at `https://<user>.github.io/<repo>/`.

**Subfolder of an existing games repo:**
- Drop the whole folder in (e.g. `/battle-square/`). It's self-contained and uses relative paths,
  so it works at `https://<user>.github.io/<repo>/battle-square/`.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The entire game (markup, CSS, JS). |
| `manifest.json` | PWA metadata — installable, landscape, fullscreen. |
| `sw.js` | Service worker — offline play + caching. |
| `icon.svg` / `icon-*.png` | App icons (SVG + raster fallbacks for iOS/Android). |
| `preview.png` | Open Graph / social share image (1200×630). |

## Notes

- **High scores** persist via `localStorage` under the key `endlessSaga.battleSquare.highscores`
  (per-browser, per-origin).
- **Offline:** after the first online load the service worker caches the shell and fonts, so it runs
  offline and can be added to a home screen. When you ship a new build, bump `CACHE` in `sw.js`
  (e.g. `endless-saga-v2`) so clients pull the update.
- **Fonts** load from Google Fonts. To run fully offline from the very first visit, self-host the two
  woff2 files and replace the `<link>` in `index.html`.
