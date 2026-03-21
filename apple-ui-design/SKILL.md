---
name: apple-ui-design
description: Generate Apple‑style user interfaces with high precision, defaulting to Light Mode but adaptable to Dark Mode or custom color schemes. Use this skill when the user requests interfaces that mimic Apple’s design language (iOS, macOS, visionOS) – websites, components, dashboards, or applications. Delivers production‑ready code that embodies clarity, deference, and depth, regardless of framework (HTML/CSS, React, Vue, SwiftUI, Flutter, etc.).
license: Complete terms in LICENSE.txt
---

This skill guides creation of interfaces that mirror Apple’s elite UI aesthetics with pixel‑perfect accuracy. It defaults to **Light Mode** (crisp, warm‑gray palette) but can adapt to **Dark Mode** or any custom color scheme if explicitly requested by the user. Every output must feel native to Apple’s ecosystem, be fully functional, and follow the rules below.

## Design Principles

Apple’s design language rests on three pillars:

- **Clarity** – Every element communicates its purpose instantly. Text is legible, icons are unambiguous, layouts breathe.
- **Deference** – The UI steps back, letting content shine. Motion and translucency serve context, not decoration.
- **Depth** – Layers, shadows, and blur create a sense of hierarchy and physicality without heaviness.

**CRITICAL**: The default palette is Light Mode. If the user requests Dark Mode or custom colors, implement that consistently while preserving the other guidelines (glassmorphism, grid, motion, etc.).

## Apple UI Guidelines

Apply these guidelines using whatever implementation language the user requests (HTML/CSS, React, Vue, SwiftUI, Flutter, etc.). The rules are about *what* to achieve, not *how* to code it in one syntax. Translate technical values (like bezier curves or blur filters) to the equivalent syntax in the requested framework.

### Spacing – 8pt System
All major layout dimensions (padding, margin, gaps, element sizes, icon dimensions, border radii) **must be multiples of 8px**:
- Acceptable: 8px, 16px, 24px, 32px, 40px, 48px, 56px, 64px, etc.
- Border widths may be 1px or 2px (exempt).
- Fine visual details like `2px`, `4px`, or `6px` are allowed **only** for micro‑adjustments (e.g., outline offsets, letter‑spacing, small decorative gaps) that do not disrupt the overall grid alignment. Use them sparingly and with intent.

### Colors (Default Light Mode)
- Backgrounds: nearly white with a slight warmth (e.g., `#fbfbfd`).
- Surfaces: semi‑transparent layers with backdrop blur (glassmorphism).
- Borders: translucent, never solid black.
- Accent: clean blues (`#007aff`) and subtle highlights.
- Text: high‑contrast grays, never pure black.

If the user requests **Dark Mode** or a custom palette:
- Invert the lightness appropriately while maintaining high contrast and translucency.
- Keep the glassmorphism effect (`backdrop-filter` with semi‑transparent layers).
- Ensure borders remain subtle (translucent on dark backgrounds).
- Accent colors can be adjusted (e.g., `#0a84ff` for dark mode), but keep them vibrant and legible.

### Typography
- **Primary fonts**: Use Apple’s system fonts (`SF Pro Display`, `SF Pro Text`, or `-apple-system`). For native frameworks (SwiftUI), use `.system(...)`. For cross‑platform (Flutter), use `CupertinoIcons` and appropriate font families.
- **Fallback fonts**: Acceptable fallbacks are system fonts like `BlinkMacSystemFont`, `Segoe UI`, or `sans-serif`. **Do not** use imported generic fonts such as Inter, Roboto, Arial, Helvetica, or any Google Fonts unless explicitly requested by the user.
- Headlines: Apply negative letter‑spacing for large titles (e.g., `-0.02em`) to achieve the signature extended look.

### Depth & Material
Implement glassmorphism (frosted glass) using backdrop blur on **every elevated surface**:
- Navbar (fixed)
- Cards
- Sheets / modals
- Any floating container that visually separates from the background (e.g., hero stats, badge overlays)

Use `backdrop-filter: blur(24px) saturate(180%)` or the framework’s native equivalent (e.g., `.background(.ultraThinMaterial)` in SwiftUI, `BackdropFilter` in Flutter). Shadows should be ultra‑subtle – only hint at elevation, never heavy.

### Motion & Interactions
- **Timings**: Fast transitions (200–300ms) with custom easing curves that mimic iOS. Use CSS cubic‑bezier for web, or native animation curves (like `spring()` or `.timingCurve`) for mobile frameworks.
- **Hover (desktop/web only)**: Slight lift and gentle scale.
- **Active (press)**: Subtle scale‑down to give physical feedback.
- **Staggered reveals**:  
  - Elements **above the fold** (hero section, main title, primary CTA) should have staggered animations that trigger **immediately on page load**, using `animation-delay`.  
  - Content further down (cards, roster, etc.) may use scroll‑triggered reveals, but should still include staggered delays (via `transition-delay` or `animation-delay`) to create a flowing entrance.

### Components
Design common elements with these characteristics:
- Buttons: Fixed height (40–48px), rounded corners (12px), translucent background, subtle border, clear hover/active states.
- Inputs: Same height and border styling, with a clean focus indicator.
- Navbar: Fixed to top, glass effect that blurs underlying content.

### Performance & Accessibility
- Performance: Prefer animations that use `transform` and `opacity`; limit `backdrop-filter` to small, essential areas.
- Accessibility: Provide visible focus states (e.g., blue ring), ensure color contrast (WCAG AA), support keyboard navigation and screen readers.

## What to Avoid
- Using third‑party fonts like Inter, Roboto, Helvetica, or Arial in the font stack unless explicitly requested.
- Solid black borders (`#000000`). Borders must be translucent or light gray (or appropriate for the chosen color scheme).
- Heavy shadows; keep them subtle and low‑contrast.
- Over‑use of `backdrop-filter` on large areas; balance visual quality with performance.

## Strict Rules & Verification

Before finalizing any output, you must verify:

1. **8pt Grid** – All major dimensions are multiples of 8px. Only minor fine‑tuning values (2px, 4px, etc.) are allowed if they don't break the grid.
2. **Color Scheme** – If the user did not specify a scheme, use Light Mode as described. If Dark Mode or custom colors were requested, ensure they are applied consistently and maintain the same translucency/glassmorphism principles.
3. **Typography** – Uses Apple’s system fonts as the primary; no generic fallbacks (Inter, Roboto, etc.) appear in the font stack unless requested.
4. **Glassmorphism** – All elevated surfaces (navbar, cards, sheets, modals) use backdrop blur and translucent backgrounds.
5. **Motion** – Transitions use custom easing (not linear or default ease‑in‑out); staggered reveals are present and trigger appropriately (above‑the‑fold on load, others on scroll).
6. **Borders** – All borders are translucent or light gray (or appropriate for the color scheme); no solid black borders.
7. **Accessibility** – Focus states are visible and interactive elements are keyboard‑accessible.
8. **Staggered Reveals** – Hero section and above‑the‑fold content use staggered animations that trigger immediately on page load, not solely on scroll.

**Verification phrase** (include as a comment appropriate for the language at the top of the code):  
`Apple UI Design System – Verified: 8pt, glassmorphism, SF fonts, natural motion`

Implement the interface with these rules. Be bold yet restrained – let the content shine, and let Apple’s design language speak through precision and subtlety.