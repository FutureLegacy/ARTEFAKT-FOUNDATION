# Artefakt Foundation — Site Build (April 2026)

Six-page site, shared identity system, built to the Bauhaus-inspired
spec in the handoff. Photograph leads. Type carries hierarchy.
Nothing decorative.

## Files in this build

```
artefakt-foundation/
├── index.html       Homepage — 6 panels (masthead + 4 pillars + colophon)
├── witness.html     Pillar 01 — 13-plate documentary gallery + colophon
├── connect.html     Pillar 02 — Fellowship, Academy, fieldwork, youth
├── legacy.html      Pillar 03 — Archive (formerly Preserve, public name is Legacy)
├── sustain.html     Pillar 04 — Materials reuse funding model
├── about.html       Founder, organization, board, contact
└── styles.css       Shared identity stylesheet — single source of truth
```

## Design system (locked)

| Element | Value |
|---|---|
| Paper | `#f4f1ea` |
| Ink | `#0c0b09` |
| Red (splice + single pillar accent per page) | `#c8522a` |
| Dust (rules, separators) | `#c4bfb4` |
| Graphite (secondary text) | `#6b6760` |
| Headlines | Playfair Display 400, italic for emphasis |
| Body | IBM Plex Sans 300/400 |
| Meta / labels / captions | IBM Plex Mono 400, uppercase, tracked 0.14em |
| Nav height | 72px (60px mobile) |
| Meta footer height | 36px (32px mobile) |
| Scroll behavior | scroll-snap y mandatory, 100vh panels |
| Nav color | mix-blend-mode: difference (adapts to panel under it) |
| Red splice in wordmark | `mix-blend-mode: normal` override so it stays red |

## Image manifest — what to place in `/images/`

### index.html (4 hero frames — pick strongest single image per pillar)
- `home-witness.jpg` — suggest: a strong Chicago South Side frame
- `home-connect.jpg` — suggest: Zurich workshop master image
- `home-legacy.jpg` — suggest: tent city wide frame or Calgary construction
- `home-sustain.jpg` — suggest: red dress on gravel (strongest object-as-witness frame)

### witness.html (13 plates)
- `witness-01.jpg` through `witness-13.jpg`
- Captions in HTML set placeholder locations/years — **update these in the file to match the actual images before launch**

### connect.html (4 frames)
- `zurich-workshop-01.jpg`
- `zurich-workshop-02.jpg`
- `canada-project-river.jpg`
- `lincoln-challenge.jpg`

### legacy.html (5 frames)
- `tent-city-01.jpg`
- `tent-city-02.jpg`
- `apples-in-snow.jpg`
- `calgary-construction.jpg`
- `north-korea.jpg`

### sustain.html (4 frames)
- `red-dress-gravel.jpg`
- `pink-handcuffs.jpg`
- `pink-shoes.jpg`
- `taco-stand.jpg`

### about.html (2 frames)
- `chicago-hat-figure.jpg`
- `ted-stage.jpg`

## Deploy

```bash
# Move the built files into the repo
cp artefakt-foundation/*.html ~/ARTEFAKT-FOUNDATION/
cp artefakt-foundation/styles.css ~/ARTEFAKT-FOUNDATION/

# Place images
mkdir -p ~/ARTEFAKT-FOUNDATION/images
# ... copy the JPG files listed above into /images/ ...

# Deploy
cd ~/ARTEFAKT-FOUNDATION
git add .
git commit -m "Full site build: all 4 pillars + about, shared identity system"
git push
vercel --prod
```

## Things to confirm / update before launch

1. **Witness plate captions** — the 13 plates use placeholder locations/years (e.g. "Chicago · South Side · 2019"). Update each to match the actual photograph.
2. **About panel images** — `chicago-hat-figure.jpg` and `ted-stage.jpg` are the only two photos on the About page. If you want more presence of place (Calgary, South Shore co-op, Monterey Ave gallery), add panels.
3. **Board list on About** — currently lists David Christenson, Angela Boehm, Shovik Sengupta, with a note about additional members. Update when the founding five is complete.
4. **Bio credentials** — the credential list on About mentions Alicia Patterson, Aaron Siskind, Open Society, World Press Photo. Confirm these are accurate for Jon's record; remove anything he'd prefer not listed.
5. **Contact address** — About page shows 4525 Monterey Ave NW. Confirm that's the public address you want listed now, or keep it off until the gallery is open.
6. **Treaty 7 acknowledgment** — appears in the Calgary meta footer on every page. Confirm phrasing is how Jon wants it stated.

## Known constraints (by design)

- **No images in repo yet for this build.** I wrote the HTML to reference
  files by descriptive name (e.g. `images/zurich-workshop-01.jpg`) so you
  can drop actual photographs into `/images/` and the site resolves. If
  your existing `artefakt-fullscreen.html` uses base64-embedded images,
  these pages do not — they expect real image files. This is intentional:
  base64 bloats HTML, breaks caching, and makes image swaps painful.
- **No JavaScript.** Every page is pure HTML + CSS. Scroll-snap is native.
  Nav blend mode is native. The only "interaction" is hover underlines
  and scroll.
- **About page has scrollable text panels.** The bio and organization
  panels are taller than 100vh and override the scroll-snap locally so
  long-form reading works. This is deliberate.

## Identity rules — for future edits / VA / Ophelia

- **Photograph always leads.** If a design decision makes the image
  smaller or competes with it, undo the decision.
- **Red only two places per page.** The wordmark splice, and one pillar
  code marker. Never a third use.
- **No gradients, no shadows, no filters on photographs.** If any of
  these appear in a future edit, flag and revert.
- **Two typefaces only.** Playfair Display + IBM Plex. If a third
  appears, remove it.
- **Studio and Foundation stay separate.** Do not merge navigation,
  color, or social links. The "Studio →" link in nav is the only
  crossover, and it's clearly offsite.

---

Built April 2026. Alma — Artefakt Visual Design Director.
