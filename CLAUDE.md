# Standing notes — Rachit Patni portfolio

## Project layout (added at setup, 2026-11-05)

- `site/` is what gets published. `site/index.html` is the master copy of the website (it was `portfolio_17.html` in the handoff, renamed so hosts serve it as the home page). The tab icons and link preview pictures sit beside it.
- `reference/` holds the handoff materials. They are not published.
  - `reference/phone-designs/`: the chosen phone designs (the brief calls this folder `phone-designs/`; open its `index.html` first).
  - `reference/link-preview/link-preview-final.html`: link preview HTML, webmanifest and checklist.
  - `reference/portfolio-design-system-v2.pdf`: the design system.
  - `reference/HANDOFF-BRIEF-for-Claude-Code.md`: the original brief, unchanged.
- Not supplied, by Rachit's choice: `design-system-source/` (not needed here), the older option mockups (`phone-nav-options.html`, `phone-rachit-options.html`, `phone-testimonials-before-after.html`, `laptop-quote-cutoff.html`) and `portfolio-gallery-test.html`. For gallery layout testing, add sample cards locally instead.
- The original files are kept untouched on the Desktop at `Rachit/Portfolio/Website/Deployment` as a backup. This folder is the master from now on.

The handoff brief follows, unchanged.

---

# Handoff brief — Rachit Patni portfolio

Paste this whole file into Claude Code at the start of the session. Then ask Claude Code to **save it as the project's standing notes file** (`CLAUDE.md` in the project folder), so these rules are loaded at the start of every future session and Rachit does not have to paste them again.

---

## 0. What this is

- A single-page personal portfolio for **Rachit Patni, UI/UX designer, UK**. It is one HTML file: `portfolio.html` (about 1.6 MB, animated project thumbnails and fonts are inline).
- **Who it is for:** recruiters and hiring managers, who skim. The one goal is that they get in touch (email or LinkedIn). Everything should be simple, fast and clear.
- **Design rules live in** `portfolio-design-system-v2.pdf`. The page source for its changed pages is in `design-system-source/`.
- The site is built and approved. **Your job is to fix the items below, deploy it, and add content later. It is not to redesign.**

## 1. Ground rules from the owner (follow these strictly)

1. **Do not make design decisions.** If something needs a design choice (copy, look, layout), ask Rachit first. A mockup or before/after comes before any visual change.
2. **Change only what is listed.** Do not "tidy up" other parts. Make small, targeted edits, not rewrites.
3. **Talk to Rachit in plain words.** Do not explain with code terms (class names, CSS properties, tags). Describe what he will see on screen.
4. **Check your work before saying it is done.** Test in a real browser, and on a phone-size screen. If you cannot see the rendered page yourself, say so plainly and ask Rachit to check it and send a screenshot. Do not guess how a visual change looks.
5. **One master copy.** From now on the repository is the master. If Rachit changes something in his chat with Claude, he will hand you the exact change or the updated file. Do not overwrite it with an older copy.
6. Rachit is not a developer. Keep questions to him short and give a clear recommendation with each.
7. **For any visual change, show a before and after first** and wait for Rachit's approval before changing the site. He will ask for this every time, but do it without being asked.

## 1.5 Ask Rachit these at the start of the session

Rachit has asked you to ask him. He will answer when you do.
1. **Which case studies are ready to publish?** (Skin Buddy, Replay Cinema, StatsBoost.) He will say, and give you the content. See 2.3.
2. **Where should the site be hosted, and at which address (domain)?** Do not assume.
3. **The link preview items:** these are now decided and all files are ready. See `link-preview-final.html` and section 2.4. Only the domain placeholder needs filling in once the domain is confirmed.
4. **The photos:** the "What shaped me" photos and his About photo (see 2.1 and 2.2). He will provide them during development.
5. **Emeka Nnalue's testimonial:** it is cut off on every screen size today. **Rachit will trim the quote himself, so the laptop cards do not change.** He will give you the shortened text. After you apply it, check that no quote is cut off at laptop width. The phone fix (see 2.5) still goes ahead.
6. **Tablets with touch screens:** no hover there. Keep the laptop version of the RACHIT headline, or use the tap version? (See 2.9.)

## 2. Fix BEFORE publishing (these look broken or unfinished on a live site)

### 2.1 "What shaped me" photos will not load
The About section has a photo carousel. Its six photos point to files that only exist on the build machine (`/mnt/user-data/uploads/WhatsApp_Image_2026-07-18_at_15_40_57.jpeg`, `..._15_46_17`, `..._15_54_43`, `..._15_55_49`, `..._16_00_26`, `..._16_01_42`). On a live site they will show as empty boxes.
- Rachit will supply the image files. Put them in the site's files and point the carousel at them (or embed them, as the project thumbnails are).
- The carousel structure is correct. Do not change how it looks or moves.
- The photo list has **6 entries** (the sixth caption is "Beyond the work") but the carousel has **5 slides**. Ask Rachit which photos he wants shown before wiring it up.
- Captions in use: Radio studio, MY FM · Mall billboard, Jaipur · Swach Bharat, 2019 · After a college event · Live school event.

### 2.2 About photo is a placeholder
A box with a sparkle symbol sits where Rachit's photo should be. Ask Rachit for the photo. If he does not have one yet, ask whether to hide the box until he does. Do not decide yourself.

### 2.3 Case study pages say "coming soon"
Three pages (Skin Buddy, Replay Cinema, StatsBoost) each say "Full case study coming soon." Each project card on the home page has a "View case study" button leading to them.
- Once the website is published, Rachit will tell you which case study to publish first. Ask him.
- When content arrives, each page needs: a link to the next and previous case study, a "Back to work" link, and the same footer as the other pages.

### 2.4 Link preview and basics. DECIDED and all files ready.
The page has a title ("Rachit Patni — Product Designer") but no description, no preview picture, no tags for sharing, and no favicon. All three are now decided. **Open `link-preview-final.html` first — it has everything: the picture, the icon at all sizes, the full HTML to paste into the page, the webmanifest file to create, and a checklist to run after deploying.**

**What is decided:**
- **Description (115 chars):** Designing products that are genuinely useful for people. Health tech, accessibility and EdTech, based in the UK.
- **Preview picture:** `link-preview-image.jpg` (1200 × 630px). Rachit's photo on the right, his name and role on the left, on a dark background. Already at the correct size.
- **Tab icon (favicon):** RP monogram on a dark rounded square. Files at all required sizes are included.

**Files to put in the site's public folder:** `favicon.svg`, `favicon-512.png`, `favicon-192.png`, `favicon-180.png`, `favicon-32.png`, `favicon-16.png`, `link-preview-image.jpg`, `link-preview-image.png`.

**After adding the files, paste the HTML from `link-preview-final.html` into the `<head>` of `portfolio.html`.** The two placeholders `your-website-address.com` must be replaced with the real domain once it is confirmed. Do not publish with the placeholder still in.

**After deploying, run the checklist in `link-preview-final.html` section 6.** The Facebook debugger is the most reliable way to check that LinkedIn cards work.

### 2.5 Things that run off narrow phone screens (checked at 390px wide)
Checked in a browser at a plain 390px width. On laptop screens all of these must stay exactly as they are. On phones they must fit the screen.
- **The line under the big RACHIT headline** ("Former radio show host — always someone who listens first.") is cut off on both sides. It should wrap onto two lines on narrow screens.
- **The closing quote in About** ("Good design begins with understanding people. Everything else is execution.") is cut off on the right. On its own it makes the page 791px wide on a 390px screen.
- **The line under "Let's talk."** ("Full-time roles, collaborations, or just a conversation over coffee — all welcome.") is cut off on the right.
- **Testimonial cards on phones. DECIDED**, as shown in `phone-testimonials-before-after.html` (real screenshots at 390px: today on the left, the fix on the right). The cards are fixed at 340px wide, so on a phone the front card sits off-centre and runs past the right edge. Fix, on phones only:
  - **Width:** the screen width minus 36px each side (318px on a 390px phone), instead of 340px.
  - **Centred:** the front card is centred on the screen, including the first card. The neighbouring cards still show at the edges, tilted and faded, as on the laptop.
  - **Height:** the cards grow to fit their text, all to the same height (the tallest one's, roughly 50 to 60px taller than today, and never less than today's 420px). **No text may be cut off.** With a fixed height, three testimonials (Emeka, Dorsa and RJ Teena) get cut off at the narrower width.
  - **The carousel's sliding calculation** has the card width and gap built in (340 + 20). On phones it must use the real card width and centre the front card. The side space around the carousel (60px each side) is removed on phones.
  - **Check:** all eight testimonials show in full, and the front card is centred and fully on screen, at 360, 390 and 430px wide. Auto-advance and pause-on-hover are unchanged.
  - **The look of the cards does not change:** colours, accent bar, fonts and tick stay as they are. **The laptop and tablet versions do not change.**
  - **Laptop: no change. DECIDED.** Emeka Nnalue's testimonial is already cut off on every screen size today (`laptop-quote-cutoff.html` shows it). Rachit will trim the quote himself. Do not change the laptop card height. Apply his shortened text when he gives it, then check that no quote is cut off at laptop width.
- **The page ends up wider than the phone.** The two items above, and the off-screen testimonial cards, stick out past the screen edge. Contain them so the page itself is never wider than the screen. On some phones this can show up as sideways panning or the page zooming out. **Check on a real phone.**
- **The mascot sits on top of the "Back to start" button** in the footer on phones. Check and fix so the button can be tapped.
- There are about 14 forced single-line pieces in total. Check each at phone width, and only change the ones that actually overflow.
- **Already fine at every size tested** (360, 390, 768, 1024, 1440px): Visitor gallery, Playground and the three case study pages. **Home at 768 and 1024px** has only been measured, not reviewed by eye, so look at it.

### 2.6 Navigation bugs
1. **Flash when entering the home page.** When the visitor clicks Enter or Skip on the first screen and lands on Home, the top navigation briefly shows a light background for a split second (it can look like it blinks twice). It must be **transparent with white text from the very first frame**, stay that way through the whole dark hero, and switch to the light background with dark text only when the "Some Things I made" section reaches the nav. Several attempts in chat did not fix it (re-checking scroll position, removing the light state before paint, switching off the fade, locking the nav transparent). **Please find the real cause by inspecting the paint sequence frame by frame in browser developer tools.**
2. **"Get in touch" scroll judder.** When the visitor is already on Home and clicks "Get in touch", the page jumps up and down because two scrolls fight each other. It must scroll straight to the contact section only.
3. **"About me" link timing.** It switches page and then scrolls after a fixed 420ms delay, which can fail. It should scroll once the page has finished switching. If the visitor is already on Home, scroll directly.

### 2.7 Visitor gallery only works inside each visitor's own browser. DECIDED: use a shared database, on a free plan.
Visitors fill a name card on arrival (or later from the gallery). Cards are saved in the browser's local storage, so a new visitor sees an empty gallery with only their own card. The gallery link is in the main nav, so this will be very visible.
- **Rachit has decided:** use a shared online database so cards from all visitors show for everyone, on a **free** plan. He wants **you to recommend which one to use.**
- **First, before building anything, give Rachit 2 or 3 free options in plain words** (no code terms), with your recommendation. For each, cover: what it costs and what the free limits are, how hard it is to set up and look after, what happens if the free limit is reached (does the gallery stop working?), how visitors' names and roles are kept safe and whether they are public, and how to stop spam and bad words. **Rachit picks. Do not choose a moderation approach yourself.**
- Each card has: name, optional role, colour, number, date. The visitor's own card must still get the "That's you." chip (keep their own card id in their browser).
- Note that the mascot says "Someone left a card!" on the gallery page even when it is empty.
- For testing the layout, `portfolio-gallery-test.html` is a copy with 8 sample cards pre-filled.
- **The question Rachit will ask you** (answer it first): *"Which free database should I use for the Visitor gallery? Compare 2 or 3 options in plain words: cost and free limits, how hard it is to set up, what happens if the free limit is reached, how visitors' names are kept safe, and how to stop spam and bad words. Then tell me which one you recommend and why."*

### 2.8 Set up safety nets before the first publish
These make every later change, small or large, safe and reversible.
1. **Version history.** Put the project under version control (git) from the very first save. Any change must be undoable, including large ones.
2. **A test address before the live one.** Set up a separate preview address (many hosts give a preview link for each change) so changes are checked there first. The live site changes only after Rachit approves.
3. **Keep new words and photos separate from the site's code.** For new content (case study text, testimonials, photos), keep it as separate content files where practical, so a future redesign only changes how things look and none of the content needs rewriting. Do **not** restructure the existing content before launch unless Rachit asks.

### 2.9 Two phone designs. Both decided.
**Every chosen phone design has its own live file and pictures in the `phone-designs/` folder. Open `phone-designs/index.html` first.** The live files are `phone-navigation-bottom-sheet.html`, `phone-headline-rachit.html` and `phone-testimonials.html`. They show only the chosen versions, at 390px wide. The older mockup files show all the options side by side, so **if they differ from the pictures or from the text in this brief, the pictures and this text win.** The same folder covers the testimonial cards on phones (section 2.5).

**1. Phone navigation. DECIDED: option 3, the bottom sheet.** It is the third column in `phone-nav-options.html`. At phone width the five items currently sit in one cramped row (small text, labels wrapping onto two lines, small tap targets). Replace that row on phones only, as drawn:
- **Closed:** the logo on the left and a menu button (three lines) on the right, with a tap area of at least 44×44px. There is no separate "Get in touch" button in the bar.
- **Open:** the page behind dims. The bar stays visible and the menu button becomes an X. A panel slides up from the bottom with rounded top corners and a small handle. It holds four rows, My work, About me, Playground and Visitor gallery, each 56px tall with a thin divider. The current page is marked with a small terracotta dot. A full-width dark "Get in touch" button sits at the bottom of the panel.
- **Bar colours follow the existing rules:** transparent with white text over the dark top of the page, and light only once "Some Things I made" reaches the nav.
- **Closing (defaults, confirm with Rachit):** tap the X, tap the dimmed area, or tap a link. Pressing Escape also closes it.
- **Accessibility:** the menu button has a clear name ("Menu"), focus moves into the panel when it opens and returns to the button when it closes, and the slide respects the "reduced motion" setting.
- **Where it applies:** phone widths only. Use the site's existing phone breakpoint (640px) unless Rachit says otherwise. **Laptop and tablet navigation must not change.**
- Show Rachit a before and after on a phone-sized screen before it goes live.

**2. The RACHIT headline on phones. DECIDED: option 1, one row with the word underneath.** It is the first column in `phone-rachit-options.html` (live, so tap the letters). On the laptop the six big letters don't fit across a phone screen and the last letter (T) falls off the right edge, and phones have no hover to reveal the words. Replace the layout on phones only, as drawn:
- **The letters:** all six sit in one row across the full width of the screen with a 16px margin each side (text size about 92px on a 390px phone). They must scale with the screen so all six fit on every phone width, from about 360px up. Keep the laptop look: cream letters with a terracotta offset shadow, and the active letter in terracotta with a soft light shadow.
- **The word:** the word for the active letter appears underneath the row, one at a time, about 30px below it, in a body font at about 36px. Its first letter is cream and bold, and the rest is terracotta (for example **C**rafting).
- **Behaviour:** it cycles through the six words by itself every 1.4 seconds, as on the laptop. Tapping a letter shows that word and holds it for 4 seconds, then the cycle carries on.
- **Tap size:** every letter needs a tap area at least 44px wide, including the narrow "I". The tap area can extend into the space around the letter.
- **The sticker** says "Tap a letter!" on phones. On the laptop it still says "Hover over!".
- **The line at the bottom** ("Former radio show host — always someone who listens first.") wraps onto two lines, centred. This is the same fix as in section 2.5.
- **Accessibility:** keep the existing `aria-label` on the headline. The letters are buttons with clear names. With "reduced motion" switched on, the automatic cycle stays off and a tap is the only way to change the word.
- **Where it applies:** phone widths only. Use the same breakpoint as the phone navigation (640px). **The laptop version must not change.**
- **Ask Rachit before building:** tablets with touch screens have no hover either. Do they keep the laptop layout, or get the tap version? Do not decide yourself.
- Show Rachit a before and after on a phone-sized screen before it goes live.

## 3. Can wait until after publishing (do not do before launch unless asked)

- **Testimonial carousel on phones.** It auto-advances every 2 seconds, starts 1.5 seconds after the section is fully in view, and pauses while the mouse is over the cards or the arrows. For touch screens the proposal is: tapping a card pauses it for 4 seconds then it resumes, and swiping left or right moves one card. The arrow buttons stay. **Confirm the touch behaviour with Rachit before building.** Note: the carousel's sliding calculation has the card width and gap built in (340 + 20). If the gap ever changes, update that number too.
- **"Script" tool in Playground on touch screens.** Currently mouse-only. Proposed: tap a letter fragment to select it, then tap the canvas to place it; tapping a placed piece selects it for the size, rotate, flip and colour buttons. Desktop drag-and-drop must stay exactly as it is. Confirm with Rachit first.
- **Small labels above headings.** Their styles differ from section to section. Rachit wants them consistent, but the look must be decided with him first.
- **Speed.** The single 1.6 MB file carries images inline. Splitting images and data into separate files would make the first load faster. Only do this if Rachit asks.
- **Hosting and domain.** Ask Rachit where he wants it hosted and which address to use. His email address is hello@rachitpatni.com, but do not assume the domain.

## 4. Decisions already made. Do not change these.

**Navigation and structure**
- The main nav has: My work, About me, Playground, Visitor gallery, Get in touch.
- No "Send an email" button and no CV or resume link, by Rachit's choice.
- The footer is the same on every page: email with a Copy button, LinkedIn, and "Back to start". Case study pages are included.

**Locked behaviours**
- The first (entry) screen text sequence completes in 4.5 seconds, and the Enter and Skip buttons appear at 2.6 seconds.
- The two "managed me directly" testimonials (Verena, Holly) come first in the carousel and show a terracotta tick before their "managed Rachit directly" line.
- The mascot has no close button, by choice.

**Spacing standard** (details on page 5 of the design system PDF)
- 80px above and below main sections.
- 120px between neighbouring sections on the same background (80px below the first plus 40px above the next).
- 12px from a small label to its heading.
- 12px from a heading to its sub copy.
- 32px from a heading or sub copy to the content under it.
- Inner-page headings start 94px from the top of the page.
- Exceptions left as they are (and listed in the design system): card gaps of 20px on the project and testimonial cards, 2px between music players, About me's inner gaps (14px and 20px), Let's talk's label gap (20px), the 72px around "Some Things I made", and the 28px under the headphones sub copy.

**Look**
- Fonts: Baloo 2 (headings), DM Sans (body), Space Mono (small labels).
- Terracotta: `#9c3f29` is the only terracotta allowed for text. `#c8593e` is decorative only, never for text.
- No shadows. Surfaces are separated with 1px borders at 10% opacity.
- The site must meet WCAG 2.2 AA and respect "reduced motion" settings.

## 5. How to check it after deploying (do all of these)

1. Open the live address on a **phone** and on a laptop.
2. Click through the first screen to Home. Watch the top nav the whole way down the page. No flash, correct colours.
3. Scroll to the end of About. Confirm the "What shaped me" photos load.
4. Click each "View case study" button, and "Next" and "Back" on those pages.
5. Open Visitor gallery as a brand-new visitor (private window). Add a card, and confirm the "That's you." chip appears and the card is still there after a reload.
6. Paste the live address into a LinkedIn post draft or a message. Confirm the preview looks right.
7. On a phone, confirm nothing runs off the screen: the headline, the line under it, the closing quote in About, the line under "Let's talk.", and the testimonial cards. Confirm the page never pans sideways or zooms out, and that the "Back to start" button can be tapped.

## 6. After launch: making changes later

### 6.1 Who does what
- **Design questions** go to Rachit's chat with Claude: mockups, wording, spacing choices, case study writing, design system updates.
- **Applying changes to the site and publishing** is Claude Code's job.
- **Hand-off between the two:** Rachit brings you either the exact change (what, where, and the approved numbers) or the updated file. Before you apply it, check it against the current repository so nothing newer is overwritten. **The repository is always the master copy.**

### 6.2 Small UI changes
1. Rachit describes the change, or brings the exact change agreed in chat.
2. Show a before and after. Wait for approval.
3. Make only that change. Check it in a browser and on a phone-size screen.
4. Check it on the test address, then publish after Rachit approves.
5. If the change touches spacing, colours or fonts, tell Rachit that the design system document needs the same update. He will take that to chat.

### 6.3 Major design changes (a redesign, a new look, new page layouts)
1. **Direction first, in chat.** Rachit and Claude agree the new direction with mockups of the key pages (Home, one case study, one inner page).
2. **Update the design system first.** The document is updated to match the new direction **before** any building, so the site and the document never drift apart.
3. **New brief.** Rachit gives you a brief like this one, listing what changes and what must stay.
4. **Build on a separate copy.** Work on a test branch or preview address. The live site does not change.
5. **Rachit checks it** on a laptop and a phone.
6. **Publish only after he approves.** Keep the version history so it can be rolled back.
- For a major redesign, suggest splitting the single 1.6 MB file into separate parts for pages, styles and images, which makes later changes cheaper. **Do not do this before launch, and only with Rachit's agreement.**

## 7. Reference files

| File | What it is |
|---|---|
| `portfolio.html` | The latest site. This is the starting point. |
| `portfolio-design-system-v2.pdf` | The design system, including the spacing rules. |
| `design-system-source/` | Source for the changed design system pages, with a build script. |
| `portfolio-gallery-test.html` | A copy with sample visitor cards, for testing the gallery layout. |
| `phone-designs/index.html` (and the pictures beside it) | **Start here for anything on phones.** The chosen phone designs only: navigation, the RACHIT headline and the testimonial cards. |
| `phone-designs/phone-navigation-bottom-sheet.html`, `phone-designs/phone-headline-rachit.html`, `phone-designs/phone-testimonials.html` | One live file per chosen phone design, each with only the chosen version and its spec. They also work as reference code. |
| `phone-nav-options.html` | The three phone navigation options. Rachit chose option 3, the bottom sheet. |
| `phone-rachit-options.html` | The three phone versions of the RACHIT headline. Rachit chose option 1. |
| `phone-testimonials-before-after.html` | The testimonial cards on phones, today and with the fix. Approved. |
| `laptop-quote-cutoff.html` | Emeka's cut-off quote on a laptop. Rachit is trimming the quote himself, so no laptop change. |
| `link-preview-final.html` | **Start here for link preview.** The final picture, icon, HTML to paste, webmanifest, and post-deploy checklist. All decided. |
| `link-preview-image.jpg` / `link-preview-image.png` | The final 1200 × 630 preview picture, ready to put in the site. |
| `favicon.svg` and `favicon-*.png` | The final tab icon at all required sizes. |
| `link-preview-explainer.html` | Background explainer showing what a link preview is. For reference only. |
