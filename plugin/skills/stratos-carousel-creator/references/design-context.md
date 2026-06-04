# Design Context

Load this before any render. It is what keeps every Higgsfield call on-brand. A blank prompt gives you a generic card; a loaded design system gives you a feed that reads as one brand.

This is the **Stratos default**. To re-skin: replace the values, keep the shape, and Claude will carry your look into every card.

## Where it comes from

A design system does not have to be hand-made. Use **Claude Design** — Claude's own design ability — to generate one: ask for a palette, a type pairing, layout grammar, and voice rules for your brand, and iterate until it feels right. The Stratos system below started as a Claude Design handoff. Then distill it to one screen (this file) and load it at the top of any rendering session, or keep it in `CLAUDE.md` so it loads automatically.

## The brief (copy, then adapt)

```
# DESIGN CONTEXT — load before any render

PALETTE
  ink     #0A1E22   (background, always)
  cream   #F7F1E1   (all body + headlines)
  cyan    #6EE6E0   (primary accent: numerals, one emphasis word)
  gold    #CDB06A   (hairlines, italic emphasis, warm days)
  teal    #45777D   (sculpture shadow, support only)

TYPE
  display + body : Cabinet Grotesk (italic for headlines)
  mono / labels  : JetBrains Mono (small, low-opacity)

LAYOUT RULES (hard)
  - 4:5 portrait. Dark ink background with soft mesh + film grain.
  - Numerals are cyan everywhere, EXCEPT the punctuation card (cream).
  - Hairlines always gold. Body text always cream. Max 5 colors per card.
  - A recurring chrome-liquid sculpture is the brand character.
  - Mono metadata is always small and low-opacity.

VOICE (never violate)
  - No em dashes. No corporate filler. No AI-hype words. No scarcity.
  - No emoji on tiles. No raw competitor screenshots.
```

## How to swap it for your brand

1. **Palette** — pick 3 to 5 colors: one dark base, one light text, one primary accent, one secondary, one support. Keep it to five. Put the hex codes in the prompt so the model matches them.
2. **Type** — one display face, one mono/label face. Name them in every prompt.
3. **Hero element** — Stratos uses a chrome-liquid sculpture. Yours could be a product, a mascot, a material, or a recurring shape. It should move through the carousel the same way (cover → watch → take over → mirror → exit).
4. **Voice rules** — list the words and patterns you never want. The negation block is what kills generic AI output.

Once swapped, the flow system and prompt templates work unchanged. Same pipeline, your brand.

## Why this matters

Higgsfield is only as on-brand as the context you hand it. The design context is the difference between five posts that look like five tools made them, and a feed that looks like one studio. It is the single highest-leverage thing you load before a render.
