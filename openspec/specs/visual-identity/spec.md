# visual-identity Specification

## Purpose
TBD - created by archiving change redesign-baylor-landing-page. Update Purpose after archive.
## Requirements
### Requirement: Baylor color palette tokens
The page SHALL define and use a CSS custom-property color palette anchored on Baylor's official colors: Baylor Green `#154734` and Baylor Gold `#FFB81C`, with cream and white surfaces, deep slate body text, and warm grey muted text.

#### Scenario: Color tokens declared on `:root`
- **WHEN** the page loads
- **THEN** the stylesheet declares at minimum `--color-primary: #154734`, `--color-accent: #FFB81C`, `--color-bg: #FAF7F0`, `--color-surface: #FFFFFF`, `--color-fg: #0F172A`, `--color-muted: #6B6B6B`, and `--color-border: #E8E2D5`

#### Scenario: Brand colors used as accents, not dominant fields
- **WHEN** the page is viewed at any viewport
- **THEN** cream/white surfaces dominate the reading area, and Baylor green/gold appear in the wordmark, accent stripes, dividers, photo border, and CTA — never as a long-form text background

### Requirement: Typography pairing
The page SHALL load Playfair Display (display heading), Inter (body and UI), and Pinyon Script (single decorative accent only) from Google Fonts with `display=swap`.

#### Scenario: Font families applied
- **WHEN** the page is rendered
- **THEN** the "Jackson Kirkley" heading and "BAYLOR UNIVERSITY" wordmark use Playfair Display, all body and UI text uses Inter, and the "Class of 2026" eyebrow accent uses Pinyon Script

#### Scenario: Font fallback during network slowness
- **WHEN** Google Fonts has not yet returned
- **THEN** text renders immediately in system fallback fonts (Georgia for serif, system-ui for sans) without invisible-text periods

### Requirement: BAYLOR wordmark lockup
The page SHALL include a typographic Baylor lockup composed of "BAYLOR UNIVERSITY" set in Playfair Display all-caps with letterspacing, paired with the year and a short gold horizontal rule as a flourish.

#### Scenario: Wordmark visible above the note
- **WHEN** the page loads
- **THEN** "BAYLOR UNIVERSITY" appears as a centered all-caps lockup positioned between the name heading and the school details card, with a thin gold horizontal rule (~48px wide) above or below it

#### Scenario: Wordmark uses no protected imagery
- **WHEN** the page is rendered
- **THEN** the wordmark is purely typographic (no Baylor seal, crest, "BU" mark, or other licensed/trademarked imagery)

### Requirement: Photo treatment
The portrait photo SHALL be presented inside a rounded-rectangle frame with a 12px corner radius, a 1px Baylor green border, and a subtle drop shadow, occupying a fixed 3:4 aspect ratio.

#### Scenario: Photo rendered with frame
- **WHEN** the photo loads successfully
- **THEN** the visible photo container has `border-radius: 12px`, `border: 1px solid var(--color-primary)`, and a `box-shadow` no larger than `0 8px 24px rgba(15,23,42,0.10)`

### Requirement: Top and bottom accent stripes
The page SHALL be visually framed by a thin Baylor gold horizontal stripe at the top and a matching stripe at the bottom of the document.

#### Scenario: Stripes present on every viewport
- **WHEN** the page is rendered at any viewport
- **THEN** a 4px-tall Baylor gold band spans the full width of the viewport at the very top and bottom of the page body

### Requirement: WCAG AA contrast on all text
Every text and background color pairing used on the page SHALL meet or exceed WCAG AA contrast (4.5:1 for body text, 3:1 for large text 18.66px bold or 24px regular and above).

#### Scenario: Body text on cream
- **WHEN** the note paragraphs are rendered on the `#FAF7F0` background
- **THEN** the foreground color `#0F172A` yields a contrast ratio greater than 4.5:1

#### Scenario: CTA text on gold
- **WHEN** the CTA button is rendered with `#FFB81C` background
- **THEN** the button text uses `#154734` (Baylor green) for a measured contrast ratio greater than 4.5:1

#### Scenario: Muted footer text
- **WHEN** the "@jacksonkirkley on Venmo" footer renders in `#6B6B6B` on cream
- **THEN** the contrast ratio is greater than 4.5:1

### Requirement: No emoji icons
All iconography (CTA gift glyph, any decorative marks) SHALL be SVG, not emoji characters.

#### Scenario: CTA icon source
- **WHEN** the CTA renders
- **THEN** the icon adjacent to the button label is an inline SVG element with `aria-hidden="true"`, not a Unicode emoji code point

