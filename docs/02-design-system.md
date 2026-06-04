# 02 — Give Claude a design system

This is the difference between five posts that look like five tools made them, and a feed that looks like one studio. Higgsfield is only as on-brand as the context you hand it.

## The idea

Before you render anything, load a **design context**: your palette (with hex codes), your type, a few hard layout rules, and a short list of things to never do. Claude then carries that into every Higgsfield call, so the whole carousel speaks one language.

Without it, every prompt re-explains your brand from scratch, and the results drift. With it, you paste one brief and every card inherits it.

## Let Claude build it (Claude Design)

You do not need to be a designer. Use **Claude Design** — Claude's own design ability — to generate the system:

1. Ask Claude Design for a palette, a type pairing, layout grammar, and voice rules for your brand.
2. Iterate until it feels right.
3. Distill the result to one screen: 3 to 5 colors, two fonts, a handful of hard rules, and a "never do" list.
4. Save it (see `plugin/skills/stratos-carousel-creator/references/design-context.md`) and load it at the top of any rendering session, or keep it in your `CLAUDE.md` so it loads automatically.

The Stratos system shipped with this skill started as a Claude Design handoff, then got distilled into the one-page brief the skill loads.

## The Stratos brief (the default)

```
PALETTE
  ink    #0A1E22   background, always
  cream  #F7F1E1   all body + headlines
  cyan   #6EE6E0   primary accent (numerals, one emphasis word)
  gold   #CDB06A   hairlines, italic emphasis, warm days
  teal   #45777D   sculpture shadow, support only

TYPE
  display + body : Cabinet Grotesk (italic for headlines)
  mono / labels  : JetBrains Mono (small, low-opacity)

VOICE (never violate)
  No em dashes. No corporate filler. No AI-hype words. No scarcity.
  No emoji on tiles. No raw competitor screenshots.
```

## Swap it for your brand

Replace the values, keep the shape:

- **Palette** — one dark base, one light text, one primary accent, one secondary, one support. Five max.
- **Type** — one display face, one mono/label face. Name both in every prompt.
- **Hero element** — Stratos uses a chrome-liquid sculpture as a recurring character. Yours could be a product, a material, a mascot, or a shape. It moves through the carousel the same way.
- **Voice** — the words and patterns you never want. The negation block is what kills generic AI output.

The flow and prompt templates do not change. Only the look does.

Full reference: `plugin/skills/stratos-carousel-creator/references/design-context.md`.
