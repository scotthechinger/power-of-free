# Standalone Site — Pre-Demo Pass

**Date:** 2026-04-28
**Authoritative source:** `Copy of PowerOfFree_SiteCopy_WorthRises_FINAL - Edits 4_25.docx.txt` + Figma 28-April + assets in workspace
**Backup before edits:** `index.backup-2026-04-28-pre-rebuild.html` (107 KB)
**Current size:** `index.html` (~110 KB), 0 HTML parse errors, 0 unclosed tags

## Copy fixes against canonical doc

### About the Report
- "first effort to document" → "first to document"
- "connection expands" → "connection increases"

### Hero Video card
- "Watch what free phone communication" → "Watch what free communication"

### Quote section (rebuilt entirely)
- Reordered to Scott's spec: Michael, Saul, Felix, Angel, Tricia, Sgt. Mitchell, Shelene, Marc, Jasmeel, then Dwayne, Nia, Ransey
- All 9 quote photos self-hosted from `Photos for quote block/` → `assets/quotes/`. No more chiton-okra CDN refs in quote cards
- Jasmeel and Shelene now show their illustrations (were gradient placeholders)
- Bracketed words restored exactly per canonical: Dwayne `[hadn't]` `[Then]`, Tricia `[free]`, Sgt. Mitchell `[officers]`, Jasmeel `[free]`
- Long-form canonical quote text restored for: Felix Ali, Shelene Adams, Angel Rice, Sgt. Mitchell, Jasmeel
- Last names restored: "Felix" → "Felix Ali", "Shelene" → "Shelene Adams", "Angel" → "Angel Rice"
- Roles per canonical: "Wife, X" → "Spouse, X" for Angel + Nia; "Incarcerated, X" → "Incarcerated person, X"; "Formerly incarcerated, X" → "Formerly incarcerated person, X"

### Finding 1 — Increased Connection
- Body para 2: "bits and bobs of everyday life" → "life's ups and downs — all without a clock running"
- Quote attribution: "Commissioner Dan Marcoussidi III" → "Commissioner Dan Martuscello III"

### Finding 2 — Financial Relief
- Body: "$204 to $2,927" → "$244 to $2,927"
- Body: "Savings for families on loved ones" → "Savings for families with loved ones"
- Body: "share of these savings flowed back to communities" → "share of those savings flowed to the communities"
- Quote: "Brashari" → "Brashani"
- Quote: "down payment for our future" → "down payment for a mortgage"
- Quote attribution capitalization: "Wife of an Incarcerated Man" → "Wife of an incarcerated man"
- Video caption: "A weight lifted" → "A weight's been lifted"

### Finding 3 — Stronger Family & Community Relationships
- **Pull quote attribution: "Natavia, Formerly Incarcerated, Massachusetts" → "Hamza, Formerly incarcerated, Massachusetts"** (the one called out in handoff)
- Body: "financial stress" → "financial stressor"
- Body: "visiting relationships in reciprocity that showed support" → "rooting relationships in reciprocity that ensured support"
- Body: "Maintaining and even expanding, social ties is critical to" → "Maintaining, and even expanding, social ties is critical for"
- Top-right cropped finding PNG (was full-bleed PNG that included title; now no duplicate-title issue)
- Bottom-left video thumb now uses `assets/findings-photos/photo-finding-03.jpg` (Natavia portrait) as background; caption now `"Mutual support"`

### Finding 4 — Parenting & Child Development
- Lead: "with 19% of those children five years old or younger" → "with 18% of those children four years old or younger"
- Lead: "is one of the primary ways they continue to parent" → "is one of the primary ways they parent"
- Lead: "while separated. The high cost" → "while separated. But the high cost"
- "parent–child" (em-dash) → "parent-child" (hyphen) per canonical
- Video caption: "Raised my daughter over the phone" → `"I raised my daughter over the phone"` (with quotes)
- Top-right cropped finding PNG

### Finding 5 — Improved Mental & Physical Health
- Lead: "Those emotions erode" → "These emotions erode"
- Body: "rely on correctional officers to relieve medical attention" → "rely on correctional officers to receive medical attention"
- Video caption: `"Connection as medicine"` (added quotes per canonical)
- Top-right cropped finding PNG

### Finding 6 — Less Violence & Operational Disruption
- Lead: "change their day or their lives" → "change their day or their life"
- **Lead: garbled phrase "with especially-created broader environmental issues" replaced with full canonical sentence** "Ultimately, emotionally charged conversations were often cut short, leaving people to carry unresolved stress back into shared living spaces, which expectedly created broader environmental issues."
- Stat description: "tool that reduces tension" → "tool that reduced tensions"
- Body: "scarcity that drove that conflict" → "scarcity that drove conflict"
- Video caption: "Win-win on both sides" → `"If they're having a good day, we're having a good day"`
- Top-right cropped finding PNG

### Finding 7 — Rehabilitation
- Lead: "With that comes a sense of responsibility to the family — when people feel connected to those who care about them and can see truthful progress" → "This sense of identity and responsibility is motivating — when people feel connected to those who care about them and can see fruitful lives post incarceration"
- Quote: "[whom] they connect" → "[when] they connect"
- Quote: added missing "I can see excitement." sentence
- Body: "When access is constrained" → "When access is consistent"
- Body: "rehabilitation programs" → "rehabilitative programs"
- Video caption: `"Hope has a phone number"` (added quotes per canonical)
- Top-right cropped finding PNG

### Finding 8 — Reentry Planning & Success
- **Lead: garbled phrase "feeling cliffside-rates that the underwhelm public safety" replaced with canonical "feeding high recidivism rates that undermine public safety"**
- Body fully restructured to canonical 3-paragraph form (was 2 paragraphs with broken syntax)
- Video caption: `"The calls that come before freedom"` (added quotes per canonical)
- Top-right cropped finding PNG

### Take Action
- Card 2: "Find your representative →" → "Contact your representative →"

### About This Project / Methodology
- Lead paragraph rewritten per canonical: now includes "Since 2018, Worth Rises has led the national Connecting Families campaign aimed at making communication in prisons and jails free."
- Second paragraph rewritten per canonical: now includes the correctional staff acknowledgment
- Third paragraph rewritten per canonical: now includes the contributors thank-you

### Resources
- Names confirmed: "Report Fact Sheet" + "Implementation Fact Sheet" + "Ultimate Campaign Guide" (Scott's choice; canonical doc has "Report Flash Sheet" but Scott confirmed "Fact")

## Layout / structural changes

### Header swap (per Scott's note in handoff)
- Replaced full-height stretching coral CTA with standard rounded `.btn-coral`-style button (padding 11px 22px, border-radius 4px, hover translateY)
- Header inner now uses symmetric padding + max-width 1440px + center alignment
- `.brand` now uses `<img src="assets/illustrations/worth-rises-logo.svg">` with onerror fallback to triangle + text
  → drop the real logo SVG into `assets/illustrations/worth-rises-logo.svg` and refresh; fallback disappears automatically

### Findings 03–08 — duplicate title problem fixed
- Was: full Figma PNGs that included the title text → showed duplicated title alongside the live HTML title
- Now: cropped PNGs from `power of free:finding-pngs-new-2026-04-28/cropped/` placed under `assets/illustrations/finding-illust/cropped/`
- Files: finding-03/04/05/06/07/08 (all 6)

### Action Center — right-side mirrored handshake
- Was: only `.action-center-illust-left` visible
- Now: also `.action-center-illust-right` with `transform: scaleX(-1)` for mirrored handshake on the right (matches Figma)

### Pull-quote glyph
- Was: `❝` Unicode char in Georgia, opacity 0.85
- Now: `\201C` (`"`) in Concrette italic with Georgia fallback, opacity 0.95, larger size (64px → 96px clamp)

## Asset reorganization

### Self-hosted now
- All 9 quote photos: `Photos for quote block/` → `assets/quotes/quote-{angel,felix,jasmeel,marc,michael,mitchell,saul,shelene,tricia}.{jpg,png}`
- F3 photo: `Photos for findings/photo-finding-03.jpg` → `assets/findings-photos/photo-finding-03.jpg`
- 6 cropped finding PNGs → `assets/illustrations/finding-illust/cropped/`
- 4 F3 separated-elements SVGs (illust + 2 stat shapes + pull-quote shape) → `assets/illustrations/separated/finding-03/` (ready for future hybrid build, not wired in yet)

### Total local asset weight
- `assets/`: 71MB total (9.4MB quotes, 44MB illustrations including all the cropped PNGs)

## Verification

- HTML parse: 0 errors, 0 unclosed tags
- All `src="assets/..."` paths resolve locally (1 expected miss: `worth-rises-logo.svg` — fallback works)
- All `background-image:url('assets/...')` paths resolve locally
- 12 quote cards
- 90 fade-up + 16 slide-right + 13 scale-in + 12 slide-left + 12 counter + 11 bar-grow + 3 mask-wipe + 3 draw-path + 2 range-grow animation hooks

## Still pending (not blocking demo)

1. **Hero video poster** still references `https://chiton-okra.squarespace.com/s/Hero-Video-Landing-Image.png` — file not available locally. Drop a local copy into `assets/hero/Hero-Video-Landing-Image.png` and update the CSS rule, OR keep the CDN reference for the live version
2. **Worth Rises logo SVG** — fallback to triangle works for now. Drop `assets/illustrations/worth-rises-logo.svg` and the fallback disappears automatically
3. **About-the-Report illustration** — still uses placeholder geometric paper-rectangles SVG (`about-report-papers.svg`). No clear Figma frame yet identified; flag for the design pass
4. **F1 chart toggle (In Prisons / In Jails)** — when user clicks "In Jails", numbers swap (25→27, 45→57) but the "+80%" label is hardcoded for the prison case. For jails it should read "+111%". Minor JS fix
5. **F3 separated-elements hybrid layout** — assets are copied to `assets/illustrations/separated/finding-03/` but not yet wired into a new layout. Currently F3 still uses the cropped full-bleed PNG. The ideal pixel-perfect-with-animation pattern is still future work
6. **Mobile responsive testing** — breakpoints at 900px and 540px exist but haven't been tested at narrow widths
7. **Quote photos for Dwayne, Nia, Ransey** — still placeholder gradients. Real images haven't landed yet (canonical doc has annotations from rajaini@worthrises.org noting these are still pending high-res source material)

## Files touched

- `index.html` — heavily edited (textual fixes, quote rebuild, header swap, illustration refs)
- `index.backup-2026-04-28-pre-rebuild.html` — pre-edit backup, untouched
- `assets/quotes/` — 9 photos copied in
- `assets/findings-photos/photo-finding-03.jpg` — copied in
- `assets/illustrations/finding-illust/cropped/` — 9 cropped PNGs copied in
- `assets/illustrations/separated/finding-03/` — 4 SVGs copied in (for future hybrid build)
- `CHANGELOG-2026-04-28.md` — this file
