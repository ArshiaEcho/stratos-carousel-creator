# Carousel Flow System

The rules that make five cards read as one story. Locked for the Stratos default; adapt the values (not the structure) for your brand.

The hero element is a **recurring chrome-liquid sculpture**. It is a character, not a decoration. Its position, scale, and dominance change card by card to give the swipe a narrative shape. Replace it with your own brand element if you re-skin.

## Within-day flow (the 5-card story arc)

| Card | Purpose | Sculpture | Numeral | Reading flow |
|---|---|---|---|---|
| 1. Cover | Greet, set date + theme | today's rotation position, full size | none | left → right (type, then artifact) |
| 2. Headline 01 | First story | upper-right, ~35% of frame | cyan, upper-left, big | left → right |
| 3. Headline 02 (PUNCTUATION TILE) | Stop-scroll moment | center, ~60% of frame, gold glow up | **cream** (intentional break), upper-left | type + artifact integrated |
| 4. Headline 03 | Third story, mirror | lower-left, ~35% of frame | cyan, upper-right, big | right → left |
| 5. List + CTA | Close, hand off to comments | upper-right, ~20%, smallest | none, type-led | left → right, type-led |

**Why it works:** the sculpture greets, watches, takes over, mirrors, exits. The eye follows an S-curve. Cards 1 and 4 mirror each other. Card 3 is the only card where the artifact dominates the type. Cards 2 and 4 are typographic peers with flipped composition.

## Hard rules within a day

- Maximum **one** punctuation tile (full sculpture takeover) per carousel.
- Numerals are **always cyan** EXCEPT on the punctuation card, where they shift to **cream** to signal the tonal break.
- Hairlines are **always gold**.
- Body text is **always cream**.
- Mono metadata is **always small and low-opacity**.
- Source attribution sits at the bottom of headline cards, mirrored to the headline alignment.

## Across-day rotation (keeps the feed grid alive)

The cover composition rotates by weekday so a 5-day stretch shows five distinct covers but one unmistakable system.

### Sculpture position rotation

| Day | Cover sculpture position |
|---|---|
| Monday | Lower-right (the standard) |
| Tuesday | Upper-right |
| Wednesday | Center hero, full bleed |
| Thursday | Lower-left |
| Friday | Upper-left |

### Color emphasis rotation (warm/cool rhythm)

| Day | Emphasis |
|---|---|
| Monday | Cyan-dominant (cool, fresh start) |
| Tuesday | Gold-dominant (warm, premium) |
| Wednesday | Cyan-dominant (mid-week reset) |
| Thursday | Gold-dominant |
| Friday | Cyan-dominant (close the week) |

Cool, warm, cool, warm, cool. The render routine reads this table to set today's treatment. It should not improvise. Weekend has no rule.

### Combined table (the one the skill reads)

| Day | Sculpture position | Color emphasis |
|---|---|---|
| Mon | Lower-right | Cyan |
| Tue | Upper-right | Gold |
| Wed | Center hero | Cyan |
| Thu | Lower-left | Gold |
| Fri | Upper-left | Cyan |

## Anti-rotation rules (what NOT to vary)

- Typography hierarchy is identical every day.
- The sculpture form, lighting style, and depth-of-field do not change. Only position and scale rotate.
- Background is always dark ink with a soft mesh gradient. The mesh emphasis shifts with the color rotation; the ink base does not.
- The layout grid (margins, mono header position, safe zones) is fixed.

## QA checklist (run before delivering)

- [ ] Card 1 sculpture in today's correct position; brand mark present
- [ ] Cards 2 and 4 are mirrored compositions
- [ ] Card 3 is the only punctuation tile
- [ ] Numerals are cyan everywhere except card 3 (cream)
- [ ] Hairlines are gold
- [ ] Body type is cream
- [ ] Color emphasis matches the day (warm or cool dominant)
- [ ] No emoji on any tile
- [ ] No raw competitor screenshots
- [ ] Mono metadata is small and low-opacity
- [ ] Voice scan passes (no em dashes, no filler, no hype, no scarcity)

If any check fails, re-render that card once with a stricter prompt or skip it.

## Special tiles (optional, use sparingly)

- **Weekly Tools List**: 5 cards, warm/amber dominant, reads as a weekly edit rather than daily news.
- **Vendor Comparison**: 3 or 5 cards comparing two tools; split lighting (cyan vs gold) suggests the comparison.
- **Workflow Demo**: sculpture more abstract, terminal-flow integrated, type-led, focused on a build.

## Evolving the system

Lock a new system for at least 90 days before changing it. Consistency is the brand. After 90 days, candidate evolutions: a sixth sculpture position for weekend cadence, a seasonal tertiary accent, or a distinct sculpture variant for Reels.
