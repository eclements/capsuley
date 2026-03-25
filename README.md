# Capsuley

Spec-driven templates for building apps with AI coding agents. Derived from [Impulsy](https://impulsy.at), a production event discovery app built entirely with agentic workflows.

## What's in here

| Template | What it does |
|----------|-------------|
| [STANDARDS_DESIGN_SYSTEM_TEMPLATE.md](standards/STANDARDS_DESIGN_SYSTEM_TEMPLATE.md) | Guide + template for creating a design system standards file that AI agents read before generating UI. Covers colours, spacing, typography, components, screen templates, dark mode, and platform patterns. |

## How to use

1. Copy the template into your repo as `docs/STANDARDS_DESIGN_SYSTEM.md`
2. Read the guidance comments, look at the Impulsy examples, write your own values
3. Reference it in your agent instructions (`.github/copilot-instructions.md` or equivalent)
4. Agents now generate UI that matches your design system

## Who is this for

Developers building apps with AI coding agents (Copilot, Cursor, Claude, etc.) who want consistent UI output across every generated screen.

The templates are based on Angular + Capacitor. Web-focused teams can expand the sidebar, data table, and breakpoint sections. Native app teams can adapt the component patterns to SwiftUI or Jetpack Compose. The structure works regardless of framework.

## Origin

These templates come from building [Impulsy](https://impulsy.at) with developer-led, spec-driven agentic coding. Every screen in the app was built by AI agents reading standards files like these.

## Licence

MIT
