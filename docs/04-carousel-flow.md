# 04 — The carousel flow

What makes five cards read as one story instead of five posters. A recurring sculpture (your hero element) moves through the swipe on an S-curve: it greets, watches, takes over, mirrors, then exits.

## The 5-card arc

| Card | Role | Sculpture | Numeral |
|---|---|---|---|
| 1 | Cover | today's rotation position, full size | none |
| 2 | Headline 01 | upper-right, ~35% | cyan, big, upper-left |
| 3 | Punctuation tile | center, ~60%, gold glow | **cream** (the one break) |
| 4 | Headline 03 | lower-left, ~35% (mirror of card 1) | cyan, big, upper-right |
| 5 | List + CTA | upper-right, ~20%, smallest | none, type-led |

Cards 1 and 4 mirror each other. Card 3 is the only card where the artifact dominates the type. The numerals are cyan everywhere except card 3, where they go cream to mark the tonal break.

## Weekday rotation

The cover composition rotates so a week of covers looks varied but unmistakably one system.

| Day | Sculpture position | Color emphasis |
|---|---|---|
| Mon | Lower-right | Cyan |
| Tue | Upper-right | Gold |
| Wed | Center hero | Cyan |
| Thu | Lower-left | Gold |
| Fri | Upper-left | Cyan |

Weekend has no rule. The skill will ask you to pick a composition if you run it on a Saturday or Sunday.

## Install and run

In Claude Code:

```text
/plugin marketplace add ArshiaEcho/stratos-carousel-creator
/plugin install stratos-carousel-creator@stratos
/stratos-carousel-creator
```

The repo is private, so make sure your GitHub account has access. You can also clone it into your project's `.claude/skills/` directory directly.

Then give it a brief: a date, your top 3 stories (title + short summary + source), and optionally 5 supporting titles for the list card. The skill derives today's rotation, renders all five cards in parallel through Higgsfield, runs the QA checklist, saves them to `./carousel/{date}/`, and reports the credit cost.

## QA before you post

The skill checks every card against the locked list: sculpture in the right position, cards 2 and 4 mirrored, card 3 the only punctuation tile, numerals cyan except card 3, hairlines gold, body cream, no emoji, voice clean. Any card that fails gets one stricter re-render.

Full system: `plugin/skills/stratos-carousel-creator/references/flow-system.md`.
