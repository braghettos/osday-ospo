# Open Source in Production · OSDay 2026

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Slide deck for the talk **"Open Source in Production: Why Your Company Needs an OSPO (Before It's Too Late)"** by Diego Braga (CTO & Co-founder, Krateo PlatformOps) at [OSDay 2026](https://osday.dev), Florence — Friday 24 April, 12:30–13:15.

**Format:** 45 minutes (≈35 min talk + 10 min Q&A) · ~30 slides
**Source:** `slides.md` (Marp markdown)

## Render the deck

Install once:
```sh
npm install
```

Then:
```sh
npm run preview      # live preview in browser
npm run watch        # rebuild HTML on save
npm run build:html   # → dist/slides.html
npm run build:pdf    # → dist/slides.pdf
npm run build:pptx   # → dist/slides.pptx (PowerPoint)
npm run build:notes  # → dist/slides-notes.pdf (with speaker notes)
```

No global install needed — `marp-cli` runs via `npx`.

## Structure

| Part | Slides | Time |
|------|--------|------|
| 1 · The Problem | 5 | 5 min |
| 2 · What is an OSPO | 5 | 5 min |
| 3 · The 4 Pillars | 6 | 8 min |
| 4 · ROI | 4 | 6 min |
| 5 · Real Stories (success + failure) | 6 | 8 min |
| 6 · Where to Start | 3 | 3 min |
| 7 · Wrap & Q&A | 2 + Q&A | 10 min |

## Sources

- TODO Group · [ospoglossary.todogroup.org](https://ospoglossary.todogroup.org/)
- TODO Group · [ospomindmap.todogroup.org](https://ospomindmap.todogroup.org/)
- TODO Group · [case studies](https://todogroup.org/resources/case-studies/) (Capital One, Microsoft, SAP, Porsche, Comcast, Uber, Red Hat)
- Black Duck · OSSRA 2026 report (open source vulnerability + license stats)
- Public incident retrospectives: Equifax (2017), Heartbleed (2014), Log4Shell (2021), xz utils backdoor (2024)

## License

Slides and accompanying text are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — share, remix, and adapt with attribution to Diego Braga.

## Editing notes

- Speaker notes are HTML comments (`<!-- ... -->`) inside each slide. They show up in the `build:notes` PDF.
- All speaker placeholders are filled in. Talk is scheduled **Friday 24 April 2026, 12:30–13:15** at OSDay 2026, Florence.
- Theme is `uncover` with a dark `invert` class. Swap to `gaia` or `default` if you prefer a lighter look.
