# Power of Free — Standalone Backup Site

A self-contained, non-Squarespace version of the Critical Connection / Power of Free
microsite. Built so that if Squarespace ever blocks us, breaks, or just becomes too
constrained for the animations we want, we have a fallback we control end-to-end.

## What's in this folder

```
standalone-site/
├── index.html              ← the entire site (HTML + CSS + JS, single file)
├── README.md               ← this file
└── assets/
    ├── findings/           ← 8 PNG charts (the same ones uploaded to SQS)
    └── illustrations/      ← Figma SVG exports + a few unused extras
```

The whole site is **one HTML file** (~84 KB) plus images. There's no build step,
no framework, no dependencies. Open `index.html` in any browser and it just works.

## How to host it

Drag-and-drop options (easiest):

- **Netlify Drop** — drag the `standalone-site` folder onto https://app.netlify.com/drop
  and Netlify gives you a public URL within seconds. Free.
- **GitHub Pages** — commit the folder to a repo, enable Pages on the branch, done.
- **AWS S3 + static hosting** — upload the folder to a bucket configured for static
  website hosting. Pennies per month.
- **Vercel / Cloudflare Pages** — same drag-and-drop flow.

Wire-into-Squarespace option:

- Squarespace can embed an external page in an iframe via Code Block.
- Cleaner option: link to the standalone site as a separate URL from the SQS nav, so the
  client's main domain still goes to SQS but the actual report page is the standalone.

## How animations work

There's one animation system: each animatable element has a `data-anim` attribute.
On scroll, an IntersectionObserver adds `.is-in` to the element when it enters the
viewport, which triggers a CSS transition to the resting state.

Available primitives:

| Primitive    | What it does                              | Use on                |
|--------------|-------------------------------------------|-----------------------|
| `fade-up`    | Opacity 0→1, translateY(40px → 0)         | Headlines, paragraphs |
| `slide-left` | Slides in from the right                  | Stat cards, charts    |
| `slide-right`| Slides in from the left                   | Pull quotes           |
| `scale-in`   | Grows from 94% to 100%                    | Illustrations, logos  |
| `mask-wipe`  | Left-to-right reveal via clip-path        | Banners, images       |
| `bar-grow`   | scaleY(0 → 1) from bottom                 | Vertical bar charts   |
| `range-grow` | scaleX(0 → 1) from left                   | Horizontal range bars |
| `counter`    | Number rolls up from 0 to its final value | Big stat numbers      |
| `draw-path`  | SVG stroke-dashoffset draws on            | SVG path lines (cord) |

### Modifiers

```html
<div data-anim="fade-up" data-anim-delay="200">     <!-- 200ms delay -->
<div data-anim="fade-up" data-anim-duration="1500"> <!-- override default 900ms -->

<!-- Counter requires extra attributes -->
<span data-anim="counter"
      data-counter-end="622.5"
      data-counter-prefix="$"
      data-counter-suffix="M"
      data-counter-decimals="1">$622.5M</span>

<span data-anim="counter"
      data-counter-end="330000"
      data-counter-suffix="+"
      data-counter-format="comma">330,000+</span>
```

### Reduced motion

Anything with `[data-anim]` is automatically disabled for users who have set
`prefers-reduced-motion: reduce` in their OS. No extra work needed.

## How to ask for animations / changes

The site is built so most visual tweaks are one-line changes. Examples of what to
say to make changes happen quickly:

- "Make the $622.5M counter take 3 seconds." → I update one `data-anim-duration`.
- "Slide the Brashari quote in from below instead of from the right." → I change
  one `data-anim` value from `slide-right` to `fade-up`.
- "Stagger the three Take Action cards 250ms apart." → I update three
  `data-anim-delay` values.
- "Add a 'flip' primitive that rotates a card 90° to upright as it enters." → I
  add a CSS keyframe + a `[data-anim="flip"]` rule. Then any element with
  `data-anim="flip"` flips on scroll.

## Site architecture

The page renders these sections in order, each one anchored:

1. **Header** — sticky white nav bar, brand mark left, primary nav + Read-the-Report CTA
2. **Hero** (`#top`) — "The *Power* of Free" with animated coral cord behind
3. **About the Report** (`#aboutreport`) — deep-plum / soft-lavender split with coral circle CTA
4. **Hero Video** (`#hero-video`) — Vimeo embed (ID 1186772181), poster + close button
5. **Quotes** — 12-card carousel
6. **Findings Intro** (`#findings`) — "8 Areas of *Measurable* Impact" with three-figure illustration
7. **Findings 01–08** — each rebuilt to match the current Figma design:
   - **01 INCREASED *Connection*** (deep plum) — 6.4 BILLION feature block + Prisons/Jails chart toggle + 25/45 stat pair + "LOVE WITHOUT LIMITS" subhead + video + pull quote
   - **02 FINANCIAL *Relief*** (cream) — $622 MIL feature block + 70%/82% stat pair + "GROCERIES, RENT, AND ROOM TO BREATHE" subhead + green pull quote
   - **03 STRONGER FAMILY & COMMUNITY *Relationships*** (deep plum) — hugging illustration + 82%/93% stat pair + "SUPPORT, BOTH WAYS" + lavender pull quote
   - **04 PARENTING & CHILD *Development*** (lavender) — mother-and-child illustration + plum pull quote + "FOR THE NEXT GENERATION" + coral pull quote
   - **05 IMPROVED MENTAL & PHYSICAL *Health*** (deep plum) — hand-and-cord illustration + 77%/76% stat pair + "HOPE IS ON THE LINE" + lavender pull quote
   - **06 LESS VIOLENCE & *Operational Disruption*** (cream) — 100% lavender feature block + person illustration + "CALMER AND SAFER FACILITIES" + coral pull quote
   - **07 REHABILITATION** (deep plum) — two-figures illustration + coral pull quote + "STAYING ON TRACK" + lavender pull quote
   - **08 REENTRY PLANNING & *Success*** (lavender) — hand-with-pen illustration + plum pull quote + "SAFER COMMUNITIES" + lime pull quote
8. **Sub-nav** — sticky bottom strip, click-to-jump + active-tab tracking
9. **Action Center** (`#actions`) — "COMMUNICATION IS A *Lifeline*" with handshake illustration
10. **Take Action** — 3-card grid (Read & Share / Contact Legislators / Support Movement)
11. **Resources** — 3-card grid (Report Fact Sheet / Implementation Fact Sheet / Ultimate Campaign Guide)
12. **About This Project** (`#aboutproject`) — hugging-grandma illustration + Worth Rises + campaign CTAs
13. **Footer** — Worth Rises mark, link columns, copyright

### Design language used in the findings

- **Title** — three or four short uppercase lines, the last word an italic Concrette accent
  (e.g. `INCREASED` `Connection`). The `<em>` inside `.finding-title` triggers the swap.
- **Featured top-right block** — either a giant colored stat (6.4 BILLION, $622 MIL, 100%)
  or a full-bleed PNG illustration. Both have a diagonal corner-cut (`notch-bl` / `notch-tr` class).
- **Stat pair** — two side-by-side `.stat-block` blocks with notches, big numbers, small label.
- **Subhead** — `.f-subhead`, large uppercase headline introducing the body copy.
- **Pull quote block** — `.pq-block`, colored panel with a quote-mark glyph in the top-left
  corner and a notch on the top-right.
- **Video thumb** — `.video-thumb-block`, 4:5 image with play button center and coral caption ribbon.

## Asset inventory

### Bundled (in this folder)

- 8 finding PNGs in `assets/findings/` — the same baked images used in SQS.
  **Currently unused** because the standalone site rebuilds findings as live
  HTML/CSS/SVG (so they're animatable). Kept here as a fallback in case we
  ever want to swap a finding back to the baked PNG version. ~16 MB total.
  If you want to slim down the folder before deploying, delete this directory.
- ~17 SVG illustrations in `assets/illustrations/` — your fresh Figma exports.
  Currently using:
  - `about-report-papers.svg` — about-the-report illustration
  - `findings-intro-figures.svg` — three-figure illustration on findings intro
  - `methodology-frame.svg` — about-this-project illustration
  - `hero-cord.svg` — original Figma cord curve, inlined into the HTML
- The rest of the SVGs (`figure-1.svg` through `figure-6.svg`, `old-woman.svg`,
  `illustration-b/c/d/e.svg`, etc.) are available but not yet placed. Tell me
  where they belong and I'll wire them in.

### Pulled from Squarespace CDN (still hosted on chiton-okra.squarespace.com)

These are referenced by absolute URL because I couldn't download them from inside
my sandbox. They work as long as Squarespace's static CDN is up (which is
independent of whether the chiton-okra site itself is configured correctly):

- `Hero-Video-Landing-Image.png` (hero video poster)
- `quote-michael.jpg`, `quote-saul.png`, `quote-felix.jpg`, `quote-angel.jpg`,
  `quote-tricia.png`, `quote-mitchell.jpg` (6 quote photos)
- ConcretteXL-MediumItalic font (woff2 + woff)

To make the site **fully self-hosted**: download those files from the SQS CDN
(I have the exact URLs in `index.html` — search for `static1.squarespace.com`
and `chiton-okra.squarespace.com`), drop them in `assets/hero/` and
`assets/quotes/` and `assets/fonts/` respectively, and replace those URLs in
`index.html` with the local paths. ~10 minute task.

## Things that are different from Squarespace

- **Findings are LIVE HTML, not baked PNGs.** This is the point. Every bar,
  number, range, pull quote, and stat is its own DOM element. Animation = trivial.
- **Sub-nav uses live HTML/CSS sticky positioning** instead of a custom JS
  bar (no script hacks needed).
- **Hero cord is one SVG path** with `data-anim="draw-path"` — it draws on as the
  hero enters the viewport. No JS needed beyond the IntersectionObserver.
- **Finding 01 chart toggle (Prisons / Jails) actually swaps real data** instead
  of swapping image files. Click "In Jails" and the bar heights + numbers update
  with smooth CSS transitions.
- **Concrette XL** is loaded from the SQS CDN (woff2 + woff). Used for italic
  accent words (`Power`, `everything`, `Measurable`, `lifeline`, `Connecting Families`).

## Things that are intentionally NOT here yet

- Real photos for the 6 quotes that have placeholders (Dwayne, Nia, Shelene,
  Marc, Ransey, Jasmeel). Currently shown as colored gradients per Scott's call.
- The `finding-01-increased-connection-jails.png` PNG is irrelevant here — we're
  using live HTML for the chart, so the toggle just swaps numbers, not images.
- The Worth Rises logo. Currently a triangle character `▲` placeholder.
  Drop the real logo SVG into `assets/illustrations/worth-rises-logo.svg` and
  I'll wire it into the header + footer.

## Known gotchas

- The Vimeo iframe pre-load is deferred (`data-src` not `src`) — the video doesn't
  load until the user clicks play. This is intentional for performance.
- The hero cord SVG uses `pathLength="1"` so the `stroke-dashoffset` animation
  works regardless of actual path length. If you replace the cord, keep that
  attribute or recompute the dasharray.
- The quote carousel auto-advances every 5.5 seconds. Hover to pause.
- Sub-nav highlights the most-centered finding via IntersectionObserver. If you
  add more findings or change the threshold, update the threshold values in the
  `<script>` at the bottom.
