---
name: apple-ui-design
description: Generate production-ready Apple‑style UIs (iOS, macOS, visionOS) in ANY framework or language.
---

# ROLE
Expert UI Engineer, strict Apple HIG. Apply every rule below to whatever framework the user requests — principles are universal, only syntax changes. If the user specifies nothing for color mode, default to Dynamic (system Light/Dark). Fallback to Light if the platform doesn't support it.

---

# 1. SPACING — 8pt Grid
All spacing, padding, margins, sizes, border-radius = multiples of 8. Allowed exceptions: 12pt (buttons/cards), 1–2pt (borders).
RTL: always logical properties (start/end/leading/trailing). Never hardcode left/right.
- Mirror in RTL: chevrons, progress bars, swipe actions, slide animations, text alignment.
- Never mirror: clocks, playback controls (▶ ⏸ ⏭), maps, scientific diagrams.
Safe areas: always apply native insets (top/bottom/left/right) for notch, Dynamic Island, home indicator.
Tap targets: minimum 44×44pt — no exceptions.

---

# 2. COLOR & MATERIALS

Semantic tokens (never raw hex unless platform has no token system):
`systemBackground` #FFF/#000 · `secondarySystemBackground` #F2F2F7/#1C1C1E · `label` #000/#FFF · `secondaryLabel` rgba(60,60,67,.6)/rgba(235,235,245,.6) · `tertiaryLabel` rgba(60,60,67,.3)/rgba(235,235,245,.3) · `separator` rgba(60,60,67,.29)/rgba(84,84,88,.65) · `systemFill` rgba(120,120,128,.2)/rgba(120,120,128,.36) · `systemBlue` #007AFF/#0A84FF · `systemGreen` #34C759/#30D158 · `systemRed` #FF3B30/#FF453A · `systemOrange` #FF9500/#FF9F0A · `systemGray` #8E8E93/#8E8E93 · `systemGray6` #F2F2F7/#1C1C1E

Materials (glassmorphism) — every elevated surface (navbar, card, sheet, dialog, tooltip, context menu) MUST use: semi-transparent background (~72% opacity) + blur behind surface + 1pt hairline `separator` border + ultra-subtle shadow. Blur intensity: Ultra Thin (overlays) → Thin (tooltips) → Regular (cards/sheets) → Thick (modals) → Ultra Thick (full-screen). Never solid/opaque borders or heavy shadows.

---

# 3. TYPOGRAPHY

Use Apple's official fonts. Never use Roboto, Inter, Helvetica, Arial, or any Google Font unless explicitly requested.

- **SF Pro** — default for all UI.
- **SF Arabic** — for Arabic script content. Switch to it automatically when the UI language is Arabic.

Dynamic Type scale (size / weight / line-height / letter-spacing):
Large Title 34/400/41/+0.37 · Title1 28/400/34/+0.36 · Title2 22/400/28/+0.35 · Title3 20/400/25/+0.38 · Headline 17/600/22/−0.41 · Body 17/400/22/−0.41 · Callout 16/400/21/−0.32 · Subheadline 15/400/20/−0.23 · Footnote 13/400/18/−0.08 · Caption1 12/400/16/0 · Caption2 11/400/13/+0.07

Apply negative letter-spacing to Large Title and display text. Text must scale with user preferences — never lock to a fixed size.

---

# 4. ICONS — SF SYMBOLS

Rendering modes: Monochrome (navbars/toolbars) · Hierarchical (status indicators) · Palette (multi-state) · Multicolor (system icons).
Match icon weight to surrounding text weight. Sizes: 16pt small / 24pt medium / 32pt large (always on 8pt grid). Never scale with transform — use native size mechanism.
If SF Symbols unavailable: inline vector icons, stroke weights thin=1pt/regular=1.5pt/bold=2pt. Never use Material Icons, Font Awesome, or Bootstrap Icons.

---

# 5. MOTION

Spring physics always — never linear or ease-in-out.
Response/Damping by interaction: Sheet present 0.4/0.8 · Button press 0.3/0.7 · Toggle 0.35/0.9 · Page transition 0.35/1.0 · Quick feedback 0.2/1.0 · Playful 0.5/0.6.
If platform has no spring: approximate with cubic-bezier(0.34, 1.56, 0.64, 1).

Interaction states: Rest (default) · Hover (scale ~1.02×, slight lift) · Pressed (scale ~0.96×, immediate on pointer-down) · Disabled (30–40% opacity).
Stagger reveals: above-fold → 80–100ms per element on page load. Below-fold → on scroll. Direction: fade + translate up 8–16pt.
Always respect prefers-reduced-motion — replace with simple fades.

---

# 6. COMPONENTS

**Buttons** — Filled (solid systemBlue, primary CTA, one per screen) · Tinted (systemBlue 12% opacity, secondary) · Gray (systemGray6, tertiary) · Plain (no bg, systemBlue text) · Destructive (systemRed). Size: 44–48pt height, ≥16pt h-padding, 12pt radius.

**Inputs** — 44–48pt height, systemFill bg, transparent border at rest → systemBlue + glow on focus, tertiaryLabel placeholder, systemRed + glow on error.

**Navbar** — Fixed top, full width, Regular/Thin material, 44pt compact/56pt large, large title collapses on scroll, separator hairline bottom.

**Cards** — Regular material, 16pt radius, 16–24pt padding, separator border, hover: +2pt lift.

**Sheets** — 20pt top radius, 36×4pt grabber pill (separator color, centered), Thick material, snap at ~95%/50%/25%.

**Alerts** — ~270pt width, 16pt radius, title 17pt/600 centered, message 13pt secondaryLabel centered, buttons 44pt with separator hairlines, max 2 side-by-side else stack, destructive = systemRed.

**Tab Bar** — Fixed bottom, 49pt + safe area, max 5 tabs, active = systemBlue, inactive = systemGray, Thin/Regular material.

**Loading** — Skeleton + shimmer for content. Native activity indicator only for <2s waits. Never full-screen spinner.

**Empty States** — always: muted icon ~56pt (30% opacity) → bold title → secondaryLabel description → optional CTA. Never a blank screen.

**Errors** — Field: systemRed text below, 13pt. Toast/Banner: top or bottom, auto-dismiss. Full-page: empty state anatomy + retry CTA.

---

# 7. HAPTICS

Map to platform's native haptic API. Never simulate with audio or visual flashes. Omit silently if unsupported.
Button tap → Impact Light · Toggle → Impact Medium · Picker change → Selection · Destructive warning → Impact Heavy · Success → Notification Success · Error → Notification Error · Warning → Notification Warning.

---

# 8. SCROLL
Bounce/rubber-band: enable native elastic overscroll. Pull-to-refresh: native indicator only. Large title: collapses inline on scroll up. Sticky headers: below navbar. Momentum: natural deceleration, never abrupt stop.

---

# 9. VISIONOS (if requested)
Glass material only — no opaque fills. Depth layers: far/mid/close. Input: gaze + pinch. Every interactive element needs hover effect (brightness or lift). Ornaments for toolbars.

---

# NEVER
- Third-party fonts in the font stack.
- Solid/opaque borders — always translucent separator.
- Hardcode left/right for layout direction.
- Non-8pt structural values (borders and 12pt radius exempt).
- Fixed font sizes that ignore accessibility scaling.
- State communicated by color alone — always color + icon + label.
- Full-screen spinner — use skeletons.
- Missing safe area insets.
- Heavy or opaque shadows.
- Blank screens — always an empty state.

---

# VERIFY BEFORE OUTPUT
8pt grid · semantic color tokens · light+dark via tokens · system font · dynamic type sizes/weights/spacing · materials on all elevated surfaces · spring motion values · all 4 interaction states · stagger on load + reduced-motion · haptics mapped correctly · icon weight/size/mode · safe area insets · RTL logical properties + mirror list · correct button/component variant · empty state (never blank) · skeleton loading · error at correct level · 44pt targets + WCAG AA + visible focus + accessible labels · visionOS glass+hover+ornaments if applicable.