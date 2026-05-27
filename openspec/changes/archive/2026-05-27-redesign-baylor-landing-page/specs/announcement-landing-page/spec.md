# announcement-landing-page

The QR-linked single-page landing site that opens when someone scans the QR code on the back of Jackson Kirkley's graduation announcement. Covers content, copy, layout, interactive behavior, and accessibility for the page itself.

## ADDED Requirements

### Requirement: Hero photo display
The page SHALL display a single primary portrait photo of Jackson at the top of the viewport, presented in a fixed 3:4 (portrait) aspect-ratio container with a 12px corner radius and a 1px Baylor green border.

#### Scenario: Photo file is present
- **WHEN** `photo.jpg` exists at the project root and the page loads
- **THEN** the photo renders inside the framed container with `object-fit: cover` and descriptive alt text of "Jackson Kirkley, Class of 2026"

#### Scenario: Photo file is missing
- **WHEN** `photo.jpg` is absent or fails to load
- **THEN** the photo container is hidden via the image element's `onerror` handler, and the rest of the page layout reflows without empty space

### Requirement: Identity and destination heading
The page SHALL display Jackson's name as the primary heading and Baylor University as the destination immediately below, in a way that a viewer scanning the first viewport on a phone instantly understands who the announcement is from and where he is going.

#### Scenario: First viewport on mobile (390px wide)
- **WHEN** the page loads on a 390px-wide viewport
- **THEN** the photo, "Class of 2026" eyebrow, "Jackson Kirkley" heading, and "Baylor University" wordmark are all visible without scrolling

### Requirement: School details card
The page SHALL display a structured details card containing exactly three labeled rows: Major (Finance), Program (Business Scholars), and Move-in (August 24, 2026).

#### Scenario: Details card rendering
- **WHEN** the page loads
- **THEN** the card shows the three rows in order, each with a small uppercase label on the left and a bold value on the right, separated by hairline rules

### Requirement: Personal note content (LOCKED)
The page SHALL render the approved personal note verbatim in two paragraphs, without modification.

#### Scenario: Note content matches approved text
- **WHEN** the page loads
- **THEN** the page contains the exact text: paragraph 1 starting "This August I'll be heading to Baylor to study Finance through the Business Scholars Program. It's a goal I've been working toward for years, and I genuinely couldn't have reached it without God's hand on every step and the people He's surrounded me with." and paragraph 2 starting "Thank you for believing in me, praying for me, and being part of this chapter. I can't wait to see what God does with what comes next."

### Requirement: Venmo CTA
The page SHALL present a single primary call-to-action button labeled "Help me get started at Baylor" that links to Jackson's Venmo profile.

#### Scenario: CTA tap on mobile
- **WHEN** a user taps the CTA on a phone with the Venmo app installed
- **THEN** the link `https://venmo.com/u/jacksonkirkley` opens, which the Venmo app intercepts and presents Jackson's profile

#### Scenario: CTA tap on desktop or device without Venmo app
- **WHEN** a user clicks the CTA on a device without the Venmo app
- **THEN** the link opens Jackson's Venmo profile in a new browser tab with `rel="noopener noreferrer"`

### Requirement: Footer attribution
The page SHALL include a small footer line below the CTA showing "@jacksonkirkley on Venmo" so the recipient can confirm the destination handle before sending.

#### Scenario: Footer visible after CTA
- **WHEN** the page is rendered
- **THEN** the footer text appears below the CTA, in muted grey, in body font

### Requirement: Mobile-first responsive behavior
The page SHALL render correctly without horizontal scroll on viewports from 320px to 1920px wide.

#### Scenario: Narrow phone (375px)
- **WHEN** the page is loaded at 375px viewport width
- **THEN** all content fits without horizontal scroll, the CTA button is full-width, and typography scales via `clamp()` to remain readable

#### Scenario: Desktop (1440px)
- **WHEN** the page is loaded at 1440px viewport width
- **THEN** the content remains centered with a 600px maximum width, and additional top padding gives breathing room

### Requirement: Reduced motion preference
The page SHALL respect `prefers-reduced-motion: reduce` by collapsing all transition and animation durations to a near-zero value.

#### Scenario: User has reduced motion enabled
- **WHEN** the user's OS setting prefers reduced motion
- **THEN** all CSS `transition-duration` and `animation-duration` values collapse to `0.01ms` so motion is effectively disabled

### Requirement: Keyboard focus visibility
All interactive elements (the Venmo CTA) SHALL have a visible focus indicator when focused via keyboard navigation.

#### Scenario: Tab key reaches the CTA
- **WHEN** the user tabs to the CTA
- **THEN** a 3px solid Baylor green ring with 3px offset appears around the button
