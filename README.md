# Apple UI Design Skill

A skill for creating Apple‑style user interfaces with pixel‑perfect accuracy, defaulting to Light Mode but adaptable to Dark Mode or custom color schemes. Works with any framework (HTML/CSS, React, Vue, SwiftUI, Flutter, etc.) to generate interfaces that feel native to Apple’s ecosystem – embodying clarity, deference, and depth.

## Purpose

This skill provides a set of strict guidelines and design rules to ensure that any generated UI mimics Apple’s elite aesthetics. It is intended for AI assistants or design tools that need to produce production‑ready code with a consistent Apple look and feel.

## Key Features

- **Flexible Color Scheme** – Defaults to Light Mode (crisp, warm‑gray palette) but can adapt to Dark Mode or any custom palette on request.
- **8pt Grid System** – All major dimensions are multiples of 8px.
- **Apple System Fonts** – Uses `SF Pro Display`, `SF Pro Text`, or `-apple-system`; no generic fallbacks like Inter or Roboto.
- **Glassmorphism** – `backdrop-filter` blur on all elevated surfaces (navbar, cards, sheets, modals).
- **Subtle Borders & Shadows** – Translucent borders, ultra‑subtle shadows.
- **Natural Motion** – Custom cubic‑bezier curves mimic iOS feel; staggered reveals trigger on page load for above‑the‑fold content.
- **Accessibility** – Visible focus states, ARIA labels, keyboard navigation support, WCAG AA contrast.
- **Framework‑agnostic** – Rules are described in plain language; translate to the syntax of your chosen framework (CSS, SwiftUI, Flutter, etc.).

## How to Use

1. **Include the skill** in your AI assistant’s skill library (or copy the provided markdown file).
2. **Request a UI** – describe the interface you need, optionally specifying color preferences (e.g., “Build a dashboard in Dark Mode”).
3. **The AI will generate code** that strictly follows the Apple UI Design System rules, adjusting colors as requested.

The skill is written as a markdown file with clear sections: design principles, spacing, typography, depth, motion, components, performance, accessibility, and a verification checklist. For full details, refer to the skill file.

## Example Output

An example implementation of this skill can be found in the `example/` directory. It demonstrates a complete esports team landing page built with HTML/CSS, fully compliant with the skill’s rules.

## Verification

Every output generated with this skill should include the following comment at the top of the code:
