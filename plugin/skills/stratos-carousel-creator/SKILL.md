---
name: stratos-carousel-creator
description: Render a complete on-brand 5-card Instagram carousel from a short content brief, using the Higgsfield MCP and a loaded design system. Use when the user says "make a carousel", "render today's carousel", "Stratos carousel", "build an IG carousel", or wants a 5-card swipe post generated from a digest, headline, or topic. Applies a locked 5-card flow (cover, two headlines, a punctuation tile, a list/CTA) and the user's design context. Re-skinnable for any brand.
---

# Stratos Carousel Creator

Turn one short brief into a finished, on-brand **5-card Instagram carousel**, rendered through the Higgsfield MCP and governed by a loaded design system. The five cards read as one story, not five posters: a recurring sculpture (or your brand's hero element) moves through the swipe on an S-curve.

This skill is **self-contained and re-skinnable**. The default look is the Stratos "Style B" system. Swap the design context (see `references/design-context.md`) and the same pipeline renders your brand.

## Prerequisites (check first)

1. **Higgsfield MCP connected.** Tools named `mcp__higgsfield__generate_image`, `job_status`, `reveal_generation`, and `balance` must be available. If not, tell the user to run:
   `claude mcp add --transport http --scope user higgsfield https://mcp.higgsfield.ai/mcp`, then `/mcp` → Authenticate.
2. **A design context.** Read `references/design-context.md`. If the user has their own brand brief, use theirs instead. Never render without one loaded.

## When to invoke

- "Make me a carousel from this digest / these stories"
- "Render today's carousel"
- "Build a 5-card IG post about X"
- "Re-render card 3"

## Inputs

Gather these. Ask only for what is missing; infer sensible defaults.

1. **Date** (defaults to today). Used to derive the daily rotation.
2. **Top 3 stories / points**, each a title + a one or two line summary + a source (source optional).
3. **5 supporting items** (titles only) for the final list card. Optional; if absent, make card 5 a single CTA.
4. **Design context**, from `references/design-context.md` or the user's own.

If the user pastes a digest, parse the top 3 and the extras from it. If they give a single topic, expand it into 3 angles yourself and confirm before rendering.

## Process

### Step 1: Load the design system

Read `references/design-context.md` (or the user's brief). Hold the palette, type, layout rules, and voice rules in context. Every prompt you build must obey them.

### Step 2: Derive today's flow rules

Read the date, get the weekday, and look up the rotation in `references/flow-system.md`:

| Day | Cover sculpture position | Color emphasis |
|---|---|---|
| Mon | Lower-right | Cyan |
| Tue | Upper-right | Gold |
| Wed | Center hero | Cyan |
| Thu | Lower-left | Gold |
| Fri | Upper-left | Cyan |

Weekend has no rule. If the date is Sat/Sun, ask the user to pick a composition before proceeding.

### Step 3: Build the 5 prompts

Use the templates in `references/prompt-templates.md`. The within-day card rhythm is fixed regardless of weekday; only the **cover** uses the day's sculpture position. Each prompt follows the grammar: `[format + aspect] → [scene] → [subject + action] → [style anchor] → [negation]`, and bakes in the loaded palette hex codes and type.

The 5 cards:

| Card | Role | Sculpture | Numeral |
|---|---|---|---|
| 1 | Cover | today's position, full size | none |
| 2 | Headline 01 | upper-right, ~35% | cyan, big, upper-left |
| 3 | Punctuation tile | center, ~60%, gold glow | **cream** (the one break), upper-left |
| 4 | Headline 03 | lower-left, ~35% (mirror of card 1) | cyan, big, upper-right |
| 5 | List + CTA | upper-right, ~20%, smallest | none, type-led |

### Step 4: Render 5 cards in parallel

Call `mcp__higgsfield__generate_image` five times **in a single message** (parallel), with:
- `model`: `nano_banana_2` (default; best speed/text balance). Use a stronger text model only if the user asks.
- `aspect_ratio`: `4:5`
- `count`: `1`
- `prompt`: the card prompt from Step 3.

Then poll each with `mcp__higgsfield__job_status` until terminal, and pull final image URLs with `mcp__higgsfield__reveal_generation` (or `show_generations`). Save the five images to `./carousel/{YYYY-MM-DD}/` as `card-1-cover.png` … `card-5-list.png`.

### Step 5: QA pass

Open each PNG with the Read tool and check against the locked checklist (full list in `references/flow-system.md`):

- [ ] Card 1: sculpture in today's correct position, brand mark present
- [ ] Cards 2 & 4: mirrored compositions, numerals cyan
- [ ] Card 3: the only punctuation tile, numeral in **cream** (not cyan), sculpture ~60%, gold glow
- [ ] Card 5: sculpture small accent (~20%), list bullets, CTA closer
- [ ] All cards: dark ink background, cream body, cyan numerals (except card 3), gold hairlines
- [ ] Voice scan: no em dashes, no corporate filler, no AI-hype lexicon, no emoji on tiles

Re-render any failing card once, with a stricter prompt that quotes the exact text and the rule it broke. Max 1 retry per card.

### Step 6: Deliver

Show the user the five cards, then a short summary:
- Credit cost (check `mcp__higgsfield__balance` before/after; ~3 cr/card on `nano_banana_2`, ~15 cr/carousel).
- Today's flow rules applied.
- The output folder path.
- Ask: ✅ approve, 🔁 re-render a specific card, or 🚫 discard.

If the user has a delivery target (a Telegram bot, a Slack channel, a Buffer queue), hand the saved files off to whatever tool they use. The core skill stays delivery-agnostic.

## Voice + style rules (locked, never violate)

- NO em dashes. Use commas, periods, parentheses, or restructure.
- NO corporate filler ("leverage synergies", "best-in-class", "industry-leading").
- NO AI-hype lexicon ("revolutionary", "game-changing", "next-gen", "cutting-edge").
- NO scarcity ("limited spots", "act now", "this week only").
- NO emoji on tile designs. Mono metadata + clean serif/sans only.
- NO competitor screenshots in raw form. Always re-set in your own type.

(These are the Stratos defaults. If the user's design context defines different voice rules, follow theirs.)

## Cost guardrails

- Full carousel on `nano_banana_2`: ~15 credits.
- Single-card re-render: ~3 credits.
- Default to standard resolution; only upscale a card that actually ships.
- Suggest a daily ceiling (Stratos uses 50 cr/day) and stop if hit.

## Reference files

- `references/flow-system.md`, the locked 5-card flow + weekday rotation + QA checklist.
- `references/prompt-templates.md`, the 5 card prompt templates (self-contained, copy of the production grammar).
- `references/design-context.md`, the design system brief to load before rendering, plus how to swap it for your brand.

## Make it yours

This renders Stratos carousels out of the box. To make your own brand's engine: edit `references/design-context.md` (palette, type, voice), and optionally adjust the sculpture/hero element and rotation in `references/flow-system.md`. The pipeline does not change. The look does.
