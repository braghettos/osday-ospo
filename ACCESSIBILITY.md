# Accessibility Statement

This statement describes the accessibility of the slide deck and supporting materials in this repository: **"Open Source in Production: Why Your Company Needs an OSPO (Before It's Too Late)"** by Diego Braga, presented at OSDay 2026 in Florence on Friday 24 April 2026.

The deck is published at [github.com/braghettos/osday-ospo](https://github.com/braghettos/osday-ospo) under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Conformance target

The materials are designed to meet **Web Content Accessibility Guidelines (WCAG) 2.1, Level AA** — the technical standard referenced by the harmonised European standard **EN 301 549** (the standard the European Accessibility Act, Directive (EU) 2019/882, points to for digital content).

**Scope clarification.** A conference slide deck on a public source-code repository is not an in-scope "product" or "service" under the EAA. Conformance is therefore aspirational and self-declared, not a regulated obligation. This statement reflects the spirit of the EAA's accessibility goals applied to talk materials.

## Conformance status

**Partially conformant** — the materials substantially meet WCAG 2.1 Level AA. All known issues are documented under "Known limitations" below.

## What's been done

### In the slides (`slides.md` → `dist/slides.html`)

- **Color contrast (WCAG 1.4.3 / 1.4.6).** All foreground colors on the pure-black slide background were verified manually:

  | Foreground | Use | Ratio | AA (≥4.5) | AAA (≥7) |
  |---|---|---:|:---:|:---:|
  | `#FFFFFF` | body, header, footer | **21.00 : 1** | PASS | PASS |
  | `#FFD166` | strong, h1 | **14.56 : 1** | PASS | PASS |
  | `#A8E6FF` | h2, links | **15.43 : 1** | PASS | PASS |
  | `#B5F0B5` | h3, ok markers | **16.10 : 1** | PASS | PASS |
  | `#FF8A8A` | warning markers | **9.25 : 1** | PASS | PASS |
  | `#D0D0D0` | small text, source captions | **15.96 : 1** | PASS | PASS |

- **Typography (WCAG 1.4.4 / 1.4.12).** Body text 30 px, small text 24 px, line-height 1.5, letter-spacing 0.01em.
- **Font (perceivability).** [Atkinson Hyperlegible](https://www.brailleinstitute.org/freefont/) (Braille Institute, optimised for low-vision readers) with **Verdana** fallback (designed for screen readability and present on every platform).
- **Information not conveyed by colour alone (WCAG 1.4.1).** Status markers (✅ success, 🔥 failure) are paired with text labels; warning items use `class="warn"` plus the word "warn" in context.
- **Semantic structure (WCAG 1.3.1, 2.4.6).** Marp generates proper `<h1>`, `<h2>`, `<h3>`, `<table>`, `<th>`, `<td>` markup. The document declares `lang="en"` (WCAG 3.1.1).
- **Decorative emoji (WCAG 1.1.1).** Purely decorative emoji were stripped from list items and table cells so screen readers don't announce them. Semantic emoji (✅/🔥) remain because they carry meaning.
- **Focus visible (WCAG 2.4.7).** Links receive `outline: 2px solid #FFD166` on focus.
- **No motion / no auto-advance (WCAG 2.2.2, 2.3.1).** No animation, no time-based content, no parallax.
- **Keyboard navigation (WCAG 2.1.1).** Slides advance with arrow keys, space, Page-Up/Down, Home/End, and `F` for fullscreen.
- **Marp on-screen controls disabled (HTML build).** The Marp framework's hover-revealed control bar (next/prev/fullscreen/overview/presenter buttons) was disabled in the HTML build (`--bespoke.osc=false`) because its low-contrast styling failed automated audit and is duplicated by keyboard shortcuts.

### In the repo

- **`TRANSCRIPT.md`** — a linear plain-text version of the talk for screen-reader users, attendees who prefer reading, or anyone who can't see the slides clearly.
- **Multiple output formats** — the deck builds to HTML, PDF, and PPTX, allowing each user to pick the format that works best for their assistive technology.
- **Public source** — every change is reviewable in the Git history.

## Audit method

Automated audit run on **2026-04-23** against `dist/slides.html` using:

- [pa11y](https://github.com/pa11y/pa11y) v9
- [axe-core](https://github.com/dequelabs/axe-core) v4.11 (via pa11y's `axe` runner)
- [HTML CodeSniffer](https://squizlabs.github.io/HTML_CodeSniffer/) (via pa11y's `htmlcs` runner)

Re-run locally with:

```sh
npm run audit:a11y
```

The full audit JSON is checked in at `audits/2026-04-23-pa11y.json`.

### Audit findings

| Round | Errors | Status |
|---|---:|---|
| Baseline | 9 | All `color-contrast` |
| After theme refresh + OSC disabled | 4 | All `color-contrast`, all `needsFurtherReview: true` |
| Final | 4 | False positives (see "Known limitations") |

## Known limitations

1. **axe-core "needs-further-review" findings on the title slide (4 instances).** axe reports 4 colour-contrast warnings on the title slide for `<header>`, `<footer>`, `<em>` and `<strong>` elements. Every one is flagged with `needsFurtherReview: true`, meaning **axe could not determine the background colour, not that contrast actually failed.** This is a documented limitation of axe-core's contrast detection when slides are rendered inside Marpit's `<svg><foreignObject>` containers (the rendering technique that lets Marp keep a fixed 16:9 aspect ratio). Manual verification confirmed all four use white-on-black or amber-on-black, ratios between 14.56 : 1 and 21 : 1 — well above WCAG AAA's 7 : 1 threshold.

2. **PDF output has no semantic tagging.** The PDF generated by Marp via headless Chromium is image-pixel-perfect but is **not a tagged PDF**. Screen readers will not be able to read it directly. Use `dist/slides.html` or `TRANSCRIPT.md` as the accessible alternatives. (PDF/UA conformance for Marp output is tracked upstream and would require a different toolchain.)

3. **No formal user testing with disabled users.** The deck has not been reviewed by users who rely on screen readers or other assistive technology in production. This is a meaningful gap. Feedback from such users is welcome via the contact channel below.

4. **Live-content accessibility depends on the venue.** Live captions (CART), sign-language interpretation, accessible seating, step-free stage access and the conference's own digital surfaces are the responsibility of the OSDay 2026 organisers ([osday.dev](https://osday.dev)).

## Feedback and contact

Found an accessibility issue, or want a different format? Please contact:

- **Diego Braga** — [linkedin.com/in/diegobraga86](https://www.linkedin.com/in/diegobraga86)
- **GitHub issues** — [github.com/braghettos/osday-ospo/issues](https://github.com/braghettos/osday-ospo/issues)

## Statement metadata

- **Statement created:** 2026-04-23
- **Last updated:** 2026-04-23
- **Statement language:** English
- **Statement applies to:** the slide deck, transcript, and supporting materials in this repository at the time of writing.
- **Preparation method:** self-evaluation by the speaker; automated tooling (pa11y + axe-core); manual contrast verification.
