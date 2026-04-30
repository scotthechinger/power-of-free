# Findings Overnight Rebuild — Punch List

**Done:** 2026-04-29 overnight session. All 8 findings rebuilt using the hybrid pattern (live HTML scaffold + per-finding SVG drop-ins). HTML parses 0 errors. All 57 asset paths resolve. Counts: 8 finding articles, 9 illustration blocks, 11 pull-quote blocks, 4 chart bars, all per-finding SVG cord and shape assets wired.

---

## What's verified working

- F1 chart toggle (Prisons / Jails) — swaps eyebrow text, both stat numbers (25↔27, 45↔57), the +pct callout (+80%↔+111%), AND the chart-shape SVG backings (different heights for prisons vs. jails — the visual reproportions correctly).
- F1 cord animation — orange cord stroke draws on via `getTotalLength()` when scrolled into view.
- F5 cord animation — same pattern, different path.
- All 8 findings have proper template colors (`tpl-plum`, `tpl-cream`, `tpl-lavender`) preserved.
- All canonical copy text preserved (eyebrows, headlines, body paragraphs, pull quotes, attributions). Em-dashes upgraded to `&mdash;` entities throughout.
- Sub-nav tabs still bind to finding IDs `#finding-01` through `#finding-08` so the existing scroll-position-based active tab tracking still works.

---

## Per-finding asset inventory

```
assets/illustrations/separated/finding-01/
├── illust-finding-01.svg              (figure)
├── illust-finding-01-bg.svg           (lavender bg block)
├── illust-finding-01-cord.svg         (orange cord — also inlined in HTML for animation)
├── chart-prisons-before.svg           (25 stat shape)
├── chart-prisons-after.svg            (45 stat shape)
├── chart-jails-before.svg             (27 stat shape)
├── chart-jails-after.svg              (57 stat shape)
├── pq-finding-01-shape.svg            (lavender pull-quote rounded card)
└── pq-finding-01-glyph.svg            (double-quote marks glyph)
+ photo-finding-01.jpg

assets/illustrations/separated/finding-02/
├── illust-finding-02.svg              (phone-with-hand)
├── illust-finding-02-bg.svg           (lavender bg block)
├── coin-finding-02-a.svg              (coin decoration)
├── coin-finding-02-b.svg              (coin decoration)
└── pq-finding-02-shape.svg
+ photo-finding-02.jpg

assets/illustrations/separated/finding-03/
├── illust-finding-03.svg              (clean — figures hugging)
├── pq-finding-03.svg                  (pull-quote shape)
├── stat-finding-03-a.svg              (placeholder, ~170 bytes)
└── stat-finding-03-b.svg              (placeholder, ~170 bytes)
+ photo-finding-03.jpg

assets/illustrations/separated/finding-04/
├── illust-finding-04-a.svg            (figure A from zip)
├── illust-finding-04-b.svg            (figure B from zip)
├── pq-finding-04-left.svg             (left pull-quote shape)
└── pq-finding-04-right.svg            (right pull-quote shape)
+ photo-finding-04.jpg

assets/illustrations/separated/finding-05/
├── illust-finding-05-figure-a.svg     (right figure — orange shirt with phone)
├── illust-finding-05-figure-b.svg     (left figure — green shirt holding phone)
├── illust-finding-05-bg.svg           (lavender bg)
├── illust-finding-05-cord.svg         (coral cord)
├── stat-finding-05-a.svg              (lime 77% stat shape)
└── stat-finding-05-b.svg              (coral 76% stat shape)
+ photo-finding-05.jpg

assets/illustrations/separated/finding-06/
├── illust-finding-06-a.svg            (figure A — phone)
├── illust-finding-06-b.svg            (figure B — bigger illustration)
└── illust-finding-06-bg.svg           (lavender bg block)
+ photo-finding-06.jpg
NOTE: F6 has no separated stat shapes — using flat color fills + live numbers.

assets/illustrations/separated/finding-07/
├── illust-finding-07.svg              (figures embracing)
├── stat-finding-07-a.svg              (pull-quote shape A)
└── stat-finding-07-b.svg              (pull-quote shape B)
+ photo-finding-07.jpg
NOTE: F7's two "Rectangle" SVGs are being used as pull-quote shape backings, not stat-block backings. F7 has no chart bars.

assets/illustrations/separated/finding-08/
├── illust-finding-08.svg              (figure)
├── illust-finding-08-decor.svg        (small decorative element)
├── illust-finding-08-cord.svg         (cord — not yet wired into animation)
├── illust-finding-08-shape-a.svg      (small shape — currently unused)
├── illust-finding-08-shape-b.svg      (small shape — currently unused)
├── stat-finding-08-a.svg              (plum pull-quote shape — used for first quote)
└── stat-finding-08-b.svg              (lime pull-quote shape — used for second quote)
+ photo-finding-08.jpg
NOTE: F8 has no chart bars. The two "stat" shapes function as pull-quote backings.

assets/findings/full-svg/
├── finding-01-prisons-full.svg        (reference)
├── finding-01-jails-full.svg          (reference)
├── finding-02-full.svg                (reference)
├── finding-04-full.svg                (reference; was 4B.svg)
├── finding-05-full.svg                (reference)
└── finding-06-full.svg                (reference)
NOTE: F3, F7, F8 no full-section SVG was uploaded — using the assets/findings/ PNGs as reference.
```

---

## Judgment calls / things to review

1. **F2 chart bars** — no SVG chart shape backings were provided for Finding 2's 70%/82% bars; falling back to flat coral + lavender fills with live HTML numbers. Visual is functional but won't have the notched-corner Figma chart shape look unless you export those.

2. **F3 stat shapes (`stat-finding-03-a.svg`, `stat-finding-03-b.svg`)** — only ~170 bytes each, looks like placeholder/empty exports from a previous chat. Currently F3's chart bars use flat lime + coral fills (not these placeholders). When you have proper exports, drop them in and switch the F3 chart bars to use them.

3. **F4 stat blocks** — F4 has no chart bars in the design; the middle row uses two pull-quote blocks side by side instead. Using `pq-finding-04-left.svg` and `pq-finding-04-right.svg` as backings for those.

4. **F5 cord position** — placed roughly between the two figures. The exact position is `top: 22%; right: 22%; width: 50%`. Adjust those three CSS values if it doesn't sit perfectly between the figures' phones at your viewport.

5. **F6 illustrations** — F6 had two illustration groups but no chart-shape SVGs. Top-right uses figure B + 100% stat overlay. Middle-left uses figure A on a lavender block. No chart bars (was no chart in the design either).

6. **F7 layout** — has only one illustration. Used as the top-right block. The two "Rectangle" SVGs were used as pull-quote backings for the two quotes (Saul and Jasmeel). No chart bars.

7. **F8 cord** — `illust-finding-08-cord.svg` was extracted but not yet wired into an animation. The cord exists at `assets/illustrations/separated/finding-08/illust-finding-08-cord.svg` if you want to add it visually somewhere. The JS already has `attachCordAnim('finding-08-cord', ...)` registered — just add an `id="finding-08-cord"` to an inlined SVG path within the F8 article whenever you want to wire it.

8. **F8 small shapes** — `illust-finding-08-shape-a.svg` and `illust-finding-08-shape-b.svg` are currently unused. They're small decorative shapes; not sure where they're meant to go in the design. Drop a Figma reference image into the project when you have time and I can place them.

---

## Files touched

- `index.html` — heavy edits to F1-F8 articles (CSS template added, JS toggle rewritten, cord-anim helper added). Also: hero card, methodology, quote block, action center, and findings intro all carried over from earlier in the session.
- `index.backup-2026-04-29-pre-findings-overnight.html` — backup before any finding changes.
- `assets/illustrations/separated/finding-{01-08}/` — full per-finding asset folders.
- `assets/findings-photos/photo-finding-{01-08}.jpg` — all 8 video thumbnails landed.
- `assets/findings/full-svg/` — full-section SVG references kept as fidelity backup; never wired into HTML.

---

## What's next (when you wake up)

1. Reload and walk through F1-F8 in viewport. Spot any obvious layout breaks — illustration positions, stat block colors, pull-quote shape coverage. Give me the punch list.
2. F1 chart toggle should still work — click "In Jails" and verify both stat numbers and chart shapes change.
3. F1 + F5 cord animations should fire as you scroll into them.
4. If anything looks really off in a specific finding, easiest fix is usually a small CSS tweak (height/position percentages on the illustration's inline-style overrides) or asset swap. I'll iterate as you call out specific issues.
