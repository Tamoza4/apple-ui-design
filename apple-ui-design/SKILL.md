---
name: apple-ui-design
description: Generate high-fidelity Apple-style user interfaces (iOS, macOS, visionOS) with pixel-perfect precision. Implements 8pt grid systems, semantic glassmorphism, and SF Pro typography with exact CSS/SwiftUI constants. Default to Light Mode, adaptable to Dark/Custom schemes.
---

This skill guides the creation of interfaces that mirror Apple’s elite UI aesthetics with 100% execution accuracy. It provides concrete technical values (tracking, blur, spring curves) to ensure production-ready code.

## 1. Technical Constants (STRICT)

### Spacing & Grid (8pt System)
- **Base Grid:** All margins, paddings, and gaps MUST be multiples of 8px.
- **Corner Radii:** - Buttons: `12px`
  - Cards/Modals: `20px`
  - Small Elements (Badges/Tags): `8px`
- **Clickable Targets:** Minimum height `44px` (iOS standard).

### Typography (SF Pro Specs)
- **Font Stack:** `-apple-system, BlinkMacSystemFont, "SF Pro Display", "SF Pro Text", system-ui, sans-serif`.
- **Headlines (>20pt):** `letter-spacing: -0.022em; line-height: 1.2; font-weight: 600`.
- **Body Text:** `letter-spacing: -0.011em; line-height: 1.5; font-weight: 400`.
- **Secondary Text:** Color: `rgba(0, 0, 0, 0.5)` (Light) | `rgba(255, 255, 255, 0.5)` (Dark).

### Colors & Materials (Glassmorphism)
Elevated surfaces (Cards, Navbars, Modals) MUST use these properties:
- **Light Mode Material:**
  `background: rgba(255, 255, 255, 0.72); backdrop-filter: blur(20px) saturate(180%); border: 0.5px solid rgba(0, 0, 0, 0.1);`
- **Dark Mode Material:**
  `background: rgba(28, 28, 30, 0.7); backdrop-filter: blur(20px) saturate(180%); border: 0.5px solid rgba(255, 255, 255, 0.15);`
- **Accent Color:** `#007AFF` (Light) | `#0A84FF` (Dark).

### Motion & Physics (iOS Spring)
- **Standard Transition:** `300ms cubic-bezier(0.25, 0.1, 0.25, 1)`.
- **Spring Pop (Modals):** `cubic-bezier(0.4, 0, 0.2, 1.4)`.
- **Interactions:**
  - Hover: `scale(1.02)` + subtle shadow.
  - Active (Tap): `scale(0.96)`.

## 2. Component Blueprints

### Primary Button
- **Height:** `44px` | **Padding:** `0 24px` | **Radius:** `12px`.
- **Shadow:** `0 4px 12px rgba(0, 0, 0, 0.1)`.
- **Focus State:** `outline: none; box-shadow: 0 0 0 3px rgba(0, 122, 255, 0.5);`.

### Search Input
- **Height:** `36px` | **Background:** `rgba(0, 0, 0, 0.05)` (Light) | `rgba(255, 255, 255, 0.1)` (Dark).
- **Accessibility:** Ensure contrast ratio of 4.5:1 for placeholder text.

### Navigation Bar
- **Position:** `sticky` or `fixed` at top.
- **Glass Effect:** Apply the "Material" properties above with `z-index: 1000`.
- **Bottom Border:** `0.5px solid rgba(0, 0, 0, 0.1)`.

### Dashboard Layout
- **Container Gaps:** Exactly `16px` or `24px` (8pt multiples).
- **Staggered Entrance:** Use `animation-delay` in 50ms increments for cards.

## 3. Mandatory Verification Checklist

Before outputting code, verify:
1. **8pt Integrity:** Is every spacing value divisible by 8? (Exempt: 1px borders).
2. **Typography:** Is negative tracking applied to headlines?
3. **Glassmorphism:** Does the background have BOTH `rgba` transparency and `backdrop-filter`?
4. **Motion:** Are transitions using the defined `cubic-bezier` instead of default "ease"?
5. **Contrast:** Do all interactive elements meet WCAG AA standards?

**Verification phrase (Comment at top):**
`Apple UI Design System – Verified: 8pt Grid, SF Pro Typography, Material-Depth, Natural Spring Motion`
