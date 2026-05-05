# Changelog

All notable changes to the ViperCoin.io website are documented here.

**Claude: add an entry every time you change any file. No exceptions.**

Format:
```
## [YYYY-MM-DD] — Short title

### Added / Changed / Fixed / Removed
- What changed and why
```

---

## [2026-05-05] — Menu logo image lifted 3px

### Changed
- `.nav-logo img` got `transform: translateY(-3px)` to offset the viper head upward 3px from its centered position.

---

## [2026-05-05] — Menu logo image enlarged

### Changed
- `.nav-logo img` height `44px → 64px`. Nav pill is 88px tall, so the image still has ~12px breathing room above and below.

---

## [2026-05-05] — Swapped menu logo image: coin-rotate.gif → Viper_Head transparant.png

### Changed
- Menu `.nav-logo` `<img>` `src` swapped from `assets/coin-rotate.gif` to `assets/Viper_Head%20transparant.png` (URL-encoded space in filename). Footer logo (`assets/logo.png`) is unchanged.

---

## [2026-05-05] — VIPER COIN logo bumped to 2.4rem

### Changed
- `.nav-logo` font-size `1.95rem → 2.4rem` to make the menu logo text larger.

---

## [2026-05-05] — VIPER COIN logo letter-spacing 1.5px → 0.5px

### Changed
- `.nav-logo` letter-spacing `1.5px → 0.5px`.

---

## [2026-05-05] — VIPER COIN logo letter-spacing 2px → 1.5px

### Changed
- `.nav-logo` letter-spacing `2px → 1.5px`.

---

## [2026-05-05] — VIPER COIN logo spacing further tightened

### Changed
- `.nav-logo` letter-spacing `2.85px → 2px`.
- `.nav-logo .slash` margin-left `-1px → -3px` (effective gap between "VIPER" and "COIN" now 7px, down from the prior 9px).

---

## [2026-05-05] — Tightened VIPER COIN logo spacing

### Changed
- `.nav-logo` letter-spacing trimmed `3px → 2.85px` (5% tighter character spacing in VIPER and COIN).
- `.nav-logo .slash` got `margin-left: -1px` so the gap between "VIPER" and "COIN" drops from the flex `gap: 10px` to an effective 9px (10% tighter). Image-to-VIPER gap is left at 10px since the request was for inter-word spacing only.

---

## [2026-05-05] — BUY $VIPER hover bar + text shift reduced to 2px

### Changed
- `.nav-cta:hover` inset bar slimmed from 4px to 2px (`inset 0 -4px 0 0 #fff → inset 0 -2px 0 0 #fff`).
- `.nav-cta:hover span` translation matched: `translateY(-4px) → translateY(-2px)`. Text size stays identical between standard and hover states.

---

## [2026-05-05] — BUY $VIPER text shifts up by the bar's height on hover

### Changed
- `.nav-cta:hover span` transform changed from `scale(0.92)` to `translateY(-4px)` — text now lifts 4px on hover, exactly matching the height of the inset white bar so it clears the bar instead of getting visually overlapped. Pill footprint untouched.

---

## [2026-05-05] — BUY $VIPER bottom bar moves inside the footprint

### Changed
- `.nav-cta:hover` box-shadow flipped from outset `0 4px 0 0 #fff` to inset `inset 0 -4px 0 0 #fff`. The 4px white bar now grows upward from the bottom edge inside the pill instead of extending downward beyond it. Outer footprint stays identical between standard and hover states.

---

## [2026-05-05] — Lock BUY $VIPER dimensions on hover + tighter right-edge gap

### Changed
- Wrapped "BUY $VIPER" in a `<span>` and moved the hover shrink from `font-size` to `transform: scale(0.92)` on the span. Transforms don't affect layout, so the pill's outer width and height stay fixed in both states; only the text visually shrinks.
- `.nav-cta` transition reduced to just `box-shadow 0.25s ease`; the new `.nav-cta span` carries `transition: transform 0.25s ease`.
- `nav` padding split from symmetric `0 1.8rem` to `0 1.1rem 0 1.8rem` so the BUY $VIPER button sits ~17px from the pill's right inner edge — matching the ~17px vertical gap between the button and the pill's top/bottom edges. Logo's left-edge gap is unchanged.

---

## [2026-05-05] — BUY $VIPER: permanent white border + text shrinks on hover

### Changed
- `.nav-cta` now has a permanent `border: 1px solid rgba(255,255,255,0.55)` matching the nav pill's own border in both standard and hover states.
- `.nav-cta:hover` no longer lifts the button. Replaced `transform: translateY(-3px)` with `font-size: 1.3rem → 1.2rem` so the text shrinks slightly to "adapt" as the white bottom bar emerges. Button's vertical footprint stays put.
- Transition switched to `font-size 0.25s ease, box-shadow 0.25s ease` so both the text shrink and the bottom-edge bar animate together. Bottom bar implementation (`box-shadow: 0 4px 0 0 #fff`) is unchanged.

---

## [2026-05-05] — BUY $VIPER hover: white bottom-edge bar, button lifts

### Changed
- `.nav-cta:hover` simplified. Was: darker-green bg + 1px lift + green glow. Now: a white 4px bar appears flush along the bottom curve of the pill, and the button lifts 3px so the text shifts up adaptively as the bar emerges.
- Implemented as a single `box-shadow: 0 4px 0 0 #fff` on hover, transitioned alongside `transform`. No pseudo-element, no extra markup — the shadow inherits the pill's `border-radius`, so the visible portion is a curved white sliver matching the bottom edge only.
- `.nav-cta` transition narrowed from `all 0.2s` to `transform 0.25s ease, box-shadow 0.25s ease` so only the two animated properties are eased.

---

## [2026-05-05] — Removed nav dot-grid overlay, solid black pill

### Changed
- `nav` dropped `background-image: radial-gradient(...)` and `background-size: 28px 28px;` and switched `background-color: rgba(6,6,6,0.96) → #000` — pill is now plain black with no dot pattern, per design direction. Border, blur, and pill geometry untouched.

---

## [2026-05-05] — Squared the active nav underline corners

### Changed
- `.nav-links a.active::after` `border-radius: 2px 2px 0 0 → 0` per design direction — selected-page indicator is now a fully rectangular bar.

---

## [2026-05-05] — Fixed nav vertical centering + restored green CTA, larger button text

### Fixed
- Menu items were rendering at the top of the nav pill instead of vertically centered. Root cause: `.nav-links li` had no explicit alignment, so the inline `<a>` collapsed to its content height and sat at the top of each `<li>`. Fixed by giving `.nav-links li` `display:flex; align-items:center;` and `.nav-links a` `height:100%`, so each link now fills the full pill height and centers its text vertically. The active underline (an absolutely-positioned `::after`) now anchors to the actual pill bottom instead of overlapping the text.

### Changed
- `.nav-links a.active::after` returned to flush-bottom placement (`bottom: 18px → 0`, `height: 3px → 4px`, `border-radius: 2px → 2px 2px 0 0`). The selected indicator now sits right against the pill's bottom border per design direction.
- `.nav-cta` reverted from `var(--gold)` back to brand green `#8ded41` (with green hover/shadow). Gold remains the active-link indicator color.
- `.nav-cta` font-size bumped `1.05rem → 1.3rem` and padding `15px 26px → 13px 28px` so BUY $VIPER reads at a similar visual weight as the menu items. 1200px-breakpoint values raised in tandem (`0.92rem → 1.1rem`, `12px 20px → 11px 22px`).
- `.mobile-menu .mob-cta` reverted to green `#8ded41` to match the desktop CTA.

---

## [2026-05-05] — Enlarged top nav pill + matched ViperSwap link styling

### Changed
- Nav `top: 10px → 24px`, `height: 56px → 88px`, `left/right: 12px → 28px` to better match the visual mass of viperswap.io's nav pill
- Bumped mobile clearance padding from `120px → 160px` on `.hero-right`, `.nft-tr`, `.about-tr`, `.contact-tl`, `.lore-tr`, `.prod-hero`, `.meme-head` to keep the same ~48px breathing room above the new nav bottom edge (now 112px)
- `.nav-links a` font-size `0.88rem → 1.45rem`, font-weight `400 → 700`, letter-spacing `1.5px → 0.5px`, color `rgba(255,255,255,0.5) → #fff` so menu items are full-white and chunky (no faded inactive state — underline is the only selected indicator). Did not push to ViperSwap's full size ratio because we have 7 items vs their 3 and overflow was clipping the CTA.
- `.nav-links` and `.nav-links a` now stretch to full pill height (`align-items:stretch`, `height:100%`, link is `display:flex; align-items:center`) so the active underline can sit flush with the pill's bottom border
- Active underline now anchored at `bottom: 0` (was `bottom: -4px`), thickened to `4px`, top corners rounded — mirrors how ViperSwap's selected indicator meets the pill border
- `.nav-cta` padding `9px 22px → 15px 26px` and font-size `0.88rem → 1.05rem` so BUY $VIPER stays inside the pill but reads weightier
- `.nav-logo` font-size `1.8rem → 1.95rem`, image height `38px → 44px`
- 1200px breakpoint values scaled down further so 7 nav items still fit comfortably on smaller laptops

---

## [2026-04-28] — Initial repository setup

### Added
- `Website v2.html` — complete 7-page website (Home, Lore & Tokenomics, Products & Services, NFTs, Memes, About Us, Contact)
- `assets/` — logos, GIFs, fonts used by the website
- `Images/` — NFT art, team photos, social icons
- `Branding Assets/` — SVGs, PNGs, brand kit, font files
- `CLAUDE.md` — full project instructions for Claude AI
- `README.md` — project overview
- `GETTING_STARTED.md` — contributor onboarding guide
- `CHANGELOG.md` — this file

### Website features at this version
- Floating pill navigation (viperswap.io-inspired)
- Dark theme with green/gold accents, Bebas Neue + TGSPerfectCondensed fonts
- Home: hero with 7-image crossfade slideshow, live stats (1,540+ holders, 3,174/4,999 NFTs)
- Lore & Tokenomics: placeholder content (owner to supply lore text and token numbers)
- Memes: 562-image lazy-loading gallery with JSZip "Download All"
- NFTs: seamless marquee of 13 NFTs × 2, 6 hero previews
- About Us: 4 team cards (Jinx, Madmusicmaker, MikeyExile, Snekable)
- Contact: two-column layout with real image icons for social links
- Fully responsive — mobile breakpoints at 960px and 640px
