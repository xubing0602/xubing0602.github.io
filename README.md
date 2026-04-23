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
