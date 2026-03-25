# Design System Standards File — Template & Guide

**A framework for creating a living design system specification that works for both humans and AI agents.**

> Share this template with your team, use it in GPT/Claude/Copilot conversations, or include it in your repo as a coding standard. AI models can read this file and generate pixel-accurate mockups and production code that match your app's look and feel.

---

# Part 1: The Guide (How & Why)

*Read this once to understand the approach. Skip to [Part 2: The Template](#part-2-the-template) when you're ready to fill it in.*

---

## Why This Exists

Most design systems live in Figma or Storybook — tools that AI coding agents can't read. When you paste a Figma link into a chat, the model guesses. When you hand it a structured markdown file with your exact spacing, colours, component patterns, and layout rules, it **reproduces your design language precisely** — in mockups, in code, and across every new screen.

This isn't a Figma replacement. It's a **machine-readable design contract** that sits in your repo, next to your code, versioned with your code, and understood by every developer and every AI agent on your team.

---

## How This File Gets Created (The Process)

**You do NOT generate this file from scratch.** It emerges from real, battle-tested screens. Here's the approach:

### Phase 1: Build & Modernise 3–4 Key Screens

Pick your most important screens (e.g., home feed, detail view, settings, onboarding). Use an AI model (Claude, GPT, Copilot) as a design partner:

1. **Start a design conversation** — describe your app's target audience, brand personality, and the feeling you want (e.g., "modern challenger bank", "friendly lifestyle app", "enterprise dashboard that doesn't feel enterprise").
2. **Iterate on colour schemes** — ask the model to propose palettes, explain the psychology behind choices, and test combinations against accessibility standards (WCAG contrast ratios).
3. **Prompt for modern native patterns** — ask for "iOS-native feel" or "modern web portal" styling. Reference apps you admire (N26, Airbnb, Linear, Notion). The model will suggest spacing, typography, and interaction patterns that match.
4. **Build the screens** — implement them in your framework (Angular, React, SwiftUI, whatever). Use the model to generate the code.
5. **Refine in the browser/device** — test on real devices. Adjust spacing, colours, and typography until they feel right. This is where pixel-level decisions get made.

### Phase 2: Beautify & Test

6. **Test with real users or stakeholders** — does it feel modern? Professional? Trustworthy? Fun? Adjust.
7. **Test dark mode** — if applicable, ensure your palette works in both light and dark contexts.
8. **Test edge cases** — long text, empty states, loading states, error states. These reveal spacing and layout issues.

### Phase 3: Extract the Standards File

9. **Point your best deep-reasoning model at your finished screens** — give it access to your actual CSS/SCSS, your component HTML, and screenshots. Ask it to:
   - Identify every repeated pattern (spacing, colours, typography, component structure)
   - Extract the design tokens (specific values for padding, margin, border-radius, shadows)
   - Document the layout rules (header heights, content width, safe areas)
   - Capture the design philosophy (not just "16px padding" but *why* 16px)
10. **Review and refine the output** — the model will produce a first draft. You curate it: remove noise, add context the model missed, and organise it into the structure below.

### Phase 4: Maintain

11. **Keep it living** — when you add new patterns, update the file. When you deprecate patterns, mark them. This file is as important as your codebase.

---

## What Makes This More Than a Style Guide

A typical style guide says: *"Primary button: purple background, white text, 12px border radius."*

This file goes further:

| Layer | What It Captures | Why It Matters |
|-------|-----------------|----------------|
| **Design Vision** | Target audience, brand personality, reference apps | AI agents understand *intent*, not just values |
| **Colour Psychology** | Why purple, why not blue, what the palette communicates | Prevents random colour choices in new screens |
| **Layout Architecture** | Screen structure, scroll behaviour, safe areas, fixed vs sticky | Agents build structurally correct screens, not just pretty ones |
| **Spacing System** | Base unit, multipliers, decision tree | Consistent rhythm without memorising 50 values |
| **Component Patterns** | Full HTML/code snippets for every reusable element | Copy-paste accuracy for agents and juniors |
| **Platform Specifics** | iOS safe areas, native header heights, responsive breakpoints | Production-ready code, not demo-ware |
| **Anti-Patterns** | What NOT to do, deprecated approaches, common mistakes | Prevents regression and known pitfalls |
| **Checklists** | Screen creation checklist, testing checklist | Nothing gets forgotten |

---

## Should Dark Mode Be Inline or a Separate File?

Dark mode touches every section — colours, components, borders, shadows. You have three options:

| Approach | When to Use | Pros | Cons |
|----------|-------------|------|------|
| **Inline** (add `Dark` column to every table) | Small apps, few components | Everything in one place | File gets very long |
| **Separate file** (`STANDARDS_DARK_MODE.md`) | Large apps, 10+ component patterns | Focused, thorough coverage | Two files to maintain |
| **Hybrid** (quick reference here, full details in separate file) | Most apps | Best of both | Must keep them in sync |

**Recommendation:** Start with inline. Extract to a separate file when you have more than ~5 component-specific dark mode patterns (toggles, toasts, inputs, cards, selection states, sliders, etc.).

**If you create a separate dark mode file**, structure it like this:

```
## Dark Mode Philosophy
## Color Mapping Standards (backgrounds, text, borders)
## Component-Specific Patterns (toggles, forms, toasts, buttons, cards, selection states)
## Dark Mode Checklist
## Common Mistakes (DO / DON'T)
## Contrast Ratios (WCAG AA)
```

See the [Dark Mode Template](#-dark-mode-standards) section below for the fill-in template.

---

## Adapting This Template for Your Platform

This template works for **mobile apps, web portals, and hybrid apps**. Not every section applies to every platform.

| Section | Mobile App | Web Portal | Hybrid |
|---------|-----------|------------|--------|
| Safe Zones | ✅ iOS/Android safe areas | ❌ Skip | ✅ Capacitor/Cordova |
| Header Patterns | ✅ Sticky, 44px native | ✅ Fixed navbar, breadcrumbs | ✅ Both |
| Bottom Navigation | ✅ Tab bar | ❌ Usually sidebar | ✅ Tab bar in app shell |
| Mobile Canvas Width | ✅ 448px or similar | ❌ N/A | ✅ In mobile view |
| Responsive Breakpoints | ❌ N/A | ✅ Critical | ✅ For web fallback |
| Sidebar Layout | ❌ N/A | ✅ Collapsible sidebar | ❌ Skip |
| Touch Targets | ✅ 44px minimum | ⚠️ Recommended | ✅ 44px minimum |

**When filling in the template:** skip sections that don't apply, but keep the heading as a placeholder with "N/A — [reason]" so future team members know it was intentionally omitted, not forgotten.

---

# Part 2: The Template

*Copy everything below into a new file called `STANDARDS_DESIGN_SYSTEM.md`. Each section contains a 🔵 **GUIDANCE** block explaining what to document, followed by a 🟢 **EXAMPLE** block showing a complete Impulsy example. Replace the examples with your own app's values — add, remove, or restructure sections and table rows to match what your app actually needs.*

> [!IMPORTANT]
> **For AI agents:** The 🔵 GUIDANCE and 🟢 EXAMPLE blocks throughout this template are **template instructions**, not actual design system values. When a team uses this template, they replace the EXAMPLE content with their own app's real values. If you see GUIDANCE/EXAMPLE blocks, you are reading the **template**, not a filled-in design system.

---

# [Your App Name] Design System & Style Guide

> [!NOTE]
> Replace `[Your App Name]` with your actual app name.

**Last Updated:** [YYYY-MM-DD]
**Purpose:** Centralised design system with reusable components, utilities, and patterns
**Implementation:** [Path to your global stylesheet, e.g., `src/styles.scss`, `src/app/globals.css`, `theme.css`]

---

## 🎯 Design Vision

> [!NOTE]
> **🔵 GUIDANCE:** This is the "soul" of your app. AI agents use this section to make subjective decisions (colour choice, spacing feel, animation style) when building new screens. Without this, the model has patterns but no personality.
>
> Write freely about your app. Cover these areas (but use whatever format works):
> - What kind of app is it and who uses it?
> - What adjectives describe the brand?
> - What other apps inspire your aesthetic?
> - What design principles guide decisions?
> - What should the overall experience feel like?

> [!TIP]
> **🟢 EXAMPLE (Impulsy — mobile event discovery app):**
>
> **App Type:** Hybrid mobile app (Angular + Capacitor)
> **Target Audience:** Vienna locals, 25–45, discovering events
> **Brand Personality:** Modern, trustworthy, minimal, playful
> **Design References:** N26 for banking clarity, Airbnb for content discovery
> **Overall Feel:** A clean, native-feeling mobile experience that feels premium without being cold
>
> **Design Principles:**
> - Mobile-first, app-native experience
> - Minimal but meaningful animations
> - Tactile, responsive interactions
> - Content over chrome — UI gets out of the way
> - Consistent spacing and typography hierarchy
>
> *End of example — replace above with your own design vision.*

---

## 🎨 Colour Palette

> [!NOTE]
> **🔵 GUIDANCE:** Document every colour your app uses, grouped by purpose. Include hex values AND usage context — agents use the usage descriptions to pick the right colour for new elements.
>
> You might have 2 brand colours or 8. You might use Tailwind defaults for neutrals or custom CSS variables. There's no fixed number of rows — add what your app actually uses.
>
> Organise into these groups (add/remove groups as needed):
> - **Brand / primary colours** — your signature colours with specific usage
> - **Neutral colours** — text, backgrounds, borders
> - **Semantic colours** — error red, success green, info blue, warning yellow
> - **Dark mode quick reference** — light/dark pairs (or link to separate file)
>
> For each colour, explain WHERE it's used and WHY — not just the hex value.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — mobile event discovery app):**
>
> ### Brand / Primary Colours
>
> | Name / Variable | Hex | Usage |
> |----------------|-----|-------|
> | `purple` | #8B5CF6 | **Primary buttons, CTAs, selected states, checkmarks, active tabs** |
> | `purple-light` | #C4B5FD | Backgrounds, unselected pills, hover states |
> | `coral` | #FF6B6B | Accent (notifications, highlights) — use sparingly |
>
> ### Neutral Colours
>
> | Name / Variable | Hex | Usage |
> |----------------|-----|-------|
> | `gray-900` | Tailwind default | Primary text, headings |
> | `gray-600` | Tailwind default | Secondary text |
> | `gray-400` | Tailwind default | Separator text, placeholders |
> | `gray-200` | Tailwind default | Borders, dividers |
> | `gray-50` | Tailwind default | Page backgrounds |
>
> ### Semantic Colours
>
> | Colour | Usage |
> |--------|-------|
> | `red-500` | Errors, destructive actions |
> | `green-500` | Success states |
> | `blue-500` | Info states |
>
> ### Dark Mode Quick Reference
>
> | Element | Light | Dark |
> |---------|-------|------|
> | Page background | `bg-white` | `bg-black` (#000000 OLED) |
> | Card background | `bg-white` | `bg-gray-800` (#1F2937) |
> | Primary text | `text-gray-900` | `text-white` |
> | Secondary text | `text-gray-600` | `text-gray-300` |
> | Borders | `border-gray-200` | `border-gray-700` |
>
> *End of example — replace above with your own colour palette.*

---

## 🌙 Dark Mode Standards

> [!NOTE]
> **🔵 GUIDANCE:** If your app supports dark mode, document it here OR in a separate `STANDARDS_DARK_MODE.md` file.
>
> Dark mode touches everything — backgrounds, text, borders, component states, shadows. Cover these areas:
>
> 1. **Colour mappings** — how every background, text, and border colour changes
> 2. **Component patterns** — how each interactive component adapts (toggles, inputs, buttons, toasts, cards, selection states, sliders)
> 3. **Visual hierarchy** — explain the dark mode layering philosophy (e.g., "pure black base → gray-800 cards → gray-700 interactive elements")
> 4. **Checklist** — what to verify when building any new component
> 5. **Common mistakes** — what NOT to do (the things you've learned the hard way)
>
> For large apps with 5+ component-specific patterns, a separate file is recommended:
> **For complete dark mode standards:** See [STANDARDS_DARK_MODE.md](STANDARDS_DARK_MODE.md)
>
> For smaller apps, write it all inline below.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — separate file approach):**
>
> Impulsy uses a separate `STANDARDS_DARK_MODE.md` with these sections:
>
> ### Dark Mode Philosophy
> Pure black (#000000) base for OLED battery savings. Elevated surfaces use subtle grays for hierarchy. Purple brand colour works perfectly in both modes.
>
> ### Background Colours
>
> | Element | Light Mode | Dark Mode | Class Pattern |
> |---------|------------|-----------|---------------|
> | Page background | `bg-white` | `bg-black` | `bg-white dark:bg-black` |
> | Cards/Containers | `bg-white` | `bg-gray-800` | `bg-white dark:bg-gray-800` |
> | Headers | `bg-white` | `bg-gray-900` | `bg-white dark:bg-gray-900` |
> | Elevated surfaces | `bg-gray-50` | `bg-gray-700` | `bg-gray-50 dark:bg-gray-700` |
> | Disabled inputs | `bg-gray-50` | `bg-gray-700` | `bg-gray-50 dark:bg-gray-700` |
>
> ### Component Patterns
> **Toggles:** OFF: `bg-gray-200` → `dark:bg-gray-700`. ON: `bg-purple` (no change — works in both).
> **Buttons:** Primary: `bg-purple text-white` (no change needed!). Secondary: `bg-white` → `dark:bg-gray-700`.
> **Toasts:** Info: `bg-blue-50 border-blue-400` → `dark:bg-blue-900/20 dark:border-blue-500 dark:text-blue-200`.
> **Pill buttons inside containers:** `dark:bg-gray-700` (lighter than gray-800 container for visible separation).
>
> ### Common Mistakes
> ❌ DON'T: Use `gray-100` backgrounds in dark mode (too bright). Use `gray-800` for buttons inside gray-800 containers (invisible).
> ✅ DO: Use semi-transparent backgrounds for toasts (`blue-900/20`). Keep purple as-is for CTAs.
>
> *End of example — replace above with your own dark mode standards.*

---

## 📐 Typography System

> [!NOTE]
> **🔵 GUIDANCE:** Define your type scale with semantic class names or tokens. Include the class name agents should use in generated code — not raw CSS values.
>
> Cover these groups (add more if your app needs them):
> - **Headings** — page titles, section headings, card titles (typically 3–5 levels)
> - **Body text** — primary, secondary, metadata sizes
> - **Labels & helpers** — form labels, helper/hint text, section divider labels
>
> For each, specify: class/token name, usage context, size, weight, and colour.
> You might have 3 heading levels or 6. You might define labels separately or not. Document what your app actually uses.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> ### Headings
>
> | Class | Usage | Style |
> |-------|-------|-------|
> | `.heading-1` | Page titles, main headings | 2xl, bold, gray-900 |
> | `.heading-2` | Section headings | xl, semibold, gray-900 |
> | `.heading-3` | Card titles, subsections | lg, semibold, gray-900 |
>
> ### Body Text
>
> | Class | Usage | Style |
> |-------|-------|-------|
> | `.body-text` | Standard body text | base (16px), gray-900 |
> | `.body-text-sm` | Secondary content | sm (14px), gray-600 |
> | `.body-text-xs` | Metadata, timestamps | xs (12px), gray-500 |
>
> ### Labels & Helpers
>
> | Class | Usage | Style |
> |-------|-------|-------|
> | `.label-text` | Form labels, input labels | sm, medium, gray-700 |
> | `.helper-text` | Helper text under inputs | sm, gray-600 |
> | `.separator-text` | Section divider labels | xs, gray-400, uppercase, tracking-wide |
>
> *End of example — replace above with your own typography system.*

---

## 📏 Spacing Standards

> [!NOTE]
> This is the highest-value section. Inconsistent spacing is the #1 sign of AI-generated UI. Define a base unit and multiplier system so every spacing decision is derived, not guessed.

### Base Unit

> [!NOTE]
> **🔵 GUIDANCE:** Pick a base unit (commonly 4px, 8px, or 16px) and define multipliers. This prevents arbitrary spacing values and ensures visual rhythm. You may have 4 multipliers or 8 — define what your app actually uses.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — 16px base):**
>
> **Base:** 16px (Tailwind `4` unit)
>
> | Multiplier | Value | Token / Class | Usage |
> |-----------|-------|---------------|-------|
> | 0.5x | 8px | `space-2` / `gap-2` | Compact inline spacing (pills, badges) |
> | 0.75x | 12px | `space-3` / `gap-3` | Related items (info card grids) |
> | **1x** | **16px** | **`space-4` / `gap-4`** | **Default (cards, below headings)** |
> | 1.5x | 24px | `space-6` / `gap-6` | Medium separation (section breaks) |
> | 2x | 32px | `space-8` / `gap-8` | Major sections (menu groups) |
> | 6x | 96px | `pb-24` | Bottom padding (accounts for bottom nav) |
>
> *End of example — replace above with your own base unit system.*

### Heading Spacing

> [!NOTE]
> **🔵 GUIDANCE:** Define consistent rules for spacing above and below headings. Strongly recommended: ONE rule below ALL headings (same value, no exceptions). Top margins can vary by heading level to create hierarchy.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> | Heading Level | Above (Top Margin) | Below (Bottom Margin) |
> |--------------|--------------------|-----------------------|
> | `.heading-1` | `mt-8` (32px) 2x base | `mb-4` (16px) 1x base |
> | `.heading-2` | `mt-6` (24px) 1.5x base | `mb-4` (16px) 1x base |
> | `.heading-3` | `mt-4` (16px) 1x base | `mb-4` (16px) 1x base |
> | `.separator-text` | `mt-8` (32px) 2x base | `mb-4` (16px) 1x base |
>
> **Rule:** ONE spacing below ALL headings = `mb-4` (16px). Always. No exceptions.
>
> *End of example — replace above with your own heading spacing.*

### Content Block Spacing

> [!NOTE]
> **🔵 GUIDANCE:** Define spacing between major content elements — card lists, section groups, and scrollable content bottom padding. Add rows for any recurring spacing pattern in your app.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> | Context | Token / Class | Value | Usage |
> |---------|---------------|-------|-------|
> | Between cards in list | `space-y-4` | 16px (1x) | Event cards, menu items |
> | Between major sections | `space-y-8` | 32px (2x) | Profile, Settings, Logout groups |
> | Content bottom padding | `pb-24` | 96px (6x) | Scrollable content (accounts for bottom nav) |
> | After content blocks | `mb-6` | 24px (1.5x) | Stats cards, profile card |
> | Info card grid gap | `gap-3` | 12px (0.75x) | 2-column stats display |
>
> *End of example — replace above with your own content block spacing.*

### Spacing Decision Tree

> [!NOTE]
> **🔵 GUIDANCE:** Write a quick-reference decision tree that agents can follow instead of memorising tables. This is the most valuable part of the spacing section — it turns spacing into a simple algorithm.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> 1. **Between related items?** → `gap-4` (16px)
> 2. **Between sections?** → `space-y-8` (32px)
> 3. **Below all headings?** → `mb-4` (16px) — no exceptions
> 4. **Above headings?** → `mt-6` for h2, `mt-4` for h3, `mt-8` for labels
> 5. **Scrollable content?** → `pb-24` (96px)
> 6. **Compact grouping (pills, badges)?** → `gap-2` (8px)
>
> **✅ DO:**
> - Use 16px as your default spacing
> - Double it (32px) for major breaks
> - Halve it (8px) for tight groupings
> - Always use `mb-4` below headings
> - Always use `pb-24` for scrollable content
>
> **❌ DON'T:**
> - Use arbitrary values outside the multiplier system
> - Mix different bottom margins for headings (always `mb-4`)
> - Place elements flush together (minimum 8px)
> - Forget bottom padding on scrollable content
>
> *End of example — replace above with your own spacing decision tree.*

---

## 📱 Screen Layout Standards

### Safe Zones (Mobile / Hybrid Only)

> [!NOTE]
> **🔵 GUIDANCE:** Document your safe area classes. Skip if web-only. These handle notch/status bar (top) and home indicator (bottom) on modern devices.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
> - `.safe-top` — top padding for notch/status bar: `padding-top: env(safe-area-inset-top)`
> - `.safe-bottom` — bottom padding for home indicator: `padding-bottom: env(safe-area-inset-bottom)`
> - `.pb-safe` — Tailwind utility: `padding-bottom: max(1rem, env(safe-area-inset-bottom))`
>
> *End of example — replace above with your own safe zones.*

> [!NOTE]
> Web portals: write "N/A — web app, no native safe areas"

### Screen Horizontal Padding

> [!NOTE]
> **🔵 GUIDANCE:** Define your app's padding rules per screen type. Different screens often use different horizontal padding (e.g., tight detail screens vs. breathing-room onboarding). Document each distinct padding level and where it applies.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — mobile):**
>
> | Context | Token / Class | Value | Usage |
> |---------|---------------|-------|-------|
> | Main Screen Headers | `px-6` | 24px | Upcoming, Discover, More screens |
> | Detail Screen Headers | `px-4` | 16px | Event Details, Settings |
> | Main Content | `px-6` | 24px | Primary content areas |
> | Login/Onboarding | `px-8` | 32px | Form screens needing breathing room |
>
> *End of example — replace above with your own screen padding.*

> [!TIP]
> **🟢 EXAMPLE (Web portal):**
>
> | Context | Token / Class | Value | Usage |
> |---------|---------------|-------|-------|
> | Sidebar | `w-64` | 256px | Fixed sidebar |
> | Main content | `px-8` | 32px | Content area |
> | Narrow content | `max-w-3xl mx-auto px-6` | — | Centered read forms |
>
> *End of example — replace above with your own screen padding.*

### Header Patterns

> [!NOTE]
> **🔵 GUIDANCE:** Document one block per screen type in your app. Cover height, behaviour (sticky/fixed/static), classes, and what content sits inside.
>
> Common screen types to consider:
> - Main tabs / dashboard (the top-level screens)
> - Detail screens (child screens with back navigation)
> - Form / onboarding screens (possibly no header, or minimal)
> - Modals / bottom sheets (if applicable)

> [!TIP]
> **🟢 EXAMPLE (Impulsy — mobile):**
>
> **Main Screens (Upcoming, Discover, More):**
> - Height: `h-14` (56px), Sticky: `sticky top-0 bg-white border-b z-50 safe-top`
> - Content: No top padding needed (header in document flow)
>
> **Detail Screens (Event Details, Settings):**
> - Height: `h-11` (44px — iOS native standard), Sticky
> - Back button: 44x44px, `-ml-4` flush offset, purple chevron, `active:opacity-60`
>
> *End of example — replace above with your own header patterns.*

> [!TIP]
> **🟢 EXAMPLE (Web portal):**
>
> **Top Navbar:**
> - Height: `h-16` (64px), Fixed: `fixed top-0 w-full bg-white border-b z-50`
> - Content: `pt-16` to clear fixed header
>
> **Sidebar:**
> - Width: `w-64` (256px) expanded, `w-16` (64px) collapsed
> - Position: `fixed left-0 top-16 h-[calc(100vh-4rem)]`
>
> *End of example — replace above with your own header patterns.*

### Full Screen Template

> [!NOTE]
> **🔵 GUIDANCE:** Provide a copy-paste-ready template for your most common screen type. This is the single most valuable thing for AI agents — they'll use it as the starting point for every new screen. Use your actual framework syntax.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — Angular):**
>
> ```html
> <div class="min-h-screen bg-white dark:bg-black">
>   <header class="sticky top-0 z-10 bg-white dark:bg-gray-900 border-b border-gray-200 dark:border-gray-700 safe-top">
>     <div class="max-w-md mx-auto px-6 h-14 flex items-center justify-between">
>       <h1 class="heading-2">Page Title</h1>
>     </div>
>   </header>
>
>   <main class="max-w-md mx-auto px-6 pt-6 pb-24 space-y-4">
>     <!-- Content -->
>   </main>
>
>   <nav class="fixed bottom-0 inset-x-0 bg-white dark:bg-gray-900 border-t z-50 safe-bottom">
>     <!-- Tab bar -->
>   </nav>
> </div>
> ```
>
> *End of example — replace above with your own full screen template.*

### Detail Screen Template

> [!NOTE]
> **🔵 GUIDANCE:** Provide a copy-paste-ready template for detail/child screens with back navigation.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — Angular):**
>
> ```html
> <div class="min-h-screen bg-white dark:bg-black">
>   <header class="sticky top-0 z-10 bg-white dark:bg-gray-900 border-b border-gray-200 dark:border-gray-700">
>     <div class="max-w-md mx-auto px-4 h-11 flex items-center gap-2">
>       <button (click)="goBack()" class="-ml-4 w-11 h-11 flex items-center justify-center active:opacity-60">
>         <lucide-icon name="chevron-left" size="24" class="text-purple"></lucide-icon>
>       </button>
>       <h1 class="heading-3">Screen Title</h1>
>     </div>
>   </header>
>
>   <main class="max-w-md mx-auto px-6 pt-6 pb-24">
>     <!-- Detail content -->
>   </main>
> </div>
> ```
>
> *End of example — replace above with your own detail screen template.*

**Back Button Standards (Mobile):**

> [!NOTE]
> **🔵 GUIDANCE:** Document your back button specs. Key details: touch target size (44px minimum on iOS), icon, colour, offset trick to align with screen edge, and interaction feedback.

### Content Width Constraint

> [!NOTE]
> **🔵 GUIDANCE:** If your app constrains content to a max width (mobile apps on tablets, centered web layouts), document it here. This prevents agents from creating full-bleed layouts where you want centered content.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> **Standard width:** `max-w-mobile` (448px) for mobile, content centered with `mx-auto`
>
> ```html
> <div class="w-full max-w-md mx-auto px-6">
>   <!-- Content -->
> </div>
> ```
>
> On desktop/tablet: Content stays centered at 448px max.
> On mobile: Full width with horizontal padding.
>
> *End of example — replace above with your own content width constraint.*

### Bottom Navigation (Mobile / Hybrid)

> [!NOTE]
> **🔵 GUIDANCE:** Document your persistent bottom nav specs. Key details: height, position, z-index, background, and how much bottom padding content needs to clear it. Skip if web sidebar layout.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
> - Height: 64px + safe area (`safe-bottom`)
> - Position: `fixed bottom-0 w-full`
> - Z-index: `z-50`
> - Background: `bg-white dark:bg-gray-900 border-t border-gray-200`
> - Content padding to clear: `pb-24` on all scrollable content
>
> *End of example — replace above with your own bottom navigation specs.*

### Sidebar Layout (Web Only)

> [!NOTE]
> **🔵 GUIDANCE:** Document sidebar specs. Skip if mobile-only. Cover: expanded/collapsed widths, position, collapse trigger, content offset.

> [!TIP]
> **🟢 EXAMPLE:**
> - Width expanded: 256px (`w-64`)
> - Width collapsed: 64px (`w-16`) — icons only
> - Position: `fixed left-0 top-16 h-[calc(100vh-4rem)]`
> - Collapse: below 1024px or toggle button
> - Content offset: `ml-64` when expanded, `ml-16` when collapsed
>
> *End of example — replace above with your own sidebar layout.*

### Responsive Breakpoints (Web Only)

> [!NOTE]
> **🔵 GUIDANCE:** Document your breakpoint system. Skip if mobile-only. Add as many breakpoints as your app actually uses.

> [!TIP]
> **🟢 EXAMPLE:**
>
> | Breakpoint | Width | Layout Changes |
> |-----------|-------|----------------|
> | Mobile | < 640px | Single column, bottom nav, full-width cards |
> | Tablet | 640–1024px | Collapsed sidebar, 2-column grid |
> | Desktop | > 1024px | Expanded sidebar, 3-column grid, data tables |
>
> *End of example — replace above with your own responsive breakpoints.*

### Platform-Specific Notes

> [!NOTE]
> **🔵 GUIDANCE:** Document anything platform-specific that affects layout. These are the gotchas that agents won't know unless you tell them.

> [!TIP]
> **🟢 EXAMPLE (Mobile / hybrid):**
> - iOS safe areas: notch (safe-top) and home indicator (safe-bottom) — use env(safe-area-inset-*)
> - Scroll behaviour: `position: sticky` preferred over `fixed` in Capacitor WebView
> - Keyboard avoidance: content shifts up when keyboard opens — bottom CTA stays above keyboard
> - Overscroll: `overscroll-contain` prevents pull-to-refresh interfering with custom scroll
>
> *End of example — replace above with your own platform-specific notes.*

> [!TIP]
> **🟢 EXAMPLE (Web):**
> - Scroll restoration: handled by router — `scrollPositionRestoration: 'enabled'`
> - Print stylesheet: hide sidebar, navigation, make content full-width
> - Content density: user preference stored in localStorage, default to 'comfortable'
>
> *End of example — replace above with your own platform-specific notes.*

---

## 🃏 Component Library

> [!NOTE]
> **🔵 GUIDANCE:** Document every reusable component in your app. For each, provide:
> 1. Token/class name agents should use in code
> 2. Visual description (colours, radius, shadows, sizing)
> 3. Code snippet showing the markup pattern
> 4. Interaction states (hover, active, disabled, focus)
>
> Your app might have 3 components or 30. Document what exists. Common components to consider:
> - Cards (static, interactive, list items)
> - Buttons (primary, secondary, destructive, icon-only, pill)
> - Icons & icon containers
> - Selection states (checkmarks, rings, toggles)
> - Dividers (solid, gradient, labelled)
> - Feedback (toasts, notices, banners, loading states)
> - Badges, pills, tags
> - Avatars / profile images
> - Navigation items (tab bar, sidebar items)
>
> For each component, always include a code snippet — this is the most valuable reference for agents.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> ### Cards
>
> | Token / Class | Usage | Style Summary |
> |--------------|-------|---------------|
> | `.card` | Base card | White bg, rounded-card (16px), shadow-card |
> | `.card-interactive` | Clickable | Card + hover shadow + active scale (0.98) |
> | `.card-padding` | Default padding | p-4 (16px) |
>
> ```html
> <!-- Static card -->
> <div class="card card-padding">
>   <p>Content</p>
> </div>
>
> <!-- Interactive card -->
> <button class="card-interactive card-padding">
>   <p>Clickable content</p>
> </button>
> ```
>
> ### Buttons
>
> | Token / Class | Usage | Style Summary |
> |--------------|-------|---------------|
> | `.btn-primary` | Primary CTA | Purple bg, white text, rounded-button (12px) |
> | `.btn-secondary` | Secondary action | White bg, gray-200 border, gray-700 text |
> | `.btn-destructive` | Destructive action | Red-600 bg, white text |
> | `.btn-icon` | Icon-only button | 40x40px circular, subtle hover bg |
>
> **All buttons include:** active scale (0.98), disabled opacity (0.5 + pointer-events-none), 150ms transitions.
>
> ```html
> <button class="btn-primary w-full">Continue</button>
> <button class="btn-secondary">Cancel</button>
> <button class="btn-destructive">Delete Account</button>
> ```
>
> ### Icons & Icon Containers
>
> **Library:** Lucide
> **Default stroke weight:** 2 (medium-bold)
>
> | Icon Size | Usage | Container Size |
> |-----------|-------|----------------|
> | 16px | Small inline, chevrons, checkmarks | None |
> | 20px | Navigation, tab bar, form controls | 40px |
> | 24px | Standard UI icons | 48px |
> | 28px | Large feature icons, hero sections | 56px |
>
> **Icon containers:** Coloured rounded squares that frame icons for visual hierarchy.
>
> | Container | Size | Radius | Usage |
> |-----------|------|--------|-------|
> | `.icon-container-sm` | 40x40px | rounded-lg | Navigation, tab bar |
> | `.icon-container` | 48x48px | rounded-xl | Category icons |
> | `.icon-container-lg` | 56x56px | rounded-2xl | Hero icons |
>
> ```html
> <div class="icon-container bg-purple-100">
>   <lucide-icon name="calendar" size="24" class="text-purple"></lucide-icon>
> </div>
> ```
>
> ### Selection States
>
> **Checkmarks:** 20x20px purple circle with white check (stroke-width 2.5), absolutely positioned top-right.
> **Selection rings:** `ring-2 ring-purple` on selected cards. `ring-2 ring-red-500` on error state.
>
> ```html
> <div class="card-interactive card-padding ring-2 ring-purple relative">
>   <div class="absolute -top-2 -right-2 w-5 h-5 bg-purple rounded-full flex items-center justify-center">
>     <lucide-icon name="check" size="12" class="text-white" strokeWidth="2.5"></lucide-icon>
>   </div>
>   <p>Selected item</p>
> </div>
> ```
>
> ### Dividers
>
> ```html
> <!-- Solid divider -->
> <div class="border-t border-gray-200 dark:border-gray-700"></div>
>
> <!-- Gradient divider (fades at edges) -->
> <div class="h-px bg-gradient-to-r from-transparent via-gray-200 to-transparent"></div>
>
> <!-- Divider with text label -->
> <div class="flex items-center gap-3">
>   <div class="h-px bg-gray-200 flex-1"></div>
>   <span class="text-xs text-gray-400 uppercase tracking-wide">Section Label</span>
>   <div class="h-px bg-gray-200 flex-1"></div>
> </div>
> ```
>
> ### Feedback / Toasts / Notices
>
> | Type | Classes |
> |------|----------|
> | Info | `bg-blue-50 border-2 border-blue-400 text-blue-900` |
> | Warning | `bg-yellow-50 border-2 border-yellow-400 text-yellow-900` |
> | Error | `bg-red-50 border-2 border-red-400 text-red-900` |
> | Success | `bg-green-50 border-2 border-green-400 text-green-900` |
>
> ```html
> <div class="bg-blue-50 border-2 border-blue-400 rounded-xl p-4">
>   <p class="text-blue-900"><span class="font-semibold">Note:</span> Your changes were saved.</p>
> </div>
> ```
>
> *End of example — replace above with your own component library.*

---

## 📝 Form Components

> [!NOTE]
> **🔵 GUIDANCE:** Document every form element pattern — input, textarea, select, checkbox, radio, toggle, date picker, etc. Include code snippets with exact classes and all visual states (default, focus, error, disabled).
>
> Pay special attention to **selects/dropdowns** — underdocumented selects are the fastest way to get inconsistent UI, because every developer will style them differently.
>
> For each form element, cover:
> - Default state classes
> - Focus state (ring/border colour)
> - Error state (red border + error message pattern)
> - Disabled state
> - Label placement and spacing
> - Helper text pattern

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> ### Standard Input
>
> ```html
> <div class="mb-4">
>   <label class="block text-sm font-medium text-gray-700 mb-2">Label</label>
>   <input class="w-full px-4 py-3 rounded-xl border border-gray-200 focus:ring-2 focus:ring-purple focus:border-transparent"
>          placeholder="Placeholder" />
>   <p class="mt-1 text-sm text-gray-600">Helper text</p>
> </div>
> ```
>
> **Design tokens:**
> - Padding: `px-4 py-3` (16px horizontal, 12px vertical)
> - Border radius: `rounded-xl` (12px)
> - Border: 1px solid gray-200
> - Focus: 2px ring in purple, border goes transparent
> - Error: `border-red-500 focus:ring-red-500` + red error message below
>
> ### Dropdown / Select
>
> ```html
> <select class="w-full px-4 py-3 pr-10 rounded-xl border border-gray-200 focus:ring-2 focus:ring-purple appearance-none bg-chevron-purple">
>   <option>Option 1</option>
> </select>
> ```
>
> **Key specs:**
> - Touch-friendly padding: `px-4 py-3`
> - Custom chevron: Purple (#8B5CF6), positioned `right 0.75rem center`, size `1.5rem`
> - Focus: `focus:ring-2 focus:ring-purple focus:border-transparent`
> - Right padding: `2.5rem` to accommodate chevron
> - Disabled: `opacity-50 cursor-not-allowed bg-gray-50`
>
> *End of example — replace above with your own form components.*

---

## 📦 Border Radius System

> [!NOTE]
> **🔵 GUIDANCE:** Define named radius tokens for consistency. Most apps need 3–5 levels. The goal is that developers never use raw `rounded-lg` — they use your semantic token like `rounded-card`.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> | Token / Class | Value | Usage |
> |--------------|-------|-------|
> | `rounded-button` | 12px | Buttons, inputs, small interactive elements |
> | `rounded-card` | 16px | Cards, containers, modals |
> | `rounded-pill` | 24px | Pills, tags, badges, search bar |
> | `rounded-full` | 9999px | Avatars, circular icon containers |
>
> *End of example — replace above with your own border radius system.*

---

## 🌟 Shadow System

> [!NOTE]
> **🔵 GUIDANCE:** Define named shadow tokens. Most apps need 2–4 levels (subtle, default, elevated, overlay). Specify exact CSS values so agents generate pixel-perfect shadows.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> | Token / Class | Value | Usage |
> |--------------|-------|-------|
> | `shadow-card` | `0 2px 8px rgba(0,0,0,0.08)` | Default card elevation |
> | `shadow-card-hover` | `0 4px 12px rgba(0,0,0,0.12)` | Hovered/lifted cards |
> | `shadow-header` | `0 1px 3px rgba(0,0,0,0.05)` | Sticky headers |
>
> **Dark mode:** Shadows are invisible on dark backgrounds. Use borders (`border-gray-700`) or background elevation (`bg-gray-800` → `bg-gray-700`) instead.
>
> *End of example — replace above with your own shadow system.*

---

## 📱 Mobile Patterns

> [!NOTE]
> Skip this entire section if building a web-only app.

> [!NOTE]
> **🔵 GUIDANCE:** Document mobile-specific patterns that don't fit in other sections. Common areas:
> - Native header (height per platform, alignment, border)
> - Fixed bottom CTA (blur backdrop, safe area padding, shadow)
> - Mobile canvas width (max-width on tablets)
> - Gesture patterns (swipe, pull-to-refresh)
> - Status bar treatment
>
> All of these are things agents will get wrong unless explicitly told.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> ### Native Header
> - Standard height: 44px (iOS native) for detail screens, 56px for main screens
> - Title alignment: Centered (iOS style)
> - Border: `border-b border-gray-200 dark:border-gray-700`
> - Back button: 44x44px, purple chevron-left, `-ml-4` offset, `active:opacity-60`
>
> ### Fixed Bottom CTA
> - Backdrop: `bg-white/80 backdrop-blur-md` (frosted glass effect)
> - Dark mode: `dark:bg-black/80 dark:backdrop-blur-md`
> - Padding: `px-6 py-4 pb-safe` (safe-area-aware)
> - Shadow: `border-t border-gray-200` (subtle, not a heavy shadow)
> - Button: full-width primary `btn-primary w-full`
>
> ```html
> <div class="fixed bottom-0 inset-x-0 bg-white/80 dark:bg-black/80 backdrop-blur-md border-t">
>   <div class="max-w-md mx-auto px-6 py-4 pb-safe">
>     <button class="btn-primary w-full">Continue</button>
>   </div>
> </div>
> ```
>
> ### Mobile Canvas Width
> - Max width: 448px (`max-w-md`)
> - Centering: `mx-auto`
> - On desktop/tablet: content centered, no stretch
> - On mobile: full width
>
> *End of example — replace above with your own mobile patterns.*

---

## 🌐 Web Patterns

> [!NOTE]
> Skip this section if building a mobile-only app.

> [!NOTE]
> **🔵 GUIDANCE:** Document web-specific patterns. Common areas:
> - Sidebar navigation (active state, collapse, icons)
> - Data tables (header style, row height, hover, pagination)
> - Breadcrumbs (separator, truncation, current page)
> - Content density options (if supported)
> - Modal/dialog patterns
> - Search/filter bars
>
> Add whatever patterns your web app uses.

> [!TIP]
> **🟢 EXAMPLE (Admin portal):**
>
> ### Sidebar Navigation
> - Width: 256px expanded, 64px collapsed
> - Active state: `border-l-4 border-purple bg-purple-50` + bold text
> - Icons: 20px, always visible even when collapsed
> - Hover: `bg-gray-50`
>
> ### Data Tables
> - Header: `sticky top-0 bg-gray-50 font-semibold text-sm text-gray-600 uppercase tracking-wide`
> - Row height: 48px (comfortable), 36px (compact)
> - Hover: `hover:bg-gray-50`
> - Borders: horizontal only, `border-b border-gray-100`
> - Pagination: Bottom of table, showing "1–20 of 156" with page size dropdown
>
> ### Breadcrumbs
> - Separator: `/` in gray-400
> - Current page: semibold, no link
> - Truncation: Collapse middle items with `…` when > 4 levels deep
>
> *End of example — replace above with your own web patterns.*

### Content Density (Optional)

> [!NOTE]
> If your web app supports multiple density modes, define them here. Common approach: 3 tiers.

> [!TIP]
> **🟢 EXAMPLE:**
>
> | Density | Row Height | Padding | Font Size | Usage |
> |---------|-----------|---------|-----------|-------|
> | Compact | 36px | py-1 px-3 | sm (14px) | Data-heavy screens, power users |
> | Comfortable | 48px | py-2 px-4 | base (16px) | Default |
> | Spacious | 64px | py-4 px-6 | lg (18px) | Read-focused, accessibility |
>
> *End of example — replace above with your own content density tiers.*

---

## 💡 Best Practices

### ✅ DO

> [!NOTE]
> **🔵 GUIDANCE:** Write your app's specific best practices. These should be real rules learned from experience — not generic advice. Examples below.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
> - Use semantic class names — `.heading-1` instead of raw `.text-2xl .font-bold`
> - Combine design system classes — `<button class="btn-primary w-full">`
> - Use spacing utilities for consistent vertical rhythm
> - Use icon containers with coloured backgrounds for visual hierarchy
> - Follow the spacing decision tree for every layout decision
> - Always test dark mode when adding new components
>
> *End of example — replace above with your own best practices.*

### ❌ DON'T

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
> - Don't inline raw colour values — use design tokens
> - Don't create custom shadows — use the shadow system
> - Don't use arbitrary spacing — follow the base unit system
> - Don't skip semantic HTML — use `<button>`, `<h1>`, etc.
> - Don't use `bg-gray-800` for elements inside `bg-gray-800` containers (invisible in dark mode)
>
> *End of example — replace above with your own "don't" list.*

### Deprecated Patterns

> [!NOTE]
> **🔵 GUIDANCE:** Document patterns you've tried and rejected. This is critical — it prevents AI agents from regenerating old approaches you've already moved away from. Include what changed and WHY.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> `position: fixed` headers → `position: sticky` headers
> → Fixed caused content to hide behind header in iOS WebView/Capacitor. Sticky keeps header in document flow.
>
> Inline dark mode conditionals → Tailwind `dark:` classes
> → Logic-based dark mode was error-prone and verbose. Tailwind's utility approach is more maintainable.
>
> *End of example — replace above with your own deprecated patterns.*

---

## 📋 Component Examples (Reference Implementations)

> [!NOTE]
> **🔵 GUIDANCE:** Include 2–3 complete component examples that combine multiple patterns from your design system. These "golden examples" are the most valuable part of the file — agents will pattern-match against them when building similar UI.
>
> Good examples to include:
> - An interactive list item (card + icon + text + selection state)
> - A complete screen layout (header + content + bottom CTA)
> - A form section (labels + inputs + validation + submit)
> - A data display (card with stats, badges, metadata)
>
> Use your actual framework syntax — Angular templates, React JSX, Vue SFC, etc.

> [!TIP]
> **🟢 EXAMPLE (Impulsy — Angular):**
>
> ### Example 1: Selectable Interest Card
>
> ```html
> <button class="card-interactive card-padding flex items-center gap-3 w-full"
>         [class.ring-2]="selected" [class.ring-purple]="selected"
>         (click)="toggle()">
>   <div class="icon-container bg-purple-100">
>     <lucide-icon name="music" size="24" class="text-purple"></lucide-icon>
>   </div>
>   <div class="flex-1 text-left">
>     <div class="heading-3">Live Music</div>
>     <div class="body-text-sm">Concerts, festivals, DJ sets</div>
>   </div>
>   <div *ngIf="selected" class="w-5 h-5 bg-purple rounded-full flex items-center justify-center">
>     <lucide-icon name="check" size="12" class="text-white" strokeWidth="2.5"></lucide-icon>
>   </div>
> </button>
> ```
>
> ### Example 2: Full Screen with Header + Bottom CTA
>
> ```html
> <div class="min-h-screen bg-white dark:bg-black">
>   <header class="sticky top-0 z-10 bg-white dark:bg-gray-900 border-b border-gray-200 dark:border-gray-700">
>     <div class="max-w-md mx-auto px-4 h-11 flex items-center">
>       <button (click)="goBack()" class="-ml-2 p-2">
>         <lucide-icon name="arrow-left" size="20"></lucide-icon>
>       </button>
>     </div>
>   </header>
>
>   <div class="max-w-md mx-auto px-6 pt-6">
>     <h1 class="heading-1 mb-4">Page Title</h1>
>     <p class="body-text-sm mb-8">Description text goes here.</p>
>   </div>
>
>   <div class="max-w-md mx-auto px-6 pb-24 space-y-4">
>     <!-- Content cards -->
>   </div>
>
>   <div class="fixed bottom-0 inset-x-0 bg-white/80 dark:bg-black/80 backdrop-blur-md border-t border-gray-200 dark:border-gray-700">
>     <div class="max-w-md mx-auto px-6 py-4 pb-safe">
>       <button class="btn-primary w-full">Continue</button>
>     </div>
>   </div>
> </div>
> ```
>
> *End of example — replace above with your own component examples.*

---

## ✅ Quick Start Checklist

> [!NOTE]
> **🔵 GUIDANCE:** Write a checklist that a developer or AI agent should verify after building ANY new screen. This should be tailored to your app's specific patterns. The categories below are a good starting point — add or remove items to match your stack.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
>
> **Layout:**
> - [ ] Correct header height (56px main, 44px detail)
> - [ ] Content width wrapper (`max-w-md mx-auto`) applied
> - [ ] Correct horizontal padding (`px-6` main, `px-4` detail headers)
> - [ ] Bottom padding `pb-24` accounts for bottom nav
> - [ ] Safe area classes applied (safe-top on headers, safe-bottom on bottom nav)
>
> **Spacing:**
> - [ ] Base unit system followed (no arbitrary values)
> - [ ] `mb-4` below all headings (no exceptions)
> - [ ] `space-y-4` between cards in lists
> - [ ] `space-y-8` between major sections
>
> **Typography:**
> - [ ] Semantic heading classes (`.heading-1`, `.heading-2`, `.heading-3`)
> - [ ] Body text classes (`.body-text`, `.body-text-sm`, `.body-text-xs`)
> - [ ] Form labels use `.label-text`, helpers use `.helper-text`
>
> **Components:**
> - [ ] Cards use `.card` / `.card-interactive` + `.card-padding`
> - [ ] Buttons use `.btn-primary` / `.btn-secondary` / `.btn-destructive`
> - [ ] Icons from Lucide, stroke-weight 2, correct sizes
> - [ ] Feedback messages use toast/notice pattern with correct severity colours
>
> **Testing:**
> - [ ] Tested on target device/breakpoint
> - [ ] Content doesn't hide behind sticky header
> - [ ] Dark mode works (all bg, text, border classes have `dark:` variants)
> - [ ] Edge cases: empty state, loading state, error state, long text truncation
>
> *End of example — replace above with your own quick start checklist.*

---

## 🔗 Related Documentation

> [!NOTE]
> **🔵 GUIDANCE:** Link to all related files in your repo. Agents use these links to find supplementary information. Add whatever files are relevant to your project.

> [!TIP]
> **🟢 EXAMPLE (Impulsy):**
> - **Dark mode standards:** `docs/STANDARDS_DARK_MODE.md`
> - **Design principles:** `docs/GUIDE_DESIGN.md`
> - **Colour config:** `tailwind.config.js` + `src/styles.scss`
> - **Global styles:** `src/styles.scss`
> - **Component architecture:** `docs/ARCHITECTURE.md`
> - **Data model:** `docs/DATA_MODEL.md`
>
> *End of example — replace above with your own related documentation links.*

---

## 🔗 How to Use This File

### With AI Coding Agents (Copilot, Cursor, Aider, etc.)

Add this file to your repository and reference it in your agent instructions:

```markdown
# In your .github/copilot-instructions.md or equivalent:
When creating or modifying UI components, follow the design system in `docs/STANDARDS_DESIGN_SYSTEM.md`.
```

The agent will read the file and apply your exact patterns when generating code.

### With Chat Models (ChatGPT, Claude, etc.)

Paste the file (or relevant sections) into a conversation:

> "Here is my app's design system. Create a mockup for a user profile screen following these standards."

The model will generate HTML/code that matches your spacing, colours, typography, and component patterns.

### With Your Team

- **New developers:** "Read the design system file before building any UI."
- **Code reviews:** "Does this PR follow the design system? Check the checklist."
- **Design discussions:** "Propose the change as an update to the standards file."

---

**Remember:** This file is living documentation. It evolves with your product. Update it when patterns change, and treat changes to this file with the same care as changes to your code.
