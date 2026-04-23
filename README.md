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

## Accessibility

The deck targets **WCAG 2.1 Level AA**, the technical baseline referenced by the **European Accessibility Act (EAA)** via the harmonized standard **EN 301 549**. See "Compliance scope" below for the legal nuance.

### What's in the deck

- **Color contrast.** All foreground colors verified at WCAG AA against pure-black background (body white at 21:1, accent amber/sky/mint at ≥13:1, warning red at ≥7:1). Color is never the sole carrier of meaning.
- **Font.** [Atkinson Hyperlegible](https://www.brailleinstitute.org/freefont/) (Braille Institute, designed for low vision) with **Verdana** fallback (designed for screen readability and present on every system).
- **Type size.** Body 30px / small 24px / line-height 1.5 — comfortably above the 16px minimum for projected slides.
- **Semantic markup.** Marp generates proper `<h1>/<h2>/<h3>` and `<table>` elements; the deck declares `lang="en"`.
- **Decorative emoji** are stripped or ignored by screen readers; informative ones (✅ success, 🔥 failure) stay paired with text.
- **No motion / no auto-advance / no time-based content.** Keyboard-navigable in browser presentation mode.
- **[`TRANSCRIPT.md`](TRANSCRIPT.md)** ships in this repo — a linear plain-text version for screen-reader users, attendees who prefer reading, or anyone who can't see the slides clearly.

### What I haven't verified

- Automated axe-core / Lighthouse audit on the rendered HTML
- Manual screen-reader pass (VoiceOver / NVDA / JAWS)
- Verification with users who have visual or cognitive disabilities

These should be run before claiming WCAG conformance formally.

### Compliance scope · the EAA question honestly

The European Accessibility Act (Directive (EU) 2019/882, in application since **28 June 2025**) covers a defined list of **products and services placed on the EU market** — e-commerce, banking, e-readers, transport, audiovisual media, telephony, and so on. A **conference slide deck published on GitHub does not fall under EAA scope** as a regulated service. The conference website and any e-ticketing flow likely do.

What we *can* and *do* claim: the deck targets **the same technical standard the EAA relies on** — WCAG 2.1 AA via EN 301 549 — so the content meets the spirit of the law even where the letter doesn't apply. Where conformance is required (the conference's own digital surfaces, an organisation's accessibility statement), formal testing and a published accessibility statement are needed.

### Delivery tips (for the speaker)

- **Verbalize visuals.** Don't say "as you can see" — describe what's on the slide so attendees following on audio still get the content.
- **Pause** after stats and quotes for processing.
- **Face the audience** when speaking (lip-reading, expression).
- **Repeat questions** before answering.
- **Share the slides + transcript link** at the start *and* end — let people follow along on their own device.
- **Ask the conference about live captions (CART) and ASL/LIS interpretation.** OSDay can confirm what's available.

### What the venue/conference owns

These are not in this repo's control — coordinate with [osday.dev](https://osday.dev):

- Step-free stage and reserved accessible seating
- Live captions (CART) on screen during the talk
- Sign-language interpretation
- Microphone and clear PA for hard-of-hearing attendees
- Accessible bathrooms, quiet room

## License

Slides and accompanying text are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — share, remix, and adapt with attribution to Diego Braga.

## Editing notes

- Speaker notes are HTML comments (`<!-- ... -->`) inside each slide. They show up in the `build:notes` PDF.
- All speaker placeholders are filled in. Talk is scheduled **Friday 24 April 2026, 12:30–13:15** at OSDay 2026, Florence.
- Theme is `uncover` with a dark `invert` class. Swap to `gaia` or `default` if you prefer a lighter look.
