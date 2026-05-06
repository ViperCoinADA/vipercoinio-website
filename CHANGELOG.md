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

## [2026-05-06] — FANGS cards: icon top-alignment, responsive scaling, equal heights

### Fixed
- `.fc` inner grid changed from `align-items: center` → `align-items: start` + `align-content: start` so the icon always anchors to the top of the title text instead of floating to the vertical midpoint of multi-line titles (which shifted visually at different viewport widths).
- `.fc .fc-icon` and `.fc .fc-title` both get explicit `align-self: start` to guarantee top-alignment regardless of row height.
- `flex-shrink: 0` added to `.fc .fc-icon` to prevent the circle from compressing when the title text is very long.
- `grid-template-rows: auto 1fr` added to `.fc` so the description row expands to fill any remaining card height — ensures all 4 cards distribute their internal space consistently.

### Changed
- `.feat-grid` now has `align-items: stretch` set explicitly (was relying on CSS grid default) to guarantee all 4 cards in a row stretch to the same height.
- Icon responsive scaling added:
  - `≤960px`: icon `57px → 48px`
  - `≤640px`: icon `42px`, card padding `2.2rem → 1.6rem`, title `1.875rem → 1.5rem`

---

## [2026-05-06] — v3 release: merged madmusicmaker branch into master

**Merged by:** MrJustJinx  
**Branch:** `madmusicmaker` → `master`  
**New file:** `Website v3.html` (madmusicmaker's changes promoted from `Website v2.html`)  
**Previous version preserved as:** `Website v2.html` (original MrJustJinx build, untouched on master)

### Summary of all changes in this release (authored by madmusicmaker / Jaron Deming)

#### Nav bar — complete rework
- Nav pill enlarged: `height: 56px → 88px`, `top: 10px → 24px`, `left/right: 12px → 28px`
- Nav background: removed dot-grid overlay, now plain solid black `#000`
- Logo image swapped: `coin-rotate.gif` → `Viper_Head transparant.png` (new asset)
- Logo font size: `1.8rem → 2.4rem`, letter-spacing tightened to `0.5px`
- Nav link font: `0.88rem → 1.45rem`, weight `400 → 700`, color always full white (no faded inactive state)
- Active page indicator: gold underline bar (`::after`) anchored flush to pill bottom
- BUY $VIPER button: permanent `1px solid #fff` border; hover now uses inset bottom-bar (`box-shadow: inset 0 -2px 0 0 #fff`) + 2px padding shift instead of lift/glow
- Hamburger: rebuilt as green `#8ded41` circle (52×52px) matching BUY $VIPER visual language; bars `#000`; same inset hover treatment
- Mobile menu repositioned: `top: 76px → 124px` to clear taller nav

#### Buttons — unified hover pattern (all buttons site-wide)
- All buttons (`.btn-red`, `.btn-green`, `.btn-ghost`, `.btn-gold`, `#dl-all-btn`, `.dl-btn`) given `1px solid #fff` border and the same inset bottom-bar + padding-shift hover treatment as BUY $VIPER
- Removed all glow/lift/color-change hovers — replaced with consistent press-down feel
- `align-self: flex-start` added to all buttons to prevent stretching in flex-column containers

#### FANGS OF CARDANO cards — full redesign
- Cards now use solid accent color fill as background (`var(--fc-color)`) with black text — no longer dark glass
- Square corners (no `border-radius`)
- Layout: `display: grid; grid-template-columns: 1fr auto` — title left, circular icon right
- Icon in circular badge: 57px, `rgba(255,255,255,0.3)` fill, `1px solid #000` ring
- Cardano card icon swapped to `Images/cardano-starburst-black.svg` (new asset); SVG uses `object-fit: contain` inside circle
- Title font size: `1.25rem → 1.875rem`, uppercase
- `fc-red` color changed from site red `#d63c2a` to magenta `#de5af2`
- Hover: colored drop-shadow via `--fc-shadow` variable per card, white border

#### Color token update
- `--gold` updated: `#f0a830 → #ffa621` — cascades through all gold usages site-wide

#### Page top-padding — nav clearance
- All hero/landing sections bumped `5rem → 8rem` top padding to clear taller nav bottom edge (~113px)
- `.hero-left` kept at `4rem` (content was too low in viewport at 8rem)

#### Section pills / tags
- `.tag` gets `align-self: flex-start` to stop stretching in flex-column parents
- Letter-spacing padding fix: `padding: 5px 14px → 5px 10px 5px 14px` so text centers inside pill
- "POWERED BY CARDANO" eyebrow changed from plain `<div>` to `<span class="tag tag-green">`

#### HOW IT WORKS step cards
- Square corners: `border-radius: 12px → 0`
- Hover border: `rgba(0,0,0,0.07) → solid #000`

#### Products & Services cards
- `.pc` and `.pc-body` use flex-column with `flex: 1` so buttons lock to card bottoms regardless of description length

#### Responsive breakpoints
- Hamburger breakpoint moved: `960px → 1050px`
- New shrink tier at `1300px`: menu items and logo scale down before hiding
- Mobile section top-padding bumped `120px → 160px` across all affected sections

---

## [2026-05-05] — Products & Services cards: buttons locked to bottom

### Changed
- `.pc` (Products & Services cards) switched to `display: flex; flex-direction: column` so the body section can grow vertically.
- `.pc-body` got `flex: 1; display: flex; flex-direction: column; justify-content: space-between` — the description sits at the top of the body and the button anchors to the bottom of the card. Buttons now line up at the same vertical position across all cards regardless of description length.

---

## [2026-05-05] — FANGS card border thickness matched to HOW IT WORKS

### Changed
- `.fc` border `1px → 2px solid var(--border)` so it matches the step cards' 2px border thickness. The white hover border (`.fc:hover{border-color:#fff}`) is therefore now 2px — visually consistent across both card families.

---

## [2026-05-05] — HOW IT WORKS step cards: square corners + black hover border

### Changed
- `.step` `border-radius: 12px → 0`. The four step cards now have square corners.
- `.step:hover` got `border-color: #000` so the standard faint `rgba(0,0,0,0.07)` border switches to solid black on hover, giving a clearer interactive feedback (lift + shadow + crisp black outline).

---

## [2026-05-05] — FANGS card colored dropshadow (hover-only) + white hover border

### Fixed
- The intended colored card dropshadow wasn't visible. Switched implementation from `color-mix(in srgb, var(--fc-color) 10%, transparent)` to per-class rgba via a new `--fc-shadow` variable. Each color class declares its own pre-tuned shadow tint: `.fc-red` → `rgba(222,90,242,0.45)`, `.fc-green` → `rgba(111,228,46,0.45)`, `.fc-cyan` → `rgba(0,212,232,0.45)`, `.fc-gold` → `rgba(255,166,33,0.45)`. Higher alpha than the step cards' 10% black is needed because a colored shadow on a dark page background needs more weight to register visually (the step cards sit on cream/white, where 10% black is plenty).

### Added
- `.fc:hover` applies the colored dropshadow (`box-shadow: 0 16px 36px var(--fc-shadow)`) and a white border (`border-color: #fff`) alongside the existing `translateY(-6px)` lift. Same offset/blur as the HOW IT WORKS step shadow for consistency. Standard state has no shadow — colored glow only appears on hover.

---

## [2026-05-05] — Cleared hero-image clipping on NFT, Lore, and About pages

### Fixed
- The NFT page's right-side thumbnail grid (`.nft-tr`) and the Lore (`.lore-tr`) and About (`.about-tr`) page's full-bleed background images were clipped behind the fixed nav. Their containers had only `padding: 3rem` (or `0`) — far less than the nav's ~113px bottom edge. Bumped each to `padding: 8rem 3rem 3rem` / `padding: 8rem 0 0` so the images and thumbnails start below the nav.

---

## [2026-05-05] — Mobile dropdown menu repositioned below the nav

### Fixed
- `.mobile-menu` `top: 76px → 124px`. Was set when the nav was smaller (top:10, height:56). With the current nav (top:24, height:88, bottom edge ~113), the dropdown was opening underneath the nav pill and getting hidden behind it (nav `z-index: 1000` > dropdown `z-index: 999`). Now opens cleanly below the nav.

---

## [2026-05-05] — POWERED BY CARDANO unified with descriptor pill style

### Changed
- Home hero eyebrow changed from a plain `<div class="hero-eyebrow">` to `<span class="tag tag-green hero-eyebrow">` so it shares the same pill styling (padding, border-radius, border, font) as the WHY VIPER? / GET STARTED / etc. descriptors throughout the site, with the green color variant.
- `.hero-eyebrow` CSS stripped down to just `opacity: 0; animation: fadeUp 0.7s 0.1s forwards;` — typography/color/box now come from `.tag` and `.tag-green`. Animation behavior unchanged.

---

## [2026-05-05] — Descriptor pills: stop stretching + center text

### Fixed
- `.tag` pills (the section descriptors above titles — WHY VIPER?, GET STARTED, ECOSYSTEM, etc.) were stretching to full container width inside flex-column parents (`.lore-tl`, `.about-tl`, `.nft-tl`, `.sp-red`, `.sp-dark`, `.contact-tl`). Same root cause as the buttons. Added `align-self: flex-start` so they shrink to their text content like in `.feat-section`.
- Visible text inside `.tag` was off-center because `letter-spacing: 4px` adds an invisible 4px of trailing space after the last character. Compensated by reducing right padding by 4px: `padding: 5px 14px → 5px 10px 5px 14px`. Visible text now sits centered between the pill's left and right edges.

---

## [2026-05-05] — Stop buttons stretching to full container width

### Fixed
- `.btn-red`, `.btn-green`, `.btn-ghost`, `.btn-gold` were stretching to full width inside flex-column section containers (`.sp-red`, `.sp-dark`, `.lore-tl`, `.about-tl`, `.nft-tl`, `.contact-tl`) because flex children default to `align-items: stretch`. Added `align-self: flex-start` to each so they auto-size to content — matching the BUY $VIPER button's compact pill look.
- `.mobile-menu .mob-cta` got `align-self: center` so the mobile BUY $VIPER shrinks to content width and centers in the dropdown instead of stretching with the menu links.
- `.nav-cta`, `#dl-all-btn`, `.dl-btn` already lived in row-flex / centered parents and weren't stretching, so they were left alone.

---

## [2026-05-05] — Hero-left content visible from first load

### Changed
- `.hero-left` top padding `8rem → 4rem` so the home-page title, sub, description, and buttons sit higher in the viewport and are fully visible above the fold without scrolling.

---

## [2026-05-05] — Responsive nav: button locked right, menu adapts, hamburger at 1200px

### Changed
- Restructured the responsive nav so the BUY $VIPER button stays locked to the right edge at full desktop size and the menu items shrink to make room (instead of the button getting pushed off the pill).
- New cascade: **≥1401px** full-size desktop nav; **1201–1400px** menu items shrink (`1.15rem`, tighter padding/letter-spacing) + logo shrinks (`1.65rem`, image 36px) + nav padding `1.8rem → 1rem`, button stays full size; **≤1200px** menu links + button hide and the hamburger appears; **≤960px** still triggers the existing hero/section single-column layout.
- Removed the previous `.nav-cta { font-size: 1.1rem; padding: 11px 22px }` shrink override at 1200px — the button now keeps its desktop `1.3rem / 13px 28px` sizing across all breakpoints (per "don't shrink the button" direction).

---

## [2026-05-05] — Hamburger styled like BUY $VIPER, locked to 52×52 circle

### Changed
- `.hamburger` rebuilt to mirror the BUY $VIPER button visual language: green `#8ded41` background, `1px solid #fff` border, and the same `box-shadow: inset 0 -2px 0 0 #fff` + content-shift hover treatment as `.nav-cta` (via `padding-bottom: 4px` on hover, since explicit width/height locks the outer dimensions).
- Set explicit `width: 52px; height: 52px` with `border-radius: 50%` so the button is a perfect circle the same height as BUY $VIPER. Bars centered via `align-items: center; justify-content: center` instead of padding-based positioning.
- Bar width trimmed `24px → 18px` for a tighter, less-elongated icon. Bar color `#fff → #000` so the lines read on the green pill (continues to rotate to black "X" on `.hamburger.open`).

---

## [2026-05-05] — Hero section top padding bumped to 8rem to clear nav

### Changed
- All hero/landing sections got top padding bumped from `5rem → 8rem` (or `3rem → 8rem` where applicable) to clear the now-taller fixed nav (`top:24px`, `height:88px`, bottom edge ~113px) with breathing room. Affected: `.hero-left`, `.hero-right`, `.lore-tl`, `.about-tl`, `.nft-tl`, `.contact-tl`, `.meme-head`, `.prod-hero`. Maintains the original ~1.45× nav-height proportion. (`.hero-left` was later reduced to 4rem — see separate entry.)

---

## [2026-05-05] — FANGS card refinements: smaller icon, bold body, ampersand wrap, colored shadow

### Changed
- `.fc .fc-icon` size reduced 10%: `63px → 57px`.
- `.fc .fc-desc` `font-weight: 700` so the description body text reads bold against the bright card fills.
- "Utility & NFTs" title `<br>` repositioned: `Utility &<br>NFTs → Utility<br>& NFTs`. The ampersand now starts the second line.
- `.fc` got a permanent colored drop-shadow matching each card's accent: `box-shadow: 0 16px 36px color-mix(in srgb, var(--fc-color, var(--red)) 10%, transparent)`. Same offset/blur/opacity as the HOW IT WORKS step cards' hover shadow but tinted per card (magenta, green, cyan, gold) instead of black. Removed the prior harsh `rgba(0,0,0,0.3)` hover shadow; hover now just lifts via `translateY(-6px)`.

---

## [2026-05-05] — FANGS cards: title on left, icon on right + Cardano SVG fit fix

### Changed
- Swapped icon and title order in FANGS cards. `.fc` `grid-template-columns` flipped from `auto 1fr` to `1fr auto`, and explicit `grid-column` / `grid-row` placement added: title now occupies column 1 row 1, icon column 2 row 1, description spans both columns on row 2. No HTML changes needed.
- Cardano starburst SVG was clipping inside the round icon because `object-fit: cover` cropped its corners against the circular border. Added `.fc .fc-icon img[src*="cardano-starburst"] { object-fit: contain; width: 80%; height: 80% }` so the SVG scales down enough to fit fully inside the inscribed circle. Other card icons still use `cover` and bleed to the icon edge.

---

## [2026-05-05] — FANGS card title bigger + Cardano icon swapped to SVG starburst

### Changed
- `.fc-title` font-size `1.25rem (20px) → 1.875rem (30px)` — +10px per request. Affects both stacked rows of the FANGS section card titles.
- "Cardano Powered" card icon image swapped from `Images/Cardano Logo.png` to `Images/cardano-starburst-black.svg`. Other three card icons untouched.

---

## [2026-05-05] — FANGS card layout: smaller circular icon beside two-line title

### Changed
- `.fc .fc-icon` border thinned `2px → 1px` to match the nav pill thickness, size shrunk `84px → 63px` (25% smaller), `overflow: hidden` added so the circle's curve crops the image.
- `.fc .fc-icon img` now `width: 100%; height: 100%; object-fit: cover` — image fills the entire interior of the circle and the circular border crops the bottom corners.
- `.fc` switched from default block stacking to `display: grid; grid-template-columns: auto 1fr; gap: 1rem; align-items: center` — icon sits in column 1, title in column 2, both vertically centered on row 1. Description now spans both columns on row 2 via `.fc .fc-desc { grid-column: 1 / -1 }`.
- Title margin-bottom zeroed inside `.fc` (the grid `gap` handles spacing) and `line-height: 1.05` added to keep the two stacked title lines tight.
- Each card's title got an explicit `<br>` between its two words (e.g. `Community Driven → Community<br>Driven`) so it reliably stacks into two rows beside the icon. `Utility & NFTs` breaks after the ampersand.

---

## [2026-05-05] — FANGS card icons in circular container + global gold color updated

### Added
- `.fc .fc-icon` (FANGS section card icons) now sit inside an 84px circular container with `border-radius: 50%`, a `2px solid #000` ring, and a translucent `rgba(255,255,255,0.3)` fill that lets the card's accent color show through as a lighter tint. Icon image scaled down to 40px to fit. Scoped to `.fc` so the contact-page icons (`.contact-fc .fc-icon`) are unaffected.

### Changed
- `--gold` CSS custom property `#f0a830 → #ffa621`. Cascades through every `var(--gold)` usage automatically.
- Replaced two unrelated rgba gold values that had drifted from the variable: `rgba(240,168,48,*)` (one shadow alpha) and `rgba(232,184,75,*)` (used in `.tag-gold`, `.nft-thumb:hover`, `.ng:hover`, `.sl.jp:hover`) all updated to `rgba(255,166,33,*)` to match the new gold.

---

## [2026-05-05] — All button borders forced to pure white

### Fixed
- Button borders were rendering as muted gray on colored backgrounds because they used translucent white (`rgba(255,255,255,0.55)`, `0.18`, `0.15`, `0.14`) which blends with the underlying color. Replaced all button borders with solid `1px solid #fff`.
- Affected: `.nav-cta`, `.mob-cta`, `.btn-red`, `.btn-green`, `.btn-ghost`, `.btn-gold`, `#dl-all-btn`, `.dl-btn`, `.lb-close`, `.lb-dl`, `.lb-share`.
- Removed three hover-state `border-color` overrides that conflicted with the pure-white base (`.lb-close:hover` was switching to red, `.lb-dl:hover` to translucent white, `.lb-share:hover` to half-white). Border now stays white in both standard and hover.
- Nav pill border (`nav` element itself, not a button) intentionally left at `rgba(255,255,255,0.55)` since the request was scoped to buttons.

---

## [2026-05-05] — FANGS cards: uppercase titles + red card swapped to #de5af2

### Changed
- `.fc-title` got `text-transform: uppercase` so all four card titles render in caps regardless of the underlying HTML casing.
- `.fc-red` `--fc-color` swapped from `var(--red)` (`#d63c2a`) to `#de5af2` (magenta/pink). Only the FANGS first card is affected — `var(--red)` itself is unchanged so `.btn-red`, marquee bar, etc. still use the original red.

---

## [2026-05-05] — FANGS OF CARDANO cards: solid accent fill, no rounding, black text

### Changed
- `.fc` cards (Community Driven, Cardano Powered, Meme Culture, Utility & NFTs in the FANGS OF CARDANO section): `border-radius: 12px → 0` for square corners, `background: rgba(255,255,255,0.025) → var(--fc-color, var(--red))` so each card fills with its top-accent color (red / green / cyan / gold), `color: #000` added on the card so the title text is black.
- `.fc-desc` text color `var(--text) (rgba(255,255,255,0.6)) → #000` for readability against the bright fills.
- Removed the now-redundant `.fc::before` accent strip (it would have rendered the same color as the new card background).
- Hover state simplified — kept the lift + drop shadow but dropped the border-color change, since the border was the same color as the background and produced no visual effect.

---

## [2026-05-05] — Unified all buttons to BUY $VIPER hover pattern

### Changed
- All main action buttons (`.btn-red`, `.btn-green`, `.btn-ghost`, `.btn-gold`, `.mob-cta`, `#dl-all-btn`, `.dl-btn`) now share the same hover treatment as `.nav-cta`: a permanent `1px solid rgba(255,255,255,0.55)` border, and on hover an `inset 0 -2px 0 0 #fff` bottom bar plus a 2px upward text shift. No background-color change, no outer drop shadow, no whole-button translateY lift.
- Switched the text-shift mechanism from a `<span>` + `transform: translateY` to a pure-CSS padding flip on hover (`padding: 13px 36px → 11px 36px 15px 36px` etc). Total padding stays constant so the button's outer width and height don't change; only the text moves up. This means no HTML span wrappers are needed on any button — applies to all instances by class alone.
- `.nav-cta` was converted to the same padding-flip approach for consistency, and the `<span>BUY $VIPER</span>` wrapper in the HTML was removed.
- `.btn-ghost` border thinned `2px solid rgba(255,255,255,0.25) → 1px solid rgba(255,255,255,0.55)` and padding bumped `12px → 13px` so it shares the same dimensions and translucent-white border as the other buttons.
- Per-button hover padding values match the relevant standard padding (subtracting/adding 2px top/bottom): primary buttons `13px → 11/15`, `#dl-all-btn` `11px → 9/13`, `.dl-btn` `8px → 6/10`, `.mob-cta` `11px → 9/13` (mobile).

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
