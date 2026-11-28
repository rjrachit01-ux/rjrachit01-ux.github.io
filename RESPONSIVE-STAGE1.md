# Responsive Navigation — Stage 1 Reference

**Completed:** 2026-11-26  
**Breakpoints:** Phone <768px · Tablet 768–1023px · Desktop ≥1024px

## What was done

### CSS foundations (index.html)
- Added `:root` responsive tokens: `--rsp-pad-phone:18px`, `--rsp-pad-tablet:32px`, section padding, title sizes, gap values
- Removed the cramping rule that squeezed desktop nav links at ≤640px

### Bottom-sheet nav (all 4 files)
- Breakpoint extended from `max-width:640px` → `max-width:1023px`
- Bar padding: 18px left / 8px right at phone; 32px left / 22px right at tablet (768–1023px)
- Backdrop: `rgba(0,0,0,0.45)`, 180ms linear (was 55%, 350ms)
- Sheet slide: 240ms `cubic-bezier(0.22,1,0.36,1)` (was 350ms)
- Sheet max-height: `calc(100dvh - 64px - env(safe-area-inset-top))` with `overflow-y:auto`
- Sheet bottom padding: `calc(28px + env(safe-area-inset-bottom))`
- Bar z-index raised to 160 while menu is open (above backdrop at 150)
- `prefers-reduced-motion`: transitions removed for `#ph-dim` and `#ph-sheet`

### navScroll fix (index.html)
- Now uses `hero-sec.getBoundingClientRect().bottom <= 64` (hero's lower edge vs bar height)
- Skips update while sheet is open (bar state frozen until close)

### JS improvements (all 4 files)
- `phNavToggle()` — single button toggles open/close (hamburger ↔ X)
- Scroll position saved before locking (`_phScrollY`) and restored on dismiss-without-navigation
- Focus trap: Tab/Shift+Tab cycles within open sheet
- Background `aria-hidden` while sheet is open (index.html)
- `Escape` key closes sheet (all files)
- Resize to ≥1024px closes sheet automatically (all files)
- Guard prevents double-open if already open

### Active states in sheet
- **index.html**: `phNavUpdateActive()` marks current page; "My work" active on home/entry
- **replay, statsboost, skin-buddy**: "My work" hardcoded as `ph-row on` (all are case studies)

## Files changed
- `site/index.html`
- `site/statsboost/navigation.css` + `site/statsboost/index.html`
- `site/replay/index.html`
- `site/skin-buddy/index.html`

## Stage 2 — COMPLETE (2026-11-27, corrected)

### Pages changed: `site/index.html`

#### Start page (`#pg-entry`) — phone <768px
- Padding: `calc(env(safe-area-inset-top) + 32px) 18px calc(env(safe-area-inset-bottom) + 32px)`
- `overflow-x:hidden; overflow-y:auto; min-height:100dvh` (allows scroll on short screens)
- `.ename`: 32px
- `.eterm`: max-width 354px, centred
- `.etagline`: max-width 354px, centred, 24px top gap
- `.etagline-secondary`: 16px, line-height 1.6
- `.et5`, `.ectas`: width 100% (makes Enter fill the container)
- `.ectas`: margin-top 28px, gap 12px
- `.ebtn`: width 100%, min-height 52px
- `.eskip`: min-height 44px, flex display for touch target

#### Start page (`#pg-entry`) — tablet 768–1023px
- Padding: `calc(env(safe-area-inset-top) + 40px) 32px calc(env(safe-area-inset-bottom) + 40px)`
- `.ename`: 40px
- `.etagline-secondary`: 16px, line-height 1.6
- `.et5`, `.ectas`: max-width 354px centred, same button specs

#### Add my card (`#pg-onboard`) — HTML structure
- `.ob-nav-row` div added as first child of `#pg-onboard`, containing `.ob-back` and `.ob-skip-sm`
- Skip destination fixed: `gp(obPrevPage==='gallery'?'gallery':'home')` (gallery-origin returns to gallery)
- `.ob-skip-sm` removed from `.ob-btn-row`; `.ob-btn-row` now contains only Submit
- `.ob-credit` always hidden (`display:none!important` in global CSS) — conflicts with nav row placement on desktop
- `.ob-back` global CSS: `position:absolute;top:20px;left:24px` removed (positioned by `.ob-nav-row` instead)
- `.ob-nav-row` global CSS: `position:absolute;top:0;left:0;right:0;display:flex;justify-content:space-between;align-items:center;padding:20px 24px` — absolute on desktop, overridden to static on phone/tablet

#### Add my card (`#pg-onboard`) — phone <768px
- Padding: `calc(env(safe-area-inset-top) + 24px) 18px calc(env(safe-area-inset-bottom) + 32px)`
- `justify-content:flex-start; min-height:100dvh`
- `.ob-nav-row`: `position:static; width:100%; min-height:44px; margin-bottom:24px; padding:0` — normal-flow flex row, Back left, Skip right
- `.ob-back`: min-height 44px, cursor:pointer
- `.ob-skip-sm`: min-height 44px, cursor:pointer
- 24px gap from nav row to welcome heading (via margin-bottom on nav row)
- `.ob-welcome`: 32px, line-height 1.15
- `.vc`: width 100%, max-width 320px, min-height 184px, padding 20px, margin 0 auto 24px
- `.ob-form-wrap`: gap 20px; `.ob-field`: gap 8px; inputs: min-height 48px
- `.cdot`: 44×44px; `.cdots`: gap 8px
- `#pg-onboard .btn-dk`: width 100%, min-height 52px, font-size 16px, centred

#### Add my card (`#pg-onboard`) — tablet 768–1023px
- Padding: `calc(env(safe-area-inset-top) + 24px) 32px calc(env(safe-area-inset-bottom) + 32px)`
- `.ob-nav-row`: `position:static; width:100%; min-height:44px; margin-bottom:24px; padding:0; max-width:560px; margin-left:auto; margin-right:auto` — Back left, Skip right, aligned with 560px content column
- `.ob-back`: min-height 44px, cursor:pointer
- `.ob-skip-sm`: min-height 44px, cursor:pointer
- `.ob-welcome`: 36px
- `.ob-wrap`: max-width 560px centred
- `.vc`: width 100%, max-width 320px; same form-field specs as phone
- Submit button only in `.ob-btn-row` (Skip in nav row on both phone and tablet)

#### Add my card (`#pg-onboard`) — desktop (≥1024px)
- `.ob-nav-row{display:contents}` — dissolves the wrapper; Back's `position:absolute;top:20px;left:24px` is relative to `#pg-onboard` exactly as before
- `.ob-credit` visible at `position:absolute;top:20px;right:24px` — original desktop behaviour restored
- Skip is moved into `.ob-btn-row` (beside Submit) by `obResponsive()` on load and resize — original desktop layout restored
- No duplicate interactive controls: a single `.ob-skip-sm` element moves between `.ob-nav-row` (phone/tablet) and `.ob-btn-row` (desktop) via JS; inline onclick is preserved, no extra event listeners added
- `obResponsive()` also runs on `DOMContentLoaded` and `window.resize`

## Stage 3 — COMPLETE (2026-11-27, hero vertical spacing revised)

**Note: Option 3 selected for phone hero** (supersedes earlier Option 1 selection)

### Pages changed: `site/index.html`

#### Phone hero Option 3 (≤767px)
- `.hero-content` and `.hero-coord` hidden on phone via `display:none!important`
- `.hero` overridden to `height:auto; min-height:0; display:block; padding-bottom:0; overflow:visible`
- `.ph-hero` in normal flow: `position:static; padding:64px 16px 0` (64px clears fixed nav)
- `.ph-hero-sticker`: `position:static; display:inline-block; margin-bottom:48px` — 48px gap to letter row
- Letters: `ph-ltr` class, 92px Baloo 2, text-shadow `4px 5px 0 var(--tc)`, 1400ms cycle
- `.ph-hero-row{margin-bottom:28px}` — 28px gap to sentence (unchanged base style)
- Sentence: `ph-hero-sent`, 23px DM Sans, inactive phrases `rgba(249,247,242,.34)`, active `#c8593e`
- `hero-sub` in normal flow: `position:static; margin-top:40px; padding-bottom:calc(32px + env(safe-area-inset-bottom))`
- Hero grows with content; no viewport-height minimum; following section moves up naturally
- Measured at 390×844: hero height 464px; spacings confirmed 48/28/40px per spec
- JS: `phHeroInit()`, `phHeroRender()`, `phHeroCycleStart()`, `phHeroCycleStop()`, `phHeroPick()`
  - `phHeroInit()` called in `gp('home')` block after `wspInit()`
  - Cycle stops when navigating away from home (`phHeroCycleStop()` added to `gp()`)
  - 1400ms auto-cycle, 4000ms hold on tap, `prefers-reduced-motion` respected
  - HTML built once (guarded by `row.dataset.built`)

#### Tablet hero (768–1023px)
- Desktop expanding/collapsing RACHIT composition and tap interaction fully preserved
- `.hero` overridden to `height:auto; min-height:0; flex-direction:column; align-items:center; padding-top:128px; padding-bottom:40px`
  - 128px = 64px nav clearance + 64px gap to letter group (per spec)
- `hero-sub` in normal flow: `position:static; margin-top:40px; white-space:normal; text-align:center`
- Measured at 768×1024: hero 404px; at 820×1180: hero 415px; letters at 128px; 40px gap to radio line
- No viewport-height fill; portrait tablet no longer has dead space below letters

#### Work / project cards (phone <768px, tablet 768–1023px)
- Removed duplicate `@media(max-width:700px){.proj-grid{grid-template-columns:1fr;}}` (×2)
- Phone: 1-col grid, `gap:16px`
- Tablet: 2-col grid, `gap:20px`
- Both phone and tablet: `aspect-ratio:auto` on card; `position:relative;aspect-ratio:4/3` on `.proj-thumb`
- `.proj-overlay`: `position:relative;opacity:1;background:#18181b;padding:20px` — always visible
- `.proj-tags-ov`, `.proj-title-ov`, `.proj-desc-ov`, `.proj-cta-ov`: `opacity:1;transform:none;transition:none`
- `.proj-title-ov`: `font-size:24px`; `.proj-desc-ov`: `font-size:16px`
- `cursor:pointer` on card (replaces `cursor:none` from base CSS)
- Hover thumb scale disabled (`transform:none`)

#### Testimonials (phone <768px)
- Card width: `calc(100vw - 36px)` (wider than old `calc(100vw - 72px)` formula)
- `height:auto;min-height:0;padding:24px 24px 24px 28px`
- Adjacent cards (adj-left, adj-right, far, far-right): `transform:none;opacity:0.4` — no rotation
- Body text: `font-size:16px`
- Tablet: `height:auto` only (carousel composition preserved)

#### About me (phone <768px, tablet 768–1023px)
- Phone: `ab-top` → 1-col, `gap:24px`; `ab-heading` → `var(--rsp-h2-phone)` (32px)
- Tablet: `ab-top` → 1-col, `gap:32px`; `ab-heading` → `var(--rsp-h2-tablet)` (36px)
- Photo strip: `220px` phone / `280px` tablet

#### Music (playlist section)
- `.sp-frame`: `max-width:100%;width:100%` on phone/tablet — prevents any horizontal overflow

#### Contact / footer (phone <768px)
- `.ct-sub`: `white-space:normal!important;font-size:16px!important`
- `.foot-bot`: `flex-direction:column;align-items:flex-start;gap:16px;padding-right:0` — stacked
- `.foot-back`: `min-height:44px;display:inline-flex;align-items:center;cursor:pointer`
- Tablet: `.foot-back` min-height 44px only; horizontal layout maintained

#### Shared spacing (phone/tablet)
- Section padding: `.work-sec,.testi-sec,.about-sec,.playlist-sec` → 56px phone / 64px tablet
- Section heading: `.sec-h` → `var(--rsp-h2-phone)` / `var(--rsp-h2-tablet)`
- Relies on existing `--pad:clamp(18px,4vw,52px)` on `.wrap` (already ~18px at 390px)

## Stage 4 — COMPLETE (2026-11-27)

### Pages changed: `site/index.html`

#### Playground (phone <768px, tablet 768–1023px)
- Phone: `.play-grid{grid-template-columns:1fr;gap:20px;}`, `.play-head/.play-body{padding:20px;}`, `.stool{44px;font-size:16px}`
- Tablet: `.play-grid{grid-template-columns:1fr 1fr;}`, Script card `.play-card:last-child{grid-column:1/-1}`, `.stool{44px;font-size:16px}`
- Desktop (≥1024px): `.stool` stays 30×30px/12px — tablet override scoped to tablet breakpoint
- Pointer events: all `mousedown/move/up` → `pointerdown/pointermove/pointerup` + `pointercancel`
- `touch-action:none` on `.sc-stage` and `.sc-frag`; `touch-action:manipulation` on `.stool`
- `getBoundingClientRect()` called live at drag-start (not cached) — coordinates match resized canvas
- Removed old non-standard `@media(max-width:800px)` and `@media(max-width:560px)` playground breakpoints

#### Visitor gallery — Stage 4 (phone <768px, tablet 768–1023px)
- **DOM restructure:** `.gal-leave` moved inside `.gal-head` → `gal-intro-row`, before `.gal-grid`, so reading order is title → subtitle → invitation → cards at all sizes
- Phone: `.gal-intro-row{flex-direction:column}` stacks subtitle and invitation vertically; full-width button, 24px gap above/below invitation; no CSS ordering needed
- Tablet + desktop (≥768px): `.gal-intro-row{display:flex;justify-content:space-between;align-items:flex-start;gap:32px}` — subtitle left, invitation right; `gal-leave{text-align:right;padding-top:8px;max-width:40%}` aligns text top with subtitle
- Invitation text: DM Sans 16px/400/1.5/`#6B6B73`; button: DM Sans 16px/500, `#18181B` bg, `#F9F7F2` text, `0 24px` padding, 48px min-height, 28px radius, content-sized on desktop/tablet
- Right edge: `.gal-leave` right edge aligns with `.gal-grid` right edge (measured 1288px at 1440px viewport) ✓
- 32px gap to grid: `.gal-head{padding-bottom:32px}` — applies whether invitation is shown or hidden
- When invitation hidden: no empty column; `.gal-intro-row` shows subtitle only, 32px gap maintained ✓
- Removed: `border-top`, `text-align:center`, `padding:28px 0 80px` from old `.gal-leave`
- Removed: `#pg-gallery .wrap{display:flex;flex-direction:column}` and `order:` from phone breakpoint (no longer needed with correct DOM order)

#### Stage 4 verification — browser-measured at key breakpoints
- **390px**: 1-col grid, full-width button, stacked layout ✓
- **768px**: 2-col grid, two-col intro row, invitation above cards ✓
- **1024px**: 4-col grid, two-col intro row ✓
- **1440px**: 5-col grid, invitation top and right edges aligned with subtitle and grid ✓; mouse drag works; stool 30px unchanged ✓
- **Hidden state (1440px)**: 32px gap subtitle-to-grid, no empty column ✓
- **Back and Skip from gallery-origin onboard**: both return to gallery ✓ (browser-simulated)
- **Physical device unverified**: touch scroll suppression in stage, pointer cancel from OS interrupts, `env(safe-area-inset-*)` insets

## Final whole-site verification — COMPLETE (2026-11-28)

**Checkpoint commit:** `810508c` (Stages 3–4)  
**Tested in:** Chrome (Chromium) via browser emulation, localhost:4321

### Viewports verified (13 total)
- **320×740** — no overflow, entry/home render ✓
- **375×812** — no overflow ✓
- **390×844** — full pass (all pages/sections) ✓
- **390×600** — no overflow, entry scrollable ✓
- **430×932** — no overflow ✓
- **768×1024** — no overflow (testimonial carousel cards clipped by `.glide-outer overflow:hidden`, cannot scroll horizontally) ✓
- **820×1180** — no overflow ✓
- **844×390** — no overflow, tablet nav (hamburger) ✓
- **960×1440** — no overflow ✓
- **1023×900** — hamburger visible, desktop links hidden, gallery intro flex row ✓
- **1024×900** — desktop links visible, hamburger hidden ✓ (breakpoint boundary confirmed)
- **1032×1376** — no overflow, desktop nav ✓
- **1440×900** — no overflow, desktop nav, gallery right-edges aligned ✓

### Navigation journeys (real clicks)
1. Start → Enter → onboard ✓
2. Back on onboard (entry-origin) → entry ✓
3. Skip on onboard (entry-origin) → home ✓
4. Gallery → Add yours → onboard (gallery-origin) ✓
5. Back on onboard (gallery-origin) → gallery ✓
6. Skip on onboard (gallery-origin) → gallery ✓
7. Hamburger → Playground → navigates, sheet closes ✓
8. Hamburger → Visitor gallery → navigates, sheet closes ✓
9. Footer "Back to start" → entry ✓
10. Case study "Next" (Skin Buddy → StatsBoost) ✓
11. Case study links: StatsBoost has Previous (Skin Buddy) + Next (Replay) ✓

### Hamburger nav
- Opens bottom sheet with all items (My work active on home) ✓
- Escape key closes ✓
- Focus trap: Tab/Shift+Tab cycles within sheet, `role="dialog"`, `aria-label="Navigation menu"` ✓
- `aria-hidden="false"` on sheet when open, `"true"` when closed ✓
- Resize to ≥1024px closes sheet ✓

### Phone hero
- 6 RACHIT letters cycling at 390×844 ✓
- Timer (`phHeroTimer`) active on home, cleared on nav away ✓
- Reduced motion: `phHeroCycleStart()` returns early when `prefers-reduced-motion:reduce` ✓
- Hero stops cycle on resize to ≥768px ✓

### Project cards
- Phone (390px): 1-col, overlay always visible (opacity:1, relative) ✓
- Tablet (768px): 2-col, overlay always visible ✓
- Desktop (1024px): overlay opacity:0 (hover-only), absolute ✓

### Playground
- Phone: 1-col grid, stool 44×44px ✓
- Tablet (768px): 2-col grid, Script card `grid-column:1/-1` (full width), stool 44×44px ✓
- Desktop (≥1024px): stool 30×30px (tablet override reverts) ✓

### Gallery invitation
- Phone (390px): stacked layout, full-width button, correct DOM order ✓
- Tablet/Desktop: flex row, invitation right-aligned, right edge = grid right edge ✓
- gal-leave button: "Add yours →" navigates to onboard with `obPrevPage:'gallery'` ✓

### About photo strip (wspPhotoResize)
- Equal heights at every breakpoint (all 17 slides same height) ✓
- Phone: `Math.min(220, availW/maxRatio)` → 172px at 390px (landscape photo caps it) ✓
- Tablet (768px): 280px exactly ✓
- Desktop (≥1024px): inline styles cleared, CSS `height:360px` takes over ✓
- Lazy loading: `loading="lazy"` on all strip images ✓

### Forms / onboard
- Empty name: submit with no name stays on onboard, does not navigate ✓
- Onboard phone layout: Back + Skip in nav row (top), full-width submit button ✓

### Accessibility
- No console errors throughout session ✓
- Hamburger: `aria-label="Menu"` ✓
- Playground stools: all have text content (emoji symbols), no unlabelled controls ✓
- Project cards: `role="button"`, `tabindex="0"`, `onkeydown` Enter handler ✓
- Sheet dialog: `role="dialog"`, `aria-label="Navigation menu"`, focus returns on close ✓
- Reduced motion: CSS `animation/transition` zeroed globally + JS guards on hero cycle and photo resize ✓

### Notes / known non-issues
- Testimonial carousel: `adj-right` card extends slightly beyond viewport in DOM, but `body` has `overflow-x:hidden` and `glide-outer` has `overflow-x:hidden`; page cannot scroll horizontally ✓
- Photo strip heights at phone lower than 220px target — this is correct behaviour: `wspPhotoResize()` caps at `availW/maxRatio` to maintain landscape photo aspect ratios
- **Physical device unverified**: touch scroll suppression in Playground stage, pointer cancel from OS interrupts, `env(safe-area-inset-*)` insets
