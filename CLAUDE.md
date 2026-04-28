# CLAUDE.md — ViperCoin.io Website

This file contains everything Claude needs to work on this project. Read it fully before making any changes.

---

## RULE #1 — Always Update the Changelog

**Every time you change any file, add an entry to `CHANGELOG.md` immediately.**

Use this format:

```
## [YYYY-MM-DD] — Brief title

### Changed
- Description of what changed and why
```

No exceptions. If you make three separate edits in one session, add three entries (or one combined entry covering all changes made that session). The changelog is how the team tracks progress across sessions.

---

## Project Overview

**ViperCoin.io** is the official website for ViperCoin, a Cardano-based memecoin community. The site is built as a **single HTML file** (`Website v2.html`) with all HTML, CSS, and JavaScript inline — no build tools, no frameworks, no dependencies beyond CDN links already in the file.

**Pages (7 total):** Home · Lore & Tokenomics · Products & Services · NFTs · Memes · About Us · Contact

**Brand identity:** Dark theme, green accents, Bebas Neue font, snake/viper mascot. Styled after [viperswap.io](https://viperswap.io).

---

## Repository Structure

```
vipercoinio-website/
├── Website v2.html          ← THE only file to edit for website changes
├── assets/                  ← Logos, GIFs, fonts used by the website
│   ├── fonts/               ← TGSPerfectCondensed, SlashSignature (woff/woff2)
│   ├── logo.png
│   ├── viper-char.webp
│   ├── coin-rotate.gif
│   ├── viper-head.gif
│   └── ...
├── Images/                  ← NFT art, team photos, icons
│   ├── Jinx.png
│   ├── Madmusicmaker.png
│   ├── MikeyExile.png
│   ├── Snekable.png
│   ├── Biohazard Fang.jpg
│   ├── Infernal Mage.png
│   ├── logo-white.png
│   ├── Discord-Symbol-White.png
│   └── ...
├── Branding Assets/         ← SVGs, PNGs, brand kit (for reference/design)
│   ├── SVG/
│   └── PNG/
├── CHANGELOG.md             ← Updated after every change
├── CLAUDE.md                ← This file
├── GETTING_STARTED.md       ← Onboarding guide for new contributors
└── README.md                ← Project overview
```

**NOT in this repo (too large):**
- `Viper Memes/` — 562 meme images (469 MB). These must be kept in the same folder as `Website v2.html` locally for the meme gallery to work. They are not needed to edit other pages.

---

## Working File

**`Website v2.html` is the only file that contains the website.** All CSS and JS are inline. To preview changes, open the file directly in a browser or use VS Code's Live Server extension.

When you edit `Website v2.html`, changes to HTML/CSS/JS are immediately visible on refresh.

---

## Design System

### CSS Custom Properties
```css
--bg: #000000        /* Page background */
--bg2: #111111
--bg3: #1a1a1a
--green: ...         /* Primary accent */
--gold: ...          /* Secondary accent */
--red: ...
--cyan: ...
--purple: ...
```

### Typography
- **Bebas Neue** (Google Fonts CDN) — headings
- **TGSPerfectCondensed** (local, `assets/fonts/`) — display
- **SlashSignature** (local, `assets/fonts/`) — decorative
- **Bitter** (Google Fonts CDN) — body

### Navigation
Floating pill nav, fixed at top:
```css
nav {
  position: fixed; top: 10px; left: 12px; right: 12px;
  height: 56px; border-radius: 50px;
  border: 1px solid rgba(255,255,255,0.55);
  background-color: rgba(6,6,6,0.96);
}
```
Nav bottom edge = 66px. **All first-visible sections use `padding-top: 120px` on mobile** (`@media (max-width: 960px)`) to clear the nav.

### Page Layout
```css
.page { display: none; }
.page.active { display: flex; flex-direction: column; min-height: 100vh; }
.page.active > footer { margin-top: auto; }
```
Sections bleed to the very top (no `padding-top` on `.page`). Content clears the nav with padding on first sections.

### Dot Grid Pattern
**Always use CSS, never SVG:**
```css
background: radial-gradient(circle, rgba(255,248,215,0.X) 1.5px, transparent 1.5px);
background-size: 28px 28px;
```

---

## Page-Specific Notes

### Home
- `.hero-wrap { min-height: 100vh; }`
- `.char-slideshow` — 7-image crossfade slideshow, `width: min(600px, 95%)`
- Stats: Holders `1,540+`, NFTs `3,174/4,999`, Meme count is dynamic

### Lore & Tokenomics
- Placeholder lore text — owner will supply actual content later
- Character: `Images/Viper_GIF_0020.gif`

### Memes Gallery
- 562 memes referenced via `buildMemeList()` ranges in JS
- `.js-meme-count` spans and `#js-meme-stat` update automatically from `MEMES.length`
- To add memes: extend the ranges array in `buildMemeList()`
- Uses lazy loading + JSZip (CDN) for "Download All"
- Memes live in `Viper Memes/` folder (not in this repo)

### About Us
- Team: Jinx, Madmusicmaker, MikeyExile, Snekable
- Character: `Images/Viper_IDK.gif`

### NFTs
- Marquee with 13 NFTs × 2 for seamless loop (`translateX(-50%)`)
- 6 hero previews: Biohazard Fang, Infernal Mage, Ruby Sage, Necro Bone Revenant, The Scorched Oracle, Viperine

### Contact
- Two-column split — cream left, dark right
- Mobile: single column
- Icons: real image files (not emoji) — `Images/logo-white.png`, `Images/Discord-Symbol-White.png`, `Images/VIPERSWAP.png`, `Images/WayUp Logo.jpg`

---

## Social & Community Links

| Platform   | URL |
|-----------|-----|
| X/Twitter  | https://x.com/vipercoin_ada |
| Discord    | https://discord.gg/vipercoin |
| Linktree   | https://linktr.ee/vipercoin_ada |
| ViperSwap  | https://viperswap.io |
| NFT Market | https://www.wayup.io/collection/45851dd847cf1e49b795f3c6c998e1eb18b9d30afa71e4ce8bff4183 |

---

## What NOT to Do

- Do not create separate CSS or JS files — everything stays inline in `Website v2.html`
- Do not add inline `style=""` attributes — use CSS classes instead
- Do not use SVG for dot grid backgrounds — use CSS `radial-gradient`
- Do not edit the meme ranges without understanding the `buildMemeList()` function
- Do not skip updating `CHANGELOG.md`
