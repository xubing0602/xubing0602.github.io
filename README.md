# Bing Xu — Personal Homepage

A single-file personal homepage for a Senior Data Scientist, featuring a dark terminal aesthetic with animated backgrounds, project showcase, and a customizable theme panel.

## Tech

Pure HTML/CSS/JS — no frameworks, no build step. Assets served as static files.

## Structure

```
260422_homepage/
├── index.html          # Full page (markup + styles + scripts)
└── assets/
    ├── avatar.webp     # Hero photo (WebP, 760px)
    ├── avatar_resized.jpg  # JPEG fallback
    └── avatar.jpg      # Original source (not served)
```

## Features

- Animated grid background with scan line effect
- Typewriter terminal in hero section
- Bento-grid project cards with mouse-glow effect
- Scroll-reveal animations via `IntersectionObserver`
- Tweaks panel: accent color, display font, density, grid toggle
- Fully responsive (3-col → 2-col → 1-col bento, collapsing nav)
- `prefers-reduced-motion` support

## Local Development

No server required — open directly in a browser:

```bash
open index.html
```

Or serve locally to avoid any asset path issues:

```bash
npx serve .
# or
python3 -m http.server 8080
```

## Customization

All design tokens live in `:root` at the top of `<style>`. Key variables:

| Variable | Purpose |
|---|---|
| `--bg` | Page background |
| `--cyan` | Accent color (overridden by `data-accent` attribute) |
| `--display` | Heading font family |
| `--mono` | Monospace font family |

The tweaks panel (bottom-right) toggles accent, font, density, and grid at runtime. Defaults are set in `TWEAK_DEFAULTS` in the `<script>` block.

## Performance Notes

- Hero image served as WebP (93KB) with JPEG fallback (177KB); original was 1.7MB
- Google Fonts loaded with `display=swap` to prevent invisible text during load
- Hero image preloaded via `<link rel="preload">` to minimize LCP
- Animated layers use `will-change` for GPU compositing

## Changelog

### 2026-04-29 — Project Card SVG Redesigns

**Sakura Map**
- Replaced narrow teardrop petals with proper wide cherry-blossom petals featuring characteristic notched tips
- Added double petal layer (back layer rotated 36°) for depth and fullness
- Added 10 gold stamens with anther dots; switched palette from purple to pink (oklch ~355°)
- Added 5 scattered fallen petal silhouettes as atmosphere

**Japan Restaurant Map**
- Replaced generic map-pin cluster with a ramen bowl illustration
- Bowl has double-ellipse rim (depth detail), wavy noodle lines, steam wisps, and two chopsticks resting diagonally across the rim
- Three small map pins retained in corners to preserve the map/location context

**China Footprints w/ Friends**
- Replaced abstract node-graph with scattered city dots and dashed route lines
- Added 3 hand-drawn penguin figures (1 cyan = self, 2 purple = friends) standing at key cities
- Shared city marked with a glowing halo ring where a friend penguin stands

**My Flight Atlas**
- Added two airplane silhouettes (top-down view with swept wings and tail fins)
- Cyan plane at apex of main arc (t=0.5, horizontal cruise); purple plane descending on purple arc (t=0.65, rotated 12°)
- Planes positioned using precise quadratic Bézier midpoint calculations

**World Heritage Explorer**
- Replaced globe wireframe with a split cultural/natural heritage scene
- Left (cyan): Greek temple with pediment, 6 columns, entablature, and two-step stylobate
- Right (purple): three-peak mountain range with snow cap and two pine tree clusters
- Centre: subtle UNESCO-style emblem (square = cultural, circle = natural, partially overlapping)
