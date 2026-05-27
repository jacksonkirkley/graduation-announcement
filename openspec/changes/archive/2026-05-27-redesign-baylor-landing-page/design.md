# Design — Redesign Baylor Landing Page

## Context

The v1 landing page used a cream + amber palette with Calistoga + Inter typography ("warm editorial" style). Jackson's feedback was that it looked "super basic" and didn't visibly signal Baylor — the actual subject of the announcement. The QR code on the back of his physical card will route family, friends, and mentors to this page, so first-glance recognition of "Jackson is going to Baylor" matters more than a generic warm aesthetic.

The physical card front (Downloads/Grad Announcement.png) is already designed by a photographer: portrait-orientation photo, thin navy frame, cursive "graduate" script overlay, name + high school in serif/sans below. The landing page should feel like a deliberate companion to that artifact, not a separate visual universe.

Current state: one `index.html` exists at the project root with the v1 design. OpenSpec is initialized but no specs exist yet. Photos live in `~/Downloads/Senior Photos/`.

## Goals / Non-Goals

**Goals:**
- The page reads instantly as "Baylor 2026" — color, typography, and a clear Baylor wordmark establish that within the first viewport on mobile.
- The aesthetic complements (does not clash with) the navy-framed, script-accented physical card.
- Faith-centered, gracious tone of the locked personal note is preserved without ornamentation that contradicts Jackson's "confident but not arrogant" voice.
- All design decisions are documented here so the work survives Claude Code restarts and conversation compaction.
- WCAG AA contrast (4.5:1 minimum) on every text/background combination.

**Non-Goals:**
- Building an in-page navigation, multi-section scroll experience, or any interactive elements beyond the single Venmo CTA.
- Adding analytics, tracking, or any third-party scripts.
- Designing or modifying the physical card front. It is already finalized.
- Generating the QR code or deploying to Netlify — both are downstream and tracked separately.
- Adapting the design to be reusable for future graduations or other people. This is single-use.

## Decisions

### 1. Color palette: Baylor Green + Gold on cream
- **Primary (brand):** Baylor Green `#154734`
- **Accent (celebratory):** Baylor Gold `#FFB81C`
- **Background (page):** Warm cream `#FAF7F0` (slightly warmer than pure white, complements green without competing)
- **Surface (cards):** Pure white `#FFFFFF`
- **Foreground (body text):** Deep slate `#0F172A`
- **Muted (labels, footer):** Warm grey `#6B6B6B`
- **Border:** Cream-tinted `#E8E2D5`

**Rationale:** Baylor's official athletic and university brand uses this green/gold combination. Using both — rather than only one — makes the page unambiguously Baylor-coded. Cream rather than pure white prevents the green from looking corporate-cold and matches the warmth of Jackson's locked note.

**Alternatives considered:** (a) Pure white background — rejected, too clinical against deep green. (b) Green background with cream cards — rejected, makes long-form note text harder to scan on mobile (small phone screens with reversed contrast fatigue the eye). (c) Cream + gold only with green as accent — rejected, doesn't establish Baylor identity strongly enough; gold alone reads as generic luxury.

**WCAG verification:**
- Slate `#0F172A` on cream `#FAF7F0` → ~16:1 ✓ (AAA)
- White `#FFFFFF` on green `#154734` → ~9.5:1 ✓ (AAA)
- Green `#154734` on gold `#FFB81C` → ~5.3:1 ✓ (AA) — this is the CTA combination
- White on gold → ~1.8:1 ✗ — explicitly avoided; gold buttons must use dark green/slate text

### 2. Typography: Playfair Display + Inter + Pinyon Script
- **Display heading (name, "BAYLOR UNIVERSITY"):** Playfair Display, weights 500/600
- **Body and labels:** Inter, weights 400/500/600
- **Script accent (one ornamental phrase only):** Pinyon Script, weight 400

**Rationale:** The ui-ux-pro-max typography database ranked "Classic Elegant" (Playfair Display + Inter) as the top match for "elegant, sophisticated, timeless, premium, editorial." Playfair's high-contrast strokes feel celebratory and refined — appropriate for a graduation milestone — while Inter handles all body and UI text cleanly at every size. Pinyon Script is added in a single decorative spot ("Class of 2026") because the physical card's "graduate" wordmark uses a similar copperplate-style cursive; this small echo visually links the two artifacts.

**Alternatives considered:** (a) Cormorant Garamond + Libre Baskerville (all-serif "Editorial Classic") — rejected, all-serif feels too literary/bookish for a personal milestone page. (b) Cinzel + Josefin Sans ("Real Estate Luxury") — rejected, Cinzel reads as too formal/Roman-monumental. (c) Keep v1 Calistoga + Inter — rejected, Calistoga reads as casual/friendly which undercuts the "stepping into adulthood" tone. (d) No script font, use Playfair italic for the accent — held as fallback if Pinyon ships visual issues on Android.

**Font budget:** Playfair Display (2 weights) + Inter (3 weights) + Pinyon Script (1 weight) totals ~70KB compressed via Google Fonts CDN with `display=swap`. Acceptable for a single-page personal site.

### 3. Layout pattern: Minimal Single Column with hero photo
- Section order: Top gold/green accent stripe → Hero photo → Name + Baylor lockup → School details card → Personal note → CTA → Footer → Bottom accent stripe.
- Max content width: 600px, centered.
- Mobile-first; all spacing uses `clamp()` to scale smoothly to desktop.

**Rationale:** The ui-ux-pro-max landing-page database confirms "Minimal Single Column" as the right pattern for a page with a single CTA, no navigation, and a clear mobile-primary use case. The page is short (single viewport on desktop, ~1.5 viewports on mobile) so progressive disclosure or multi-section scroll patterns aren't needed.

**Alternatives considered:** (a) Hero + Testimonials + CTA — rejected, no testimonials are appropriate here. (b) Scroll-Triggered Storytelling — rejected, the personal note is one short moment, not a narrative arc.

### 4. Visual identity: Baylor wordmark lockup + decorative accents
- **Wordmark:** "BAYLOR UNIVERSITY" set in Playfair Display, all-caps, letterspaced, with a 2px gold horizontal rule beneath the year ("CLASS OF 2026") above the name.
- **Top/bottom accent stripes:** Thin (4px) horizontal bars in Baylor gold across the top and bottom of the page — frames the content like the navy frame on the physical card without literally copying it.
- **Dividers:** Hairline rules in soft border-color between school details rows; a single gold short rule (~48px wide, centered) as a flourish between the wordmark and the personal note.
- **Photo frame:** Portrait photo at 3:4 ratio in a rounded rectangle (12px radius) with a 1px green border and subtle drop shadow. No tints or filters applied.

**Rationale:** University announcement aesthetics traditionally use thin decorative framing and centered typographic lockups (graduation programs, diplomas, university letterhead). Mirroring those conventions makes the page feel ceremonial without being heavy-handed. The top/bottom stripes echo the card's navy frame in geometry while swapping to Baylor gold, creating visual continuity without redundancy.

**Alternatives considered:** (a) Full Baylor seal/crest image — rejected, university seal usage requires permission and would crowd a personal page. (b) "BU" monogram — rejected, less recognizable to non-alumni recipients; the full word "BAYLOR" is unmistakable. (c) Laurel wreath SVG flanking the name — rejected, leans toward cliché yearbook visual.

### 5. Hero photo selection
- **Primary:** `JMKClassof2026-71.jpg` — navy suit + white shirt headshot, golden-hour light, oak tree backdrop. Strong portrait, polished, smile is warm, scales well to small mobile viewports.
- **Secondary (deferred):** No second photo on v2. The physical card front already features the guitar/water portrait; repeating photos across card front and landing page back would feel redundant. A single strong headshot on the landing page creates a clear "this is the same person, formally now" beat.

**Rationale:** The headshot is the most "stepping into the next chapter" image in the set. The guitar shot lives on the card front, the letterman jacket is high-school-coded, and the field/jacket shots are excellent but less formal. The headshot earns the hero slot.

**Alternatives considered:** Adding `JMKClassof2026-347.jpg` (guitar + cross necklace) as a secondary photo lower on the page — deferred to v3 if the user wants more personality after seeing v2.

### 6. CTA styling
- Gold (`#FFB81C`) full-width button with dark Baylor green text (`#154734`), Inter 600, 17px, 12px border radius, generous 18px vertical padding. Hover state darkens gold to `#E5A300`.
- Heroicons gift outline SVG, 20px, sized to button text.
- Focus-visible: 3px solid green ring, 3px offset.

**Rationale:** Gold-on-green inverts the heading color relationship, which keeps the button visually distinct from any other heading text and ensures it reads as "the action." Black-on-gold would also work but green-on-gold ties back to the brand lockup more cleanly.

### 7. Motion and accessibility
- All transitions ≤ 200ms.
- `prefers-reduced-motion: reduce` collapses all animations to ~0ms.
- All interactive elements have visible focus states.
- All decorative SVGs marked `aria-hidden`.
- The single photo has descriptive alt text (`Jackson Kirkley, Class of 2026`).

## Risks / Trade-offs

- **[Three font families adds page weight]** → Mitigation: limit weights loaded (only the specific weights used), use `display=swap` so text renders immediately in fallback fonts while custom faces load. Total weight stays under 80KB.
- **[Strong school colors could overpower the personal note]** → Mitigation: green and gold are confined to accents, the wordmark, and the CTA. The body of the page (note, photo, school card) sits on cream/white surfaces with neutral typography, so the colors anchor identity without dominating the reading experience.
- **[Pinyon Script may render unevenly on older Android browsers]** → Mitigation: keep the script accent limited to one short phrase ("Class of 2026"); if rendering proves problematic, fall back to Playfair Display Italic without disturbing layout.
- **[Photo is portrait-orientation; landscape framing would crop awkwardly]** → Mitigation: define a fixed aspect-ratio container with `object-fit: cover` so any photo Jackson later swaps in will degrade gracefully.
- **[Generic stock "graduation-y" decorative elements (laurels, mortarboards) would cheapen the design]** → Mitigation: explicit non-goal. All decoration is typographic or geometric (rules, stripes, borders) — no thematic illustrations.

## Migration Plan

1. Copy `~/Downloads/Senior Photos/JMKClassof2026-71.jpg` to project root as `photo.jpg`.
2. Rewrite `index.html` end-to-end with the new design (CSS embedded, single file, no build step).
3. Open in the local browser via `open index.html` for visual verification at mobile + desktop widths.
4. Iterate based on Jackson's feedback before any deployment.
5. Archive this OpenSpec change once Jackson approves the result.

Rollback: previous `index.html` content is captured in this conversation's history and in git if/when initialized. A full rewrite is acceptable because the page is single-use and the change is bounded.

## Open Questions

- Whether to add a second photo (guitar/cross) lower on the page once Jackson sees v2. Deferred to a follow-up change if requested.
- Whether to use Baylor's exact "BU" diamond mark or stick with the typographic "BAYLOR UNIVERSITY" wordmark. Defaulting to the wordmark for clarity and to avoid trademark concerns; if Jackson prefers the visual mark, a follow-up change can swap it in.

---

## Revision after first implementation review

After v2 (cream-dominant, framed portrait headshot) shipped, Jackson's feedback was: "too much dead space, not enough Baylor green, photo should be incorporated into the background and larger, the suit headshot is for LinkedIn — don't use it as the headliner, multi-photo scroll is welcome." These revised decisions supersede the originals where they conflict.

### R1. Full-bleed hero with green overlay
The hero is now a **full-bleed photo at the top of the page** with a dark Baylor green gradient overlay (top: rgba(21,71,52,0.35), bottom: rgba(21,71,52,0.85)) so eyebrow/name/wordmark text in white sits legibly over the image. On mobile the hero fills ~85vh; on desktop it caps at ~720px tall and is constrained inside the 600px container with rounded corners (or stays full-bleed and centered, depending on aesthetic). The framed-portrait approach from the original design is discarded.

### R2. Hero photo selection changed
The suit headshot (JMKClassof2026-71) is reserved for LinkedIn and not used here. **New hero: JMKClassof2026-426** — lake + golden hills + navy jacket + cross necklace + golden-hour light. Captures "looking ahead" and faith identity simultaneously, with warm tones that complement Baylor gold.

### R3. Multi-photo carousel
A horizontal scroll-snap strip lower on the page presents three additional photos: JMKClassof2026-289 (field/wildflowers), JMKClassof2026-347 (guitar + cross), JMKClassof2026-32 (Rio Americano green+gold letterman — visually rhymes with Baylor's colors). No JavaScript; native CSS scroll-snap with `overflow-x: auto` on a flex row.

### R4. Color balance shifted toward green dominance
The page now alternates Baylor green sections (hero overlay, CTA section) with cream sections (long-form note, photo strip background) instead of being cream-dominant. Approximate split: ~45% green-overlaid imagery, ~30% cream surfaces for readable text, ~10% solid green for the CTA section, ~15% white card surfaces.

### R5. Wordmark and details consolidated
The wordmark subtitle ("Finance · Business Scholars") and the school details card row data overlapped. The wordmark moves into the hero overlay as "BAYLOR UNIVERSITY · CLASS OF 2026" all-caps with letterspacing. The school details card is preserved separately for the formal Major/Program/Move-in rows.

### R6. Photo optimization in scope
Photos are now resized to ≤1600px max dimension at JPEG q82 via macOS `sips` so the total page weight stays under 1.2MB. Hero is 370KB, each carousel image ~200KB.

---

## Revision after second implementation review (polish pass)

After v3 (full-bleed hero with green overlay + carousel + green CTA) shipped, Jackson's feedback was: "photos aren't spaced great, want it to look more professional and polished — call on the design skill and research renowned sites like Apple." Research findings from Apple, Stripe, Linear, Vercel, NYT Wedding announcements, and Read.cv synthesized into the following revisions, which supersede v3 details where they conflict.

### R7. Hero overlay: lighter and neutral
Drop the heavy green/gold overlay (it was "fighting the photo"). Replace with a subtle bottom-only black gradient: `transparent 0% 55%, rgba(0,0,0,0.45) 80%, rgba(14,51,36,0.85) 100%`. The photo reads true through the top 55%, the bottom 45% darkens for text legibility. Green tint only appears in the deepest bottom slice where the eyebrow/name/wordmark sit. Premium = restraint, not stamping.

### R8. Quiet display weight
Hero name moves from `font-weight: 700` to `font-weight: 500`. Apple, Linear, Vercel all use weight 500 (not bold) on display sizes — heavier bold reads templated. Letter-spacing tightens from `-0.02em` to `-0.025em` for large sizes.

### R9. Modular type scale
All font sizes pull from a fixed ratio-1.25 scale: `0.75 / 1 / 1.125 / 1.5 / 2 / 3 / 4.5 / 6rem`. No arbitrary clamp values that don't snap to the ladder. Hero name uses `clamp(3.75rem, 14vw, 6rem)`.

### R10. Single cream surface; no hard jumps
The middle of the page (school card, note, carousel) sits on one continuous warm cream `#FAF7F0`. No white cards inside, no color jumps between sections. Section boundaries use hairline rules `rgba(0,0,0,0.08)` or pure whitespace, never block color changes. Hard color breaks only occur at hero→cream and cream→green-CTA boundaries.

### R11. Body copy refined for readability
Personal note moves to `font-size: 1.125rem`, `line-height: 1.7`, with the content column capped at `max-width: 38rem` (~65 char measure). Editorial-grade reading rhythm.

### R12. Carousel snap-to-center with peek
- `scroll-snap-type: x mandatory`, `scroll-snap-align: center` on each item.
- Items: `flex: 0 0 76vw` on mobile, fixed `300px` on desktop.
- Rail: `scroll-padding-inline: 12vw` on mobile so adjacent items peek symmetrically.
- Gap: `clamp(1rem, 2vw, 1.75rem)`.
- Item border-radius reduced from 14px to 8px (Apple uses ~8px on media; 16px+ reads consumer-app, not editorial).
- Uniform 3:4 aspect ratio across all carousel items (already in v3, retained).

### R13. Doubled section padding
Middle sections move to `padding-block: clamp(5rem, 10vh, 8rem)` (up from v3's clamp(3rem, 9vw, 4.5rem)). CTA section uses similar generous padding. Vertical rhythm is the primary spacer, not color shifts.

### R14. Accent restraint (90/10)
Green and gold appear only as: (a) hero gradient bottom tint, (b) Pinyon Script eyebrow accent in gold, (c) one short gold flourish rule on the page total, (d) green CTA section background, (e) gold CTA button. All other surfaces and borders are neutrals (cream + slate + rgba black hairlines). Removes the green photo border, green left-border on school card, and duplicate gold flourishes from v3.

### R15. Single editorial signature touch
The Pinyon Script "Class of 2026" eyebrow is retained as the one "soulful" detail that echoes the cursive on the physical card. All other decorative elements consolidated or removed so the page has one signature flourish, not five.

---

## Audit pass (against ui-ux-pro-max UX guidelines)

After the design pivoted multiple times and the page neared production readiness, a systematic audit ran the current `index.html` against the skill's UX guidelines database (99 rules) and pre-delivery checklist. These decisions document the resolution of every issue found.

### A1. Hero `srcset` for responsive image delivery
Critical issue: the hero was a single 6MB JPEG served to all viewports. Per the skill's "Image Optimization (HIGH severity)" rule, that's "4000px image for 400px display." Now serves three sizes via `srcset`:
- `photo-hero-1200.jpg` (1200×1800, ~324KB) — phones
- `photo-hero-2000.jpg` (2000×3000, ~745KB) — tablets and standard desktop
- `photo-hero.jpg` (2624×3936, ~4MB) — retina desktop

`sizes="100vw"` declared so the browser picks the right variant based on viewport × device-pixel-ratio. Mobile users get an ~80% smaller payload; retina-desktop users still see the full-resolution image for maximum sharpness, per Jackson's "as sharp as possible" priority.

### A2. Hero loading hints
Added `fetchpriority="high"` (LCP signal) and `decoding="async"` (off-main-thread image decode) to the hero image. Browser knows to prioritize the hero over below-fold assets without blocking layout.

### A3. Clear `will-change` after entrance
The `[data-reveal]` rule had `will-change: opacity, transform` permanently, promoting elements to GPU compositing layers indefinitely. Added `will-change: auto` to the `.is-revealed` state so the property releases after the entrance animation completes. Memory and rendering cost drop back to baseline.

### A4. Hero uses `min-height` not `height`
Per the skill's "Viewport Units (Medium)" rule, fixed `height: 100vh/dvh` can clip content on older mobile browsers with shrinking chrome. Switched to `min-height: 100dvh` (with `100vh` fallback) so the hero is guaranteed full-screen at minimum but can grow if needed.

### A5. Skip-to-content link
Added a visually-hidden "Skip to content" link as the first focusable element in `<body>`, anchored to `#content` on the `<main>` element. Screen reader and keyboard users can bypass the hero photo and jump straight to readable content. Link is positioned offscreen via `transform: translateY(-150%)` and slides into view on focus.

### A6. `decoding="async"` on all images
Applied to all carousel images so image decoding never blocks the main thread. Pairs with `loading="lazy"` already in place.

### A7. Removed `image-rendering: -webkit-optimize-contrast`
That property is WebKit-specific and is now widely considered a footgun on retina displays — can produce subtle pixel sharpening artifacts. Removed entirely. Browsers handle natural-image scaling correctly by default.

### A8. Desktop scrollbar affordance on carousel
The carousel hides its scrollbar via `scrollbar-width: none` for touch devices, but on desktop (devices with `hover: hover` and `pointer: fine`) a thin 6px scrollbar is now visible. Users with a mouse can see the scrollable affordance instead of guessing.

### Audit verdict
After fixes, the page passes the skill's pre-delivery checklist on every HIGH-severity item:
- Mobile-first responsive ✓
- Viewport meta ✓
- Touch target ≥44px (CTA ~50px) ✓
- WCAG AA contrast on all text/background pairings ✓
- Keyboard navigation works, focus states visible ✓
- Alt text on all images ✓
- `prefers-reduced-motion` respected ✓
- Hero is sharp on every device (srcset + full-res for retina) ✓
- Image lazy-loading below the fold ✓
- Font `display=swap` ✓
- No layout shift (aspect-ratio on photo containers) ✓
- Skip link present ✓
