# vivekadithya.com — a playable business card

The personal site of Vivek Adithya, QA automation engineer. One self-contained
static HTML file — no build step, no dependencies, no JavaScript framework.
Everything (styles, scripts, the pixel avatar, the favicon) lives in
`index.html`; the only network requests are three Google Fonts.

## Run locally

```bash
cd personal_website
python3 -m http.server 8788
# open http://127.0.0.1:8788
```

Opening `index.html` directly in a browser also works.

## Deploy

It is a single static file — any static host works:

- **GitHub Pages** — push this folder to a repo, Settings → Pages → deploy from
  branch (`/root`). Or drop it in a `docs/` folder of any existing repo.
- **Netlify** — drag the folder onto https://app.netlify.com/drop.
- **Cloudflare Pages / Vercel** — connect the repo, framework preset "None",
  output directory `/` (root).

Point the DNS for `vivekadithya.com` at whichever host you choose.

## Features (all in one file)

- **Dice-roll system** — palette, background pattern and greeting re-roll on
  every visit from a seeded PRNG. The seed lives in the URL (`?roll=123`), so a
  look is shareable and reproducible.
- **Chaos dial** (footer) — 0 pauses all animation, 11 is a mistake.
  Respects `prefers-reduced-motion` regardless.
- **Flip cards** — the trophy case; click or Enter/Space to flip.
- **Journey map** — SVG level-select path that draws itself on scroll, with a
  quest log telling the career story.
- **Birthday mode** — every October 20 the avatar wears a party hat and
  confetti falls. Preview any day with `?birthday`.
- **Contact** — copy-to-clipboard email with confetti + toast, `mailto:` link.
- The pixel avatar is drawn at runtime onto a 24×31 grid from an ASCII map
  near the top of the script (easy to tweak pixel by pixel).

## Structure

```
index.html              the whole site
_archive/samples/       the original design prototypes (dark arcade variant,
                        toybox, gallery) — kept for reference, not deployed
```

## Known TODOs

- GitHub and LinkedIn links in the contact section are placeholders (`#`).
- OG image (`og:image`) not set — add a 1200×630 screenshot when deployed.
- The old Phaser-RPG experiment lives in `~/Developer/PersonalWebsite`
  (separate repo) and is not part of this site.

## Editing tips

- Copy lives in ordinary HTML; the roll palettes, greetings, trophy cards and
  journey stops are small arrays at the top of the `<script>` block.
- The avatar shirt color follows palette color #1 of each roll automatically.
- Local easter egg: the browser console has a message for snoops.
