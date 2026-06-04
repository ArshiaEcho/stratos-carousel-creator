# 03 — Prompt Higgsfield well

Two things decide render quality: which model you use, and how you structure the prompt. You mostly talk to Claude in plain English, but the structure underneath is what makes a card clean.

## The prompt grammar

Order it the same way every time:

```
[FORMAT + ASPECT] → [SCENE / BACKGROUND] → [SUBJECT + ACTION] → [STYLE ANCHOR] → [NEGATION]
```

The negation block (`no emoji, no neon outline, no AI gloss`) is the single biggest quality lever. Keep it on every card.

## Pick the right model

| You need… | Reach for | Why |
|---|---|---|
| Text baked into the image (headlines, numerals) | Nano Banana / GPT Image | Best legible, accurate on-image type |
| A recurring face / spokesperson | Soul + trained character | Locks one identity across shots |
| Mood, abstract, atmospheric stills | Flux | Painterly, fast to iterate |
| Video with audio | Seedance / Veo | Native lip-sync, SFX, music |
| Cheap, high-volume video | Kling Turbo | The volume play for batch testing |

For carousels, the default is **`nano_banana_2`** — fast, cheap, good with the on-card text. Escalate a single card to a stronger text model only if legibility fails twice.

## The one cost rule

Resolution is the price lever, not the model. The same render at high resolution can cost **10 to 15 times** more than standard. Default everything to standard resolution while you iterate. Only upscale the one card that actually ships.

A full 5-card carousel on `nano_banana_2` is about **15 credits**. A single-card re-render is about **3 credits**. The free tier (150 credits/month) covers roughly ten carousels.

## A worked example (Stratos cover)

```
Modern tech-magazine Instagram card, 4:5 portrait. Background: deep dark teal-ink
#0A1E22. A chrome-liquid sculpture lower-right, ~100% of frame, cyan #6EE6E0 highlights,
teal #45777D shadows, warm gold #CDB06A interior glow. Cinematic depth-of-field, subtle
film grain. Center: large Cabinet Grotesk italic headline in cream #F7F1E1 reading
'Three things you should actually know in AI today', with the single word 'actually' in
cyan. Bottom-center: small mono '@yourbrand' in cream. Highly legible.
No emoji, no neon outline, no AI gloss.
```

It runs all five grammar steps in order and ends with a negation. Quote the exact copy (`reading 'â€¦'`) so the model renders your words, not a paraphrase.

## Sensitive-content trip-wires

Higgsfield's safety filter can reject legitimate prompts. Common triggers: anatomical words near body parts, "rip / tear / shatter" near a person (fine on objects), real brand or celebrity likeness, and words like "sexy" even on inanimate products. If a card is blocked, read the prompt back, swap the trigger word for a neutral synonym, and move the action onto an object rather than a person.

Full card-by-card templates: `plugin/skills/stratos-carousel-creator/references/prompt-templates.md`.
