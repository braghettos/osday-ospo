# Credits

| Asset | Source | Used on |
|---|---|---|
| `assets/qr-repo.png` | Generated from `https://github.com/braghettos/osday-ospo` via the [`qrcode`](https://www.npmjs.com/package/qrcode) npm package | Closing slide |

## A note on photographic background imagery

An earlier revision of this deck embedded three Unsplash photographs as blurred slide backgrounds (one on the title slide, one on each section-divider). They were **removed** because:

- Background imagery makes automated accessibility tooling (axe-core, pa11y) unable to compute foreground/background contrast, generating false-positive findings on every text element on those slides.
- Text-on-photo contrast is unstable and degrades badly under projector conditions, especially at the back of the room.
- Decorative imagery is invisible to screen-reader users — the inclusivity gain claimed for it doesn't reach the audience members who most need accessibility help.

Solid `#000000` slides with high-contrast typography are the more honestly accessible choice. The Codemotion guideline about "diverse images for inclusivity" remains a good rule for *meaningful* inline imagery on content slides — but not for decorative backgrounds where they compete with the content.
