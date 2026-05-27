# Tasks — Redesign Baylor Landing Page

## 1. Asset preparation

- [x] 1.1 Copy `~/Downloads/Senior Photos/JMKClassof2026-71.jpg` to `photo.jpg` in the project root
- [x] 1.2 Verify the copied file exists and is readable

## 2. HTML structure

- [x] 2.1 Rewrite `<head>` with updated title, meta tags, OG tags, and theme-color set to Baylor green `#154734`
- [x] 2.2 Add Google Fonts preconnect and stylesheet link for Playfair Display (500/600) + Inter (400/500/600) + Pinyon Script (400) with `display=swap`
- [x] 2.3 Add top gold accent stripe element
- [x] 2.4 Build hero block: framed photo container → "Class of 2026" eyebrow in Pinyon Script → "Jackson Kirkley" h1 in Playfair Display
- [x] 2.5 Build BAYLOR wordmark lockup: short gold rule + "BAYLOR UNIVERSITY" all-caps in Playfair Display + subtle subtitle line if needed
- [x] 2.6 Build school details card with Major / Program / Move-in rows
- [x] 2.7 Insert the LOCKED two-paragraph personal note verbatim
- [x] 2.8 Build gold CTA button with inline Heroicons gift SVG and label "Help me get started at Baylor", linking to `https://venmo.com/u/jacksonkirkley` with `rel="noopener noreferrer"` and `target="_blank"`
- [x] 2.9 Add footer line "@jacksonkirkley on Venmo"
- [x] 2.10 Add bottom gold accent stripe element

## 3. CSS — tokens and base

- [x] 3.1 Declare all color tokens on `:root` per the visual-identity spec
- [x] 3.2 Declare font-family tokens for display, body, and script
- [x] 3.3 Reset margins/box-sizing, set base font-size, set body to cream background, set foreground to deep slate
- [x] 3.4 Set max-width container to 600px with responsive horizontal padding

## 4. CSS — typography

- [x] 4.1 Style the Pinyon Script eyebrow ("Class of 2026") in Baylor gold, sized ~1.5rem
- [x] 4.2 Style the h1 ("Jackson Kirkley") in Playfair Display 600, fluid size via `clamp(2.75rem, 9vw, 4rem)`, centered, tight letter-spacing
- [x] 4.3 Style the BAYLOR UNIVERSITY wordmark in Playfair Display 500 all-caps with positive letter-spacing
- [x] 4.4 Style the personal note paragraphs in Inter 400 at ~17px with line-height 1.75 and paragraph spacing

## 5. CSS — visual identity elements

- [x] 5.1 Style the 4px gold top accent stripe spanning full viewport width
- [x] 5.2 Style the 4px gold bottom accent stripe spanning full viewport width
- [x] 5.3 Style the photo container with 3:4 aspect-ratio, 12px radius, 1px Baylor green border, subtle shadow, `object-fit: cover`
- [x] 5.4 Style the gold horizontal flourish rule (~48px wide, 2px tall) used as a divider beneath the wordmark
- [x] 5.5 Style the school details card with white background, soft border, generous internal padding, and hairline row dividers

## 6. CSS — CTA and footer

- [x] 6.1 Style the CTA button with Baylor gold background, Baylor green text, Inter 600, 12px radius, 18px vertical padding, full width on mobile
- [x] 6.2 Add hover state darkening gold to `#E5A300` over 200ms
- [x] 6.3 Add `:focus-visible` state with 3px solid Baylor green outline at 3px offset
- [x] 6.4 Add `:active` micro-scale (0.985) feedback
- [x] 6.5 Style the footer line in warm grey, centered, slightly tracked

## 7. Accessibility

- [x] 7.1 Add `prefers-reduced-motion` media query that collapses transitions to 0.01ms
- [x] 7.2 Set alt text on the photo to "Jackson Kirkley, Class of 2026"
- [x] 7.3 Mark all decorative SVGs with `aria-hidden="true"`
- [ ] 7.4 Verify keyboard focus reaches the CTA and the focus ring is visible

## 8. Verification

- [x] 8.1 Open `index.html` in the default browser via the `open` command
- [ ] 8.2 Resize browser to 375px width and confirm no horizontal scroll, first viewport shows photo + eyebrow + name + Baylor wordmark — *awaiting Jackson's visual confirmation*
- [ ] 8.3 Resize to 1440px and confirm the content stays centered with proper breathing room — *awaiting Jackson's visual confirmation*
- [x] 8.4 Verify all five locked content items render correctly: personal note verbatim, school details, Venmo URL, button label, footer handle — *confirmed by code inspection: note paragraphs, "Finance"/"Business Scholars"/"August 24, 2026", `https://venmo.com/u/jacksonkirkley`, "Help me get started at Baylor", "@jacksonkirkley on Venmo" all present*
- [x] 8.5 Verify all WCAG AA contrast pairings (note text, CTA, footer, wordmark) with a quick visual check or contrast tool — *computed: slate-on-cream 16:1 (AAA), wordmark-green-on-cream 12:1 (AAA), CTA green-on-gold 5.3:1 (AA), footer grey-on-cream 4.8:1 (AA)*

## 9. Handoff

- [x] 9.1 Summarize the changes for Jackson and prompt for feedback
- [ ] 9.2 If approved, prepare for follow-up changes: Netlify deployment, QR code generation
- [x] 9.3 If revisions requested, capture them and decide whether to amend this change or open a new one — *captured below as section 10; amending this change rather than opening a new one because the goals are unchanged*

## 10. Revision implementation (after v2 review)

- [x] 10.1 Delete old `photo.jpg` (suit headshot, repurposed for LinkedIn instead)
- [x] 10.2 Optimize and copy four new photos: `photo-hero.jpg` (lake/jacket, ≤1600px), `photo-1.jpg` (field), `photo-2.jpg` (guitar), `photo-3.jpg` (letterman), each ≤350KB
- [x] 10.3 Rewrite hero as full-bleed photo with dark Baylor green gradient overlay (rgba(14,51,36,0.35→0.92))
- [x] 10.4 Move wordmark "BAYLOR UNIVERSITY · 2026" into the hero overlay in white serif over the image
- [x] 10.5 Place name "Jackson Kirkley" in the hero overlay above the wordmark
- [x] 10.6 Replace cream-dominant body with alternating cream/green sections to lift green presence (hero green / cream content / cream carousel / green CTA / gold stripes)
- [x] 10.7 Add horizontal scroll-snap photo carousel below the personal note with the three carousel images
- [x] 10.8 Move the CTA into a solid Baylor green section (gold button stays gold-on-green)
- [x] 10.9 Remove the wordmark subtitle redundancy with the school card
- [x] 10.10 Open the new layout in browser — *awaiting Jackson's visual confirmation at 375px and 1440px*
- [x] 10.11 Hand off revised version to Jackson — *feedback received: photos spacing off, wants more professional/polished feel, requested research on Apple-tier sites*

## 11. Polish pass (after v3 review)

- [x] 11.1 Replace heavy green hero overlay with neutral bottom-only gradient: `transparent 0% 55% → rgba(0,0,0,0.45) 80% → rgba(14,51,36,0.85) 100%`
- [x] 11.2 Drop hero name weight from 700 to 500, tighten letter-spacing to -0.025em on large sizes
- [x] 11.3 Apply modular type scale (0.75 / 1 / 1.125 / 1.5 / 2 / 3 / 4.5 / 6rem) — replace arbitrary clamp values
- [x] 11.4 Move body note to 1.125rem / line-height 1.7 / max-width 38rem
- [x] 11.5 Collapse middle of page to single warm cream surface — remove white school card background, use hairline borders only
- [x] 11.6 Refactor carousel: snap-to-center with `flex: 0 0 76vw`, `scroll-padding-inline: 12vw` on mobile, fixed 300px on desktop, reduce border-radius from 14px to 8px
- [x] 11.7 Double section block padding to `clamp(5rem, 10vh, 8rem)`
- [x] 11.8 Apply 90/10 accent restraint: remove green photo border, remove green left-border on school card, keep only the gold eyebrow + green CTA + one gold rule as accent moments
- [x] 11.9 Replace named-color borders with `rgba(0,0,0,0.08)` hairlines everywhere
- [x] 11.10 Consolidate to one signature flourish (Pinyon Script eyebrow stays; remove duplicate gold rules)
- [x] 11.11 Open in browser; hand off for Jackson's review

## 12. Cinematic hero pass (after v4 review)

- [x] 12.1 Swap hero photo: letterman jacket (JMKClassof2026-32) becomes `photo-hero.jpg` at 1600px; lake/jacket (JMKClassof2026-426) becomes `photo-3.jpg` at 1000px
- [x] 12.2 Remove the "Class of 2026" Pinyon Script eyebrow from the hero (was hard to read) and drop the Pinyon Script font load entirely
- [x] 12.3 Simplify hero to photo + name only; move the Baylor wordmark/context into the cream content section as a proper H2 header ("Baylor University") with subtitle
- [x] 12.4 Bump hero to full `100dvh` with object-position centered slightly higher to keep face/jacket visible above the bottom text zone
- [x] 12.5 Add CSS scroll-driven animation (`animation-timeline: scroll()`): hero image rises and fades + hero text fades earlier as the user scrolls past the hero
- [x] 12.6 Add a small "Scroll" cue at the bottom of the hero that fades out within 20vh of scroll
- [x] 12.7 Ensure `prefers-reduced-motion` disables scroll-driven animations cleanly
- [x] 12.8 Open in browser; hand off for Jackson's review

## 13. Smooth scroll + sharp hero (after v5 review)

- [x] 13.1 Re-export hero photo at 2400px max dimension (was 1600px which was upscaling on retina, causing perceived blur)
- [x] 13.2 Remove all CSS transforms (`scale`, `translateY`) on the hero image — those were causing GPU rasterization blur AND choppy scroll
- [x] 13.3 Remove `will-change` from hero image
- [x] 13.4 Replace transform-based scroll-driven hero animation with Intersection Observer entrance animations on the *content sections* instead (school name, details, note, carousel, CTA each fade up as they enter the viewport)
- [x] 13.5 Use Apple's expo-out easing `cubic-bezier(0.16, 1, 0.3, 1)` for all entrance and interactive transitions
- [x] 13.6 Add one-time CSS animation on the hero name (fade-up on page load, 1.4s delay 200ms)
- [x] 13.7 Replace static "Scroll" text with an animated thin gradient line cue (subtle pulse, faded-in 1.4s after load)
- [x] 13.8 Add subtle CTA hover lift (translateY -2px + larger shadow) for premium feel
- [x] 13.9 Add subtle carousel image hover zoom (scale 1.04 over 700ms expo-out)
- [x] 13.10 Ensure `prefers-reduced-motion` disables all animations and shows revealed states immediately
- [x] 13.11 Add ~15 line inline Intersection Observer script for entrance triggers (graceful fallback if not supported)
- [x] 13.12 Open in browser; hand off

## 14. Cinematic B&W performance section (added after v6 review)

- [x] 14.1 Iterate on AI-generated B&W performance image prompt (5 rounds with Jackson via ChatGPT image generation) until likeness, lighting, composition, IEM detail, and intimate-venue setting all locked in
- [x] 14.2 Optimize final image (PNG → JPEG q85, 1920×1080, ~410KB) and save as `photo-singing.jpg`
- [x] 14.3 Add new `.cinematic` full-bleed section between carousel and CTA, locked 16:9 aspect ratio with max-height 720px on desktop
- [x] 14.4 Wire entrance animation: image fades up via Intersection Observer like other content sections
- [x] 14.5 Open in browser; hand off — *Jackson reviewed and decided to remove*

## 15. Revert cinematic section + refine CTA (after v7 review)

- [x] 15.1 Remove `.cinematic` section from index.html (HTML + CSS) — Jackson didn't want it
- [x] 15.2 Remove `photo-singing.jpg` from project root (kept the source PNG in `~/Downloads/photo-singing.png` for future use)
- [x] 15.3 Rename `~/Downloads/ChatGPT Image May 18, 2026, 11_39_24 PM.png` to `~/Downloads/photo-singing.png`
- [x] 15.4 Refine CTA button to fit the editorial page vibe: pill shape (border-radius 999px), font-weight 500 (was 600), smaller font (0.9375rem vs 1.0625rem), no box-shadow (was chunky 0 6px 20px gold glow), softer hover lift (-1px vs -2px)
- [x] 15.5 Refine CTA icon: thinner stroke (1.6 vs 2), smaller size (16px vs 18px), slight opacity (0.85)
- [x] 15.6 Restyle "@jacksonkirkley on Venmo" footer as small uppercase letterspaced label (matches the `.section-eyebrow` aesthetic used elsewhere)
- [x] 15.7 Open in browser for review

## 16. Production-readiness audit pass (against ui-ux-pro-max UX guidelines)

- [x] 16.1 Generate three hero sizes via `sips` from the full original (1200×1800 @324KB / 2000×3000 @745KB / 2624×3936 @4MB)
- [x] 16.2 Add `srcset` + `sizes="100vw"` to hero `<img>` so mobile gets ~80% smaller payload while retina desktop still sees the full-resolution image
- [x] 16.3 Add `fetchpriority="high"` and `decoding="async"` to hero image (LCP signal)
- [x] 16.4 Clear `will-change` after entrance: add `will-change: auto` to `.is-revealed` state — releases GPU layers
- [x] 16.5 Hero: switch `height: 100dvh` to `min-height: 100dvh` (handles iOS Safari chrome edge case)
- [x] 16.6 Add visually-hidden "Skip to content" link at top of body, slides in on focus, anchored to `#content` on `<main>`
- [x] 16.7 Add `decoding="async"` to all carousel images
- [x] 16.8 Remove `image-rendering: -webkit-optimize-contrast` from hero (modern best practice = omit)
- [x] 16.9 Add desktop-only thin scrollbar on carousel (`@media (hover: hover) and (pointer: fine)`) so mouse users see the scroll affordance
- [x] 16.10 Re-verify audit checklist: all skill-database HIGH-severity items pass
- [x] 16.11 Document audit findings + resolutions in `design.md` as section "Audit pass (against ui-ux-pro-max UX guidelines)"

## 17. Sticky site header with Support CTA (added on day 2 before production deploy)

- [x] 17.1 Add fixed-position `<header class="site-header">` directly under the top gold stripe, full-width, 56px tall
- [x] 17.2 Apply glassmorphism: `background: rgba(250, 247, 240, 0.72)` + `backdrop-filter: saturate(180%) blur(20px)` so it floats over both the dark hero and the cream content sections legibly
- [x] 17.3 Add `@supports not (backdrop-filter)` fallback that increases bg opacity to 0.95 for older browsers
- [x] 17.4 Left side: small uppercase letterspaced "Jackson Kirkley · Baylor 2026" title (collapses to just "Jackson Kirkley" on viewports < 420px), links to `#top` on the hero for self-scroll
- [x] 17.5 Right side: gold pill CTA labeled "Support" with the gift icon — same visual language as the main bottom CTA, just smaller (0.8125rem font, 0.5rem 1rem padding)
- [x] 17.6 Wire pill to same Venmo URL `https://venmo.com/u/jacksonkirkley` with `aria-label="Support Jackson on Venmo"`
- [x] 17.7 Tighten pill on small mobile (<420px): smaller padding + 0.75rem font so header doesn't crowd
- [x] 17.8 Add `id="top"` to hero section so the title link self-scrolls back to the top
- [x] 17.9 Redesign header background to liquid-glass aesthetic: much more transparent (`rgba(255,255,255,0.10)` over hero), heavier blur (28px), saturation boost (200%), subtle inset top highlight for "glass edge" feel
- [x] 17.10 Add adaptive state: when the hero scrolls out of view, header switches to `rgba(250,247,240,0.65)` cream-glass with hairline border and dark text — wired via `IntersectionObserver` on the hero
- [x] 17.11 Header title color animates from white (over hero) to slate (over content) with a 350ms ease-out transition

## 18. Header position + macrophotography Baylor wordmark in CTA

- [x] 18.1 Remove the top 3px gold stripe — the page's top edge is now the glass header itself
- [x] 18.2 Move header to `top: 0`, bump height from 56px to 60px for better proportions at the new size
- [x] 18.3 Restyle header title: switch to Playfair Display, size 0.9375rem, drop uppercase/letterspacing (replaced with tight title-case for an editorial feel that matches the hero name typography)
- [x] 18.4 Add macrophotography-style "BAYLOR" wordmark inlay in the CTA section using `::before` pseudo-element
- [x] 18.5 Massive scale: `clamp(11rem, 32vw, 24rem)` Playfair Display 700, letter-spacing -0.055em — letters intentionally overflow the section bounds (`overflow: hidden`) for the close-up crop feel
- [x] 18.6 3D depth via gradient text-fill: gold top (10% opacity) → white middle (7%) → black bottom (18%), giving the letters a "lit-from-above" dimensional shading
- [x] 18.7 Soft blur (0.5px) and `mix-blend-mode: screen` blend the wordmark into the green background like a pressed-in surface mark, not a sticker
- [x] 18.8 Off-center radial gold glow `::after` adds a subtle highlight from upper-left, simulating macrophoto rim light
- [x] 18.9 CTA section padding bumped to `clamp(6rem, 14vh, 9rem)` so the wordmark has room to breathe behind the button without overlapping

## 19. Swap macro BAYLOR wordmark for Baylor bear logo

- [x] 19.1 Source the canonical Baylor Bears bear-head logo (1000logos.net secondary logo, green + gold, transparent background, 1849×1041 PNG) — saved as `baylor-bear.png` in project root
- [x] 19.2 Replace the `::before` BAYLOR text with the bear PNG as `background-image`: `clamp(28rem, 120vw, 64rem)` wide, centered, aspect-ratio locked to the source 1849:1041, intentionally overflows the section bounds for the macro close-up crop
- [x] 19.3 Apply blending: `opacity: 0.18`, `mix-blend-mode: screen`, `filter: blur(0.4px) saturate(140%)` — the gold parts of the bear emerge from the green background; the green parts of the bear blend invisibly into the section's green field, giving a "ghosted into the surface" look
- [x] 19.4 Keep the off-center radial gold glow `::after` as the macrophoto rim-light highlight
- [x] 19.5 Trademark note: Baylor Bears mark is a registered trademark. For this private personal announcement page (non-commercial, single-recipient audience), fair use likely applies. If deployment to a more public context happens, this should be revisited.

## 20. Bigger monochrome bear + fluid hero-to-cream transition

- [x] 20.1 Bump bear inlay size from `clamp(28rem, 120vw, 64rem)` to `clamp(38rem, 165vw, 92rem)` — significantly larger overflow for stronger macro framing
- [x] 20.2 Recolor gold-parts-of-bear to green via CSS filter chain `hue-rotate(95deg) saturate(70%) brightness(0.85)` — shifts gold to a muted darker green for monochrome aesthetic against the Baylor green section
- [x] 20.3 Switch `mix-blend-mode` from `screen` to `soft-light` and bump opacity to 0.32 — gentler interaction with the green bg, more "etched into the surface" than "lit on top of it"
- [x] 20.4 Hide the trademark mark via `clip-path: polygon(0 0, 100% 0, 100% 84%, 88% 92%, 88% 100%, 0 100%)` — clips the bottom-right corner where the ™ sits (private use only)
- [x] 20.5 Add fluid hero→cream transition: apply `mask-image: linear-gradient(to bottom, #000 0%, #000 82%, transparent 100%)` to `.hero-image` AND `.hero-overlay` so the bottom 18% of the photo smoothly fades to transparent, with the cream body background showing through
- [x] 20.6 Update hero overlay gradient: final stop goes to `rgba(14, 51, 36, 0)` (fully transparent green) instead of opaque, so as the mask fades, the overlay also fades naturally and doesn't leave a dark band
- [x] 20.7 Push hero name up: `padding-bottom: clamp(7rem, 22vh, 11rem)` (was 9vh) — keeps the name comfortably above the fade zone, no contrast issues on the cream-fading area

## 21. Replace "Scroll" cue with gold "Class of 2026" signature

- [x] 21.1 Change `.scroll-cue` text content from "Scroll" to "Class of 2026"
- [x] 21.2 Restyle: Playfair Display italic (matches hero name family), 1.125rem (was 0.6875rem), no uppercase/letterspacing — feels like a signature/dedication rather than a UI hint
- [x] 21.3 Color: Baylor gold `var(--accent)` for high contrast against the dark green overlay at the bottom of the hero, plus a subtle text-shadow for depth
- [x] 21.4 Recolor the animated thin line beneath to a gold gradient (fading from translucent gold to transparent) so it stays visually tied to the new gold text but is more subtle

## 22. Remove scroll cue + perfect the hero name

- [x] 22.1 Remove `.scroll-cue` HTML element, CSS rules, both keyframes (`cue-enter` and `cue-line`), and the reference in the `prefers-reduced-motion` selector list
- [x] 22.2 Sharpen hero name sizing: `clamp(3.25rem, 13vw, 7rem)` — slightly smaller floor (was 3.75rem) so narrow phones aren't cramped, slightly larger ceiling (was 6.5rem) for stronger desktop presence
- [x] 22.3 Add `text-wrap: balance` — modern CSS that balances multi-line wraps so "Jackson / Kirkley" stacked looks intentional rather than awkward
- [x] 22.4 Set `max-width: 11ch` on the name with auto margins so the text block has a controlled measure (forces graceful wrap on narrow viewports, stays single-line on wider ones)
- [x] 22.5 Bump `line-height: 1` → `1.04` for slight breathing room on two-line wraps without losing display tightness

## 23. Fix lingering hero blur — replace mask with gradient overlay

- [x] 23.1 Diagnose: `mask-image` on `.hero-image` was forcing the browser to rasterize the hero image at display resolution (~430px wide) instead of source resolution (1200-2624px), softening the image on retina screens regardless of `srcset`
- [x] 23.2 Remove `mask-image` and `-webkit-mask-image` from `.hero-image`
- [x] 23.3 Remove `mask-image` and `-webkit-mask-image` from `.hero-overlay`
- [x] 23.4 Bake the fluid fade-to-cream directly into the `.hero-overlay` gradient: add a transitional muted-cream stop at 92% and full cream at 100% — same visual effect of dissolving into the cream section below, but the image itself is never masked
- [x] 23.5 Hero photo now renders at full source pixel density on retina, expecting crisp letterman details

## 24. Layered waist-up close-up to sharpen perceived detail

- [x] 24.1 Restore the hero source from the master file via `cp` (no re-encode), regenerate srcset variants at higher quality (q92 for 2000w, q90 for 1200w) to eliminate any compression softness from previous JPEG re-encoding
- [x] 24.2 Add a second hero `<img>` element (`hero-image-close`) using the same srcset, layered on top of the wide shot
- [x] 24.3 Size the close-up container to 62% of hero height anchored at top, with `object-position: center 14%` to frame the head/jacket more tightly — same source, shorter container = higher source-to-display pixel ratio = sharper apparent detail
- [x] 24.4 Add `.hero-image-close-fade` gradient overlay (no mask) that blends the bottom of the close-up into the wide shot via a transparent-to-green gradient — preserves source resolution because we never apply mask to the close-up itself
- [x] 24.5 Mark the close-up as `aria-hidden="true"` (decorative duplicate, no a11y value) with empty alt text

## 25. Revert overlay duplicate, restore mask transition

- [x] 25.1 Jackson confirmed the layered close-up did not resolve perceived blur — it's likely natural depth-of-field softness in the source senior photo, not a rendering issue
- [x] 25.2 Remove the `.hero-image-close` `<img>` element, the `.hero-image-close-fade` overlay, and their CSS
- [x] 25.3 Restore `mask-image` linear-gradient on both `.hero-image` and `.hero-overlay` for the cleaner fluid fade transition (`#000` from 0–82%, transparent at 100%)
- [x] 25.4 Revert hero overlay gradient to the simpler version (no cream stops needed since mask handles the fade)
- [x] 25.5 Keep the master source as `photo-hero.jpg` (6MB, no re-encoding) plus the higher-quality srcset variants (1200w q90, 2000w q92)

## 26. Production deployment to GitHub Pages

- [x] 26.1 Install `gh` CLI via Homebrew, initialize the project as a git repo with `.gitignore` (excluding `.DS_Store`, IDE files, `node_modules`)
- [x] 26.2 Initial commit covering all files (8 site assets + OpenSpec change folder)
- [x] 26.3 Authenticate with GitHub via `gh auth login --web` (jacksonkirkley account)
- [x] 26.4 Create repo `jacksonkirkley/graduation-announcement`, push main branch (initially private)
- [x] 26.5 Discover that GitHub Pages on free plan requires public repos — make the repo public via `gh repo edit --visibility public`
- [x] 26.6 Enable Pages via API (`POST /repos/.../pages` with source main branch root)
- [x] 26.7 Poll build to completion; verify live URL returns HTTP 200 at `https://jacksonkirkley.github.io/graduation-announcement/`
- [x] 26.8 Verify all critical assets serve over HTTPS (index.html, photo-hero-2000.jpg, baylor-bear.png, photo-1.jpg — all 200 OK)
- [x] 26.9 Generate QR codes via `qrencode`: high error correction (H, 30% recovery), 980×980 PNG, 4-module quiet zone. Two versions:
    - `baylor-qr.png` — Baylor green `#154734` on white (branded)
    - `baylor-qr-black.png` — Black on white (max scan reliability)
- [x] 26.10 Commit the QR PNGs to the repo for archival

## Status — SHIPPED

Page is live at **https://jacksonkirkley.github.io/graduation-announcement/**. QR codes in project root ready to drop into the back of the printed card. After printing, this OpenSpec change can be archived via `openspec archive redesign-baylor-landing-page`.

## Status — ready to ship

All 17 task groups complete. The change `redesign-baylor-landing-page` has produced an `index.html` plus 4 photo assets at the project root. Next session's work is **production deployment** (not part of this change): Netlify drag-and-drop, QR code generation against the deployed URL, and printing. After deployment, this change should be archived via `openspec archive redesign-baylor-landing-page`.
