# Prompt Templates

The five card prompts, self-contained. This is the production grammar Stratos uses. Fill the `{placeholders}` from the brief, keep the structure, keep the negation line.

Every prompt follows: **`[format + aspect] → [scene / background] → [subject + action] → [style anchor] → [negation]`**.

## Default palette (Style B)

Swap these hex codes for your brand's design context. The templates reference them by name.

```
ink    #0A1E22   background, always
cream  #F7F1E1   all body + headlines
cyan   #6EE6E0   primary accent (numerals, one emphasis word)
gold   #CDB06A   hairlines, italic emphasis, warm-day glow
teal   #45777D   sculpture shadow, support only
```

Type: **Cabinet Grotesk** (display + body, italic for headlines), **JetBrains Mono** (labels, metadata, small + low-opacity).

## Shared base (prepend to every card)

```
Modern tech-magazine Instagram carousel card, 4:5 portrait. STYLE B aesthetic.
Background: deep dark teal-ink hex #0A1E22 with soft mesh gradient and subtle film grain.
Chrome-liquid sculpture in {position}, occupying {scale} percent of frame, tinted with
cyan hex #6EE6E0 highlights, deep teal hex #45777D shadows, warm gold hex #CDB06A interior
glow. Cinematic depth-of-field. Highly legible. No emoji, no neon outline, no AI gloss.
```

`{position}` = the card's sculpture position. `{scale}` = its percentage. For the **cover**, use today's rotation position (see flow-system.md) at 100%.

---

## Card 1: Cover

```
{base, position = today's rotation, scale = 100}
Top-left: small monospace 'YOUR BRAND  /  {YYYY.MM.DD}' in soft cream JetBrains Mono.
Center: large Cabinet Grotesk italic display headline in cream hex #F7F1E1 reading
'{cover headline}', with the single word '{emphasis word}' in saturated cyan hex #6EE6E0.
Bottom-center: small monospace lowercase '@yourbrand' in cream.
Style: cinematic premium tech magazine.
```

## Card 2: Headline 01

```
{base, position = upper-right, scale = 35}
HEADLINE CARD. Big Cabinet Grotesk italic numeral '01' in saturated cyan hex #6EE6E0
with a thin gold hairline beneath, left-aligned. Below: bold Cabinet Grotesk display
headline in cream reading exactly: {story 1 title}. Below that, a two-line summary in
cream Cabinet Grotesk regular: {story 1 summary}. Source attribution in JetBrains Mono
cream reading 'SOURCE  /  {story 1 source}', left-aligned.
```

## Card 3: Punctuation tile (the one break)

```
{base, position = center, scale = 60}
PUNCTUATION CARD, sculpture takes 60 percent of frame, gold glow more prominent.
Top-left: Cabinet Grotesk italic numeral '02' in soft CREAM hex #F7F1E1 (not cyan) with
a thin cyan hairline beneath. Below: bold Cabinet Grotesk display headline in cream
reading exactly: {story 2 title}. Below that, a two-line summary in cream Cabinet Grotesk
regular: {story 2 summary}. Bottom-left: small monospace 'SOURCE  /  {story 2 source}'
in JetBrains Mono cream.
```

## Card 4: Headline 03 (mirror of card 2)

```
{base, position = lower-left, scale = 35}
HEADLINE CARD. Big Cabinet Grotesk italic numeral '03' in saturated cyan hex #6EE6E0
with a thin gold hairline beneath, right-aligned. Below: bold Cabinet Grotesk display
headline in cream reading exactly: {story 3 title}. Below that, a two-line summary in
cream Cabinet Grotesk regular: {story 3 summary}. Source attribution in JetBrains Mono
cream reading 'SOURCE  /  {story 3 source}', right-aligned.
```

## Card 5: List + CTA

```
{base, position = upper-right, scale = 20}
LIST CARD, sculpture as a small accent in the upper-right corner only (~20 percent).
Top-left: small monospace eyebrow 'AND ALSO TODAY' in JetBrains Mono cream. Below:
italic Cabinet Grotesk display heading in cream reading: Five more stories that shipped.
Below the heading, 5 bulleted lines in Cabinet Grotesk regular cream, each with a small
cyan dot bullet. The 5 lines, exactly:
{01. extra title one}
{02. extra title two}
{03. extra title three}
{04. extra title four}
{05. extra title five}
Below the list: a thin gold hairline rule, then an italic line in cream with the word
'SOURCES' in cyan reading: Comment SOURCES for the links. Bottom-center: tiny monospace
lowercase '@yourbrand' in cream.
```

If there are no extras, replace the list with a single centered CTA line and keep the sculpture accent.

## Notes

- Quote exact text in the prompt (`reading exactly: …`) so the model renders the copy you want, not a paraphrase.
- Keep the negation (`No emoji, no neon outline, no AI gloss`) on every card. It is the single biggest quality lever.
- For text-heavy cards, `nano_banana_2` is the default. If legibility fails twice, escalate that one card to a stronger text model (Nano Banana Pro or GPT Image) and accept the higher cost.
- Default to standard resolution while iterating. Only upscale the cards that ship.
