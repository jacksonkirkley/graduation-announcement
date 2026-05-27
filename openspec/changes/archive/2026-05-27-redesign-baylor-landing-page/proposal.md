# Redesign Baylor Landing Page

## Why

The first version of the landing page (cream + amber, Calistoga + Inter, "warm editorial" style) reads as a generic personal-blog aesthetic — Jackson's feedback was that it "looks super basic" and doesn't lean into the actual milestone: he's going to Baylor. A QR-linked announcement page tied to a school transition should feel celebratory and visibly on-brand for that school, so the moment someone scans the card they recognize where he's headed.

This redesign also captures all design decisions, content, and constraints in OpenSpec artifacts so the work survives Claude Code restarts and context compaction.

## What Changes

- Replace the v1 color palette (cream `#FFFBEB` background + amber `#D97706` accent) with Baylor's official colors: Baylor Green `#154734` and Baylor Gold `#FFB81C`, with cream/off-white surfaces preserved for warmth and contrast.
- Introduce a "BAYLOR 2026" lockup or equivalent visual identity element so the page reads as belonging to Baylor specifically rather than as a generic personal landing page.
- Strengthen visual hierarchy: larger, more confident hero, decorative dividers/flourishes that complement the navy + cursive aesthetic of the existing physical card front (Downloads/Grad Announcement.png).
- Add a primary hero photo using `JMKClassof2026-71.jpg` (navy suit headshot, golden hour). Optional secondary accent photo from `JMKClassof2026-347.jpg` (guitar + cross necklace) if layout supports it without crowding the QR-scan mobile view.
- Copy required photos from `~/Downloads/Senior Photos/` into the project root so the deployed page is self-contained.
- Re-evaluate typography against the ui-ux-pro-max database for an elegant editorial pairing (e.g., Playfair Display + Inter) that feels appropriate for graduation/Baylor rather than the friendly-casual Calistoga choice from v1.
- Preserve **LOCKED** content from v1: the approved two-paragraph personal note, the Venmo CTA labeled "Help me get started at Baylor" linking to `https://venmo.com/u/jacksonkirkley`, and the school details (Major: Finance / Program: Business Scholars / Move-in: August 24, 2026).
- Preserve **LOCKED** technical constraints: single `index.html` with embedded CSS, vanilla HTML/CSS, no JS framework, no build step, deployable as drag-and-drop to Netlify.

## Capabilities

### New Capabilities
- `announcement-landing-page`: The QR-linked landing page itself — content, copy, layout, navigation behavior, accessibility, and CTA wiring.
- `visual-identity`: Baylor-aligned design system applied to the page — color tokens, typography pairing, decorative elements, photo treatment, and how those tokens express Baylor's brand without infringing on it.

### Modified Capabilities
None. This is the first specification for this project; the existing `index.html` was built without specs and is being superseded.

## Impact

- **Files modified:** `index.html` (full rewrite of CSS and markup; content blocks preserved verbatim).
- **Files added:** `photo.jpg` (renamed copy of `JMKClassof2026-71.jpg`), optionally `photo-2.jpg` for a secondary image.
- **External dependencies:** Google Fonts CDN (font family will change from Calistoga/Inter to whatever the typography query returns; Inter is likely to stay for body).
- **Out of scope for this change:** Netlify deployment, QR code generation, modifications to the existing card front design, analytics/tracking.
