# bgkit

Copy-paste animated backgrounds for any webpage. No npm install, no build step, no framework — just an `<iframe>` pointed at a hosted HTML file.

**[Browse the gallery →](https://kartik13-op.github.io/bgkit/)**

## How it works

Each background lives as one self-contained `.html` file in `/backgrounds`, with its own inline `<style>` and `<script>`. Host the repo on GitHub Pages, then embed any background like this:

```html
<iframe
  src="https://kartik13-op.github.io/bgkit/backgrounds/aurora-mesh.html?color1=%236E56CF&color2=%23E0577B&text=Hello"
  style="position:fixed;inset:0;width:100%;height:100%;border:0;z-index:-1;"
  loading="lazy"
  title="background"
></iframe>
```

Put your real page content in normal HTML on top — the iframe sits at `z-index:-1` behind everything.

Every background is customizable through URL query params (colors, speed, density, optional hero text). Open `index.html` for a live gallery where you can drag sliders and copy the exact embed URL.

## Backgrounds

| Preview | Name | Vibe |
|---|---|---|
| `aurora-mesh.html` | Aurora Mesh | soft blended gradient blobs, parallax tilt |
| `particle-constellation.html` | Particle Constellation | drifting particles linking into constellation lines near the cursor |
| `grid-pulse.html` | Grid Pulse | dot-grid lit by a spotlight that follows the cursor |
| `liquid-blob.html` | Liquid Blob | gooey SVG-filter blobs displaced by the cursor |
| `starfield-warp.html` | Starfield Warp | 3D starfield, hold click/tap to warp to lightspeed |
| `ribbon-flow.html` | Ribbon Flow | silk ribbons of light undulating across the screen |

## Adding a new background

1. Duplicate `template.html`, rename to `kebab-case.html`, drop it in `/backgrounds`.
2. Build your effect inside the marked section — keep the `getParam` / `safeHex` / `hexToRgb` helpers and the base scaffold (hero text overlay, reduced-motion consideration, mobile-safe sizing).
3. Update the header comment block with your param table.
4. Add an entry to the `BACKGROUNDS` array in `index.html` (name, description, tags, params) — the gallery renders itself from that manifest.

## Query param conventions

Kept consistent across files where the effect allows it:

| Param | Meaning |
|---|---|
| `color`, `color1`, `color2`, `color3` | hex colors (URL-encode the `#` as `%23`) |
| `bg` | background hex color |
| `speed` | float multiplier for animation speed, default `1` |
| `density` | float multiplier for particle/element count, default `1` |
| `text` | optional hero text overlay string |
| `textcolor` | hex color for the hero text |

Any file-specific params (`radius`, `linklen`, `count`, `size`, etc.) are documented in that file's own header comment.

## Local preview

No build step needed — just open the files directly, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. Repo Settings → Pages → Deploy from branch → `main` / `root`.
3. Already wired to `Kartik13-op/bgkit` — just enable Pages (see below).

## License

MIT — fork it, rename it, ship it.
