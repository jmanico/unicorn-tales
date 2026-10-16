---
version: alpha
name: Unicorn Tales Demo
description: Quiet, readable story pages with a single plum unicorn mark.
colors:
  primary: "#49345C"
  ink: "#292431"
  surface: "#FFF9EF"
typography:
  heading:
    fontFamily: system-ui, sans-serif
    fontSize: 32px
    fontWeight: 700
    lineHeight: 1.25
  body:
    fontFamily: system-ui, sans-serif
    fontSize: 18px
    fontWeight: 400
    lineHeight: 1.6
  story:
    fontFamily: system-ui, sans-serif
    fontSize: 24px
    fontWeight: 400
    lineHeight: 1.6
  label:
    fontFamily: system-ui, sans-serif
    fontSize: 16px
    fontWeight: 700
    lineHeight: 1.5
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  page: 960px
  reading: 640px
  target: 44px
rounded:
  control: 8px
  panel: 16px
components:
  page:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    padding: "{spacing.md}"
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.surface}"
    typography: "{typography.label}"
    rounded: "{rounded.control}"
    padding: "{spacing.md}"
  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.primary}"
    typography: "{typography.label}"
    rounded: "{rounded.control}"
    padding: "{spacing.md}"
  input:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.control}"
    padding: "{spacing.md}"
  story-panel:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    typography: "{typography.story}"
    rounded: "{rounded.panel}"
    padding: "{spacing.lg}"
---

# Unicorn Tales

## Overview

[REQUIREMENTS.md](REQUIREMENTS.md) is the sole source for behavior and workflows. This document describes an unimplemented demo for ages 6–12, with English content, fictional families, parent administration, branching stories, and educational challenges. Visual tokens are new demo design decisions made under the user's authorization; they are not measurements of an existing product.

Use a calm, uncluttered reading surface with clear choices. **ASSUMPTION (DQ-1):** a unicorn is an appropriate identity for the repository name; the requirements prescribe no mascot. Existing brand guidelines are **UNKNOWN**. The mark is adopted for the demo; final brand adoption is **TO BE DECIDED**, tracked below.

Format follows the [official Google DESIGN.md specification](https://github.com/google-labs-code/design.md/blob/main/docs/spec.md), version alpha.

## Colors

Only three opaque colors are allowed: plum `primary` for actions, outlines, focus and the mark; `ink` for reading; warm `surface` for backgrounds and reversed labels. Status is communicated with words and symbols, never color alone.

Allowed foreground/background pairs are exhaustive; reversal has the same ratio:

| Foreground | Background | Contrast | Use |
| --- | --- | --- | --- |
| ink | surface | 14.41:1 | All body text, labels, status text and icons |
| primary | surface | 10.39:1 | Actions, links, boundaries, focus and logo |
| surface | primary | 10.39:1 | Primary-action labels, selected controls and logo eye |

Each pair exceeds 4.5:1 for normal text and 3:1 for large text, essential graphics, controls and focus. Never combine ink and primary, lower opacity, add gradients, or place text over an image. Hover, pressed, disabled and error states retain their assigned pair; distinguish them using outlines, underlines, symbols and explicit labels. No additional background colors are permitted.

## Typography

Use the local system sans-serif stack; no font downloads. Use heading for page titles, body for parent forms and descriptions, story for child reading and parent storytelling, and label for controls. Keep sentence case and left alignment. Use the same story size for both age bands; the requirements change vocabulary and word count, not legibility. Allow text enlargement to 200% without losing controls or content.

## Layout

One main column; page maximum `spacing.page`, reading maximum `spacing.reading`. At 320 px width, preserve `spacing.md` side margins and stack all actions without horizontal scrolling. Use md between related fields, lg between groups and xl between sections. Child controls are at least target by target with sm separation. Keep focus order identical to reading order.

Keep the fictional-data/local-demo notice visible. Parent screens group family members, child settings and educational material. Child screens prioritize the current scene, then its challenge when due, then the two story choices. Include the required exit action; no dashboard metrics, rewards, social features or new navigation destinations.

## Elevation & Depth

Flat surfaces, no shadows or overlays. Use a 2 px primary outline to identify controls and grouped panels; surface against surface is not a meaningful boundary without this outline. Use headings and spacing for hierarchy.

## Shapes

Use control rounding for actions and inputs, panel rounding for story groups. Icons are simple solid shapes or 2 px strokes, with visible text labels for actions.

`logo.svg` is a single plum unicorn-head silhouette with a horn, ear and surface-colored eye. Preserve its square viewBox, colors and proportions. Show at 24 px or larger; reserve 4 px clear space. Place only on surface. Use an accessible name when the mark stands alone and treat it as decorative beside the same visible product name. Do not add a wordmark, badge, gradient or surrounding illustration.

## Components

| Pattern | Compact behavior and states | Requirement |
| --- | --- | --- |
| Action | Primary for the screen's main action; outlined secondary for alternatives. Focus: 3 px primary ring outside a 3 px surface gap, never clipped. Hover underlines its label; pressed adds an inner surface outline on primary or primary outline on surface. Disabled keeps contrast and states why it is unavailable. | NFR-4 |
| Field / choice tag | Persistent label and helper text; errors use an icon plus a specific correction. Selected tags use the primary pair and a check; unselected tags use the secondary pair and outline. Keyboard selection remains visible. | FR-8.2, FR-9.1 |
| Family / child panel | Alias, age band, preference tags and parent controls. Empty lessons show setup guidance; no preselection. Capacity errors name the applicable limit. Parent sign-in is a labeled username/password form. | FR-8.1–8.4, FR-9.3, FR-12.2 |
| Shared settings | Explicit Save; a stale edit shows Reload and explains that resubmission is needed. A policy change replaces affected story content with a restart message. | FR-9.4–9.5 |
| Story | Scene number out of five, text, then two full-width choice actions for scenes 1–4. The final scene ends the story. Failure preserves the last valid scene and offers Retry or Return to family screen. | FR-10.1–10.3 |
| Parent storytelling | Story typography with pause, repeat scene, next choice and restart. The adult selects the child's spoken choice; no recording control. | FR-10.4 |
| Homework selector | Plain-text entry with 200-character limit, supported subject selection and accepted-format help. Choose exactly one homework item or subject/topic for an educational story. Unsupported input explains supported alternatives. | FR-11.1–11.3 |
| Challenge | Three-option, true/false or integer response. Show encouraging feedback and explanation; allow one retry or Skip. After a second wrong answer reveal the answer. Never require correctness to continue. | FR-11.5–11.7 |
| Review / delete / reset | Parent-only record review, JSON export and clearly labeled removal/reset actions. Show which records will be removed beside the action. Do not expose these controls in child mode. | FR-9.6, FR-12.3 |

All controls have accessible names; grouped options have a group label. Announce error and challenge feedback without moving focus unexpectedly. Use no motion-dependent meaning or automatic animation. Parent values, child wishes, lesson choices and challenge feedback use only the behaviors in REQUIREMENTS.md.

## Do's and Don'ts

- Do preserve the reading hierarchy, text labels, keyboard access and exact allowed contrast pairs.
- Do explain empty, rejected, stale, failed and completed states in simple English.
- Do use the existing catalog and five-scene progression; do not add features to fill visual space.
- Do not add a UI/CSS framework, remote assets, decorative motion, grades, streaks or public comparisons.
- Do not claim that design tokens alone prove full WCAG conformance; verify the implemented interface against NFR-4.

## Open Questions

- **DQ-1 — DEFERRED:** Should the demo unicorn identity become the final brand? Existing brand guidelines are UNKNOWN; final adoption is TO BE DECIDED. Owner: product owner. Dependency: final branded release only. The selected demo mark and tokens remain usable now. Close when the owner approves the identity or supplies replacement guidelines; then refresh this file, logo.svg and AC-20.
