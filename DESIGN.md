---
version: alpha
name: Picky Party
description: "ASSUMPTION: A calm, welcoming identity for cooking events with individual food needs."
# ASSUMPTION: All tokens are proposed design decisions, not supplied brand facts.
colors:
  primary: "#184D3D"
  neutral: "#FFF9ED"
  ink: "#202A24"
  error: "#8B302C"
typography:
  headline:
    fontFamily: "system-ui, sans-serif"
    fontSize: 2rem
    fontWeight: 700
    lineHeight: 1.25
  title:
    fontFamily: "system-ui, sans-serif"
    fontSize: 1.5rem
    fontWeight: 700
    lineHeight: 1.3
  body:
    fontFamily: "system-ui, sans-serif"
    fontSize: 1rem
    fontWeight: 400
    lineHeight: 1.5
  label:
    fontFamily: "system-ui, sans-serif"
    fontSize: 1rem
    fontWeight: 700
    lineHeight: 1.5
  caption:
    fontFamily: "system-ui, sans-serif"
    fontSize: 0.875rem
    fontWeight: 400
    lineHeight: 1.5
rounded:
  sm: 4px
  md: 8px
  lg: 16px
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  content: 72rem
  reading: 42rem
  control: 44px
  focus: 2px
components:
  page:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.neutral}"
    typography: "{typography.label}"
    rounded: "{rounded.md}"
    padding: "{spacing.md}"
  button-secondary:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.primary}"
    typography: "{typography.label}"
    rounded: "{rounded.md}"
    padding: "{spacing.md}"
  field:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.sm}"
    padding: "{spacing.sm}"
  notice-error:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.error}"
    typography: "{typography.body}"
    rounded: "{rounded.md}"
    padding: "{spacing.md}"
  status:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.primary}"
    typography: "{typography.label}"
  logo:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.primary}"
    size: 32px
  focus-indicator:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.ink}"
    size: "{spacing.focus}"
---

## Overview

[REQUIREMENTS.md](REQUIREMENTS.md) is the sole authority for behavior, roles, states, and workflows. This file defines their visual presentation. No application implementation exists.

ASSUMPTION: The display name is Picky Party. A warm neutral surface, deep green actions, and a single rounded mark suit a shared cooking event. Treat food needs respectfully. Use direct labels such as "Food needs", "Review request", and "Paid booking".

Existing brand guidelines and audience research are UNKNOWN. All token values and visual measurements are ASSUMPTION: proposed design choices, not observed facts. Final brand approval is TO BE DECIDED in DQ-1.

The document follows the [official Google format](https://github.com/google-labs-code/design.md/blob/main/docs/spec.md), with YAML tokens and its eight prose sections in order. Open Questions is an extension section.

## Colors

Use only the four declared colors. `neutral` is the canvas and every unfilled surface; `ink` is body text and focus; `primary` is actions, outlines, and the mark; `error` is failure text and its outline. Status text supplies meaning independently of color.

These are the complete permitted foreground/background pairs. Ratios use the declared opaque sRGB values and are rounded down to two decimals.

| Foreground | Background | Contrast | Use |
| --- | --- | --- | --- |
| ink | neutral | 14.12:1 | Text, labels, placeholders, focus indicators |
| primary | neutral | 9.23:1 | Links, outlines, icons, selection marks, logo |
| neutral | primary | 9.23:1 | Filled action text and selected-control marks |
| error | neutral | 7.83:1 | Error text, error icons, invalid-control outlines |

Every pair exceeds 4.5:1 for normal text and 3:1 for large text, necessary graphics, controls, and focus indicators. See WCAG 2.2 guidance for [text contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html) and [non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

Do not introduce other pairings, opacity, gradients, or tinted states. Keep hover, pressed, loading, and disabled states within the same pairs; distinguish them with outlines, underlines, and explicit labels. Never place ink or error on primary. Neutral containers require a primary outline when their boundary conveys meaning.

## Typography

ASSUMPTION: Use the system sans-serif family until DQ-2 is resolved. No font download is required. Use headline for the page title, title for sections, body for content, label for controls, and caption for secondary metadata. Keep prices, deadlines, ingredient amounts, and error messages at body size or larger. Use sentence case and visible field labels. Do not truncate food needs, ingredients, prices, or states.

## Layout

ASSUMPTION: Use a fluid reading order with `content` as the maximum workspace width and `reading` for long forms. Use `md` outer spacing, `lg` group gaps, `sm` field gaps, and `xl` between major sections. Reflow when content no longer fits; device breakpoints are TO BE DECIDED in DQ-3.

Use one column for narrow views. At wider sizes, place the event summary beside the current form without changing reading order. Keep the price, cutoff, and order state beside the relevant action. Calendar month and list views remain available; use the list for narrow presentations. Present ingredient rows as labelled groups when columns do not fit. Meet REQUIREMENTS.md NFR-3 at a 320-pixel viewport and 200% text size.

## Elevation & Depth

ASSUMPTION: Use a flat surface with spacing, headings, and primary outlines for grouping. No shadows or overlays are needed by these patterns. Every meaningful outline uses primary on neutral. Keep live notices in the document flow so they do not cover actions or move focus.

## Shapes

ASSUMPTION: Use `sm` corners for fields, `md` for actions and notices, and `lg` for event containers. Keep icons simple and label actions with text.

`logo.svg` is one P monogram on a neutral square. Its rounded bowl and broad stem remain visible at small sizes. Use primary for the mark and neutral for its fixed background. Preserve the viewBox and aspect ratio; do not recolor, crop, add effects, or place text inside the mark. Use its title as the accessible name. ASSUMPTION: Minimum display size is 16 pixels; preferred navigation size is the logo token. Keep clear space equal to one quarter of the rendered width. The mark is brand identity, not a dietary certification badge.

## Components

All patterns inherit page colors unless a component token provides a permitted alternative. Visual arrangements are ASSUMPTION; behavior comes from the cited requirements.

| Pattern | Compact presentation | Requirement source |
| --- | --- | --- |
| Account access | Labelled email and display-name fields; distinct verification, sent-link, and failure messages. | FR-6.1 through FR-6.4 |
| Event card and calendar entry | Title first; date and time zone, city, per-person USD price, then booking state. Open the same event detail. | FR-2.11; FR-5 |
| Event editor | Group event details, schedule, capacity, price, and dishes. Keep preview and launch distinct. Show errors beside retained values. | FR-1; FR-2.3 through FR-2.7 |
| Event detail | Menu and ingredients, schedule, price, cutoff, availability. Reveal the exact address only to the allowed audience. | FR-2.11; FR-2.12; FR-7.10 |
| Food request | One labelled group per dish with diet choices, explicit restrictions, special needs, preferences, and omission. Keep consent separate. | FR-3.2 through FR-3.10 |
| Request review | Show requests beside proposed ingredients and handling notes. Name the next actor. Distinguish approval from Attendee acceptance and payment. | FR-3.13 through FR-3.19 |
| Checkout and receipt | Final price, cancellation terms, hold expiry, and order state. Show the booking reference only after confirmation. | FR-8.6; FR-8.9; FR-8.12; FR-8.18 |
| Cancellation and refund | Separate booking state from refund state. Keep a pending or failed refund visible after cancellation. | FR-9.1 through FR-9.11 |
| Cook view | Order reference, Attendee, paid state, dish portions, approved ingredients, and handling notes. Keep unconfirmed orders clearly excluded. | FR-4.4; FR-4.5; FR-4.8 |
| Shopper list | Ingredient and variant first, then base, extra, shopping quantity, and unit. Show calculation time and print action. | FR-4.6; FR-4.7; FR-10 |
| Live notice | Text state and last update time; preserve focus and reading position. A disconnected view must look stale. | FR-4.9 through FR-4.11; NFR-3.6 |
| Organizer and Admin records | Label event, payment, refund, and payout states separately. Show each action only in its permitted context. | FR-6.6 through FR-6.17; FR-9.12 through FR-9.18 |

Actions use the primary token for the current step and the secondary token for alternatives. ASSUMPTION: Interactive targets are at least `control` in both dimensions. Long labels wrap. Links use primary on neutral with an underline. Errors use the error token plus explanatory text. Selection controls use primary outlines on neutral; selected controls may use neutral marks on primary.

Focus uses an ink outline of `focus` thickness with an equally wide neutral gap. The neutral gap separates the outline from filled controls, so both outline edges meet a neutral surface. Keep focus fully visible. Disabled controls retain their contrast and show why the action is unavailable. Loading preserves the action label and adds a text state.

Reuse the exact order, payment, refund, and event state names from REQUIREMENTS.md. An approval is not a booking; a pending payment is not paid attendance. Empty views explain that no matching records exist. Failures retain entered data and identify the failed action. Do not manufacture example events, prices, ratings, attendance, or testimonials.

## Do's and Don'ts

- Do keep USD prices, deadlines, time zones, and ingredient units explicit.
- Do keep dish omissions and substitutions visible through review and preparation.
- Do use the specified color pairs for every interactive state and meaningful graphic.
- Do preserve keyboard access, accessible names, reading order, and live-update focus.
- Do treat the SVG as the sole primary mark.
- Do not use a diet label or the logo as proof that food is medically suitable.
- Do not expose private food notes in public cards, shopper views, or email presentations.
- Do not add behaviors, actions, or states that REQUIREMENTS.md does not define.

## Open Questions

- **DQ-1** Final approval of the proposed name styling, palette, and P monogram is TO BE DECIDED. Existing brand assets are UNKNOWN; this identity is ASSUMPTION.
- **DQ-2** A dedicated brand typeface is TO BE DECIDED. Existing font rights are UNKNOWN; system sans-serif is the ASSUMPTION for this version.
- **DQ-3** Exact responsive breakpoints are TO BE DECIDED after content measurement. Content-driven reflow is the ASSUMPTION; the required viewport and text-size tests still apply.
