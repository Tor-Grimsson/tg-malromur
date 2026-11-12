---
title: TG Málrómur Italic — plan
type: plan
status: draft
updated: 2026-11-12
description: The Roman's seven workstreams run on the Italic, so the two styles match in weights, metrics, kerning method, coverage and small caps.
aliases:
  - tg-malromur-italic-plan
tags:
  - project/kol-foundry
  - domain/typography
phases:
  - W1 VF standards
  - W2 spacing
  - W3 kerning
  - W4 punctuation and ASCII
  - W5 Western European letters
  - W6 vertical metrics and loose ends
  - W7 small caps
related:
  - "[[04-italic-evaluation|Italic evaluation]]"
  - "[[02-plan|Roman plan]]"
---

# Plan — TG Málrómur Italic

**Raised:** 2026-11-12, from [[04-italic-evaluation|the Italic evaluation]]. Agreed 2026-11-12 (*"ok"*): the Roman's plan, step for step.
**Status:** W1 built and saved 2026-11-12. W2.1, W3, W4, W5 and W6 built 2026-11-12, unsaved. W2.2 built 2026-11-12, unsaved: Regular/Black of `# £ ¥ * ‹` and the hyphen from his Light outlines (`#` stroke by stroke; `› « »` follow as components; light blue; proof `italic_w22b.png`). W7 small caps built 2026-11-12, unsaved: RMX 82 % / 75 % / weight 0, −12, −96 from source (stems 136 / 154 / 304 on `n`, height 960, first run), renamed `a.sc`…, anchors placed along the 16° slant, 29 accented as components, `smcp` 72 / `c2sc` 70. Exported and collected 2026-11-12: `export/TGMalromurItalicVF.ttf` + WOFF2, 372 glyphs, `fvar` 300/400/900, Italic proofs in `specimen/tg-malromur-italic-*`. Two export blockers fixed on the way: the middle arm of `e.sc`/`f.sc` ended exactly on the stem edge, so the overlap merge differed per master (arm end moved 25 units into the stem, all masters); `v.sc` carried the production name `V` (cleared). Open: small-cap kerning, ẞ.sc.

**Built, 2026-11-12 (unsaved):**
- W2.1 Black/Regular sidebearings of H O n o from Light's ratio (H 64→54, O 88→76, o 64→56 in Black); 500 keyed layers re-synced.
- W3 copied kerning (Light 1532, Black 1550 pairs) saved to `_tmp/2026-11-12-italic-kerning-removed.json` and cleared; the Roman's kerning groups applied (217 glyphs); measured class kerning, Light 1289 · Regular 1287 · Black 1278 pairs (A·V −80/−116, L·T −156/−144). Proof `_tmp/2026-11-12-first-pass-renders/italic_w33.png`.
- W4/W5 the Roman's builds: Windows-1252 complete, 311 exporting glyphs, all compatible. Grave/circumflex/caron from his acutes; quote widened from Light; serif pilcrow built upright then slanted 16°; Œ œ from O+E, o+e. ƒ is the italic f itself (it already descends). Proof `italic_w45.png`.
- W6 win 1680/490 (same as the Roman; tallest Ä 1675, deepest J.ss01 −421); `Decompose Glyphs` 61; test VF export clean (312 glyphs, `fvar` 300/400/900).
**Shape:** W › phase › list.
**Laws carried:** as the [[02-plan|Roman plan]]. Work goes through the Glyphs MCP on `glyphs/TGMalromur-Italic.glyphspackage`, nothing is saved without his word, kerning is measured from the outlines, his drawings are never replaced, and every outline change is rendered before it is shown.
**How a phase closes:** as the Roman — a measurable acceptance line, read back through the MCP or from the exported font with fontTools, then his look in Glyphs.

---

## W1 — VF standards — ✅ built 2026-11-12 (unsaved)

Test export: `fvar` 300/400/900, default "Italic" (400), seven instances at 300…900, 215 glyphs. The Regular Italic master is interpolated from Light and Black (`_tmp/2026-11-12-first-pass-scripts/italic_w1.py`); every glyph's decomposed outline sits within 9 units of the straight Light–Black line. Two things the copy has to carry, found on the way: the corner/cap serif components (stored as hints, in a different order in Light and Black, so they are copied, not paired) and every in-between and smart-pole layer, matched by name. The untouched Italic didn't export as a variable font either (*"Intermediate layers in E"*); the `Decompose Glyphs` list (41 glyphs) fixes that, as in the Roman.

### 1.1 — Weights matched to the Roman
- Instances move to the Roman's internal positions: 300 / 366 / 444 / 534 / 639 / 759 / 900.
- **Acceptance:** each Italic instance's internal weight equals the Roman instance of the same name.

### 1.2 — Regular master
- A Regular Italic master at internal 366, built by interpolating Light and Black (as the Roman's was), with smart-component layers for it. `Variable Font Origin` moves to it.
- **Acceptance:** three compatible masters; the exported VF's `fvar` default is 400.

### 1.3 — Axis Location, the Glyphs 4 way
- External axis values on every master and instance: 300 / 400 / 500 / 600 / 700 / 800 / 900. The old `Axis Location` custom parameter is not used: Glyphs 4 ignores it (found on the Roman, 2026-11-12).
- **Acceptance:** the exported VF's `fvar` is 300/400/900 and its seven named instances sit at 300…900.

## W2 — Spacing
- 2.1 Black sidebearings from Light's counter-to-space ratio, as the Roman.
- 2.2 Red-tagged glyphs that don't scale get Black drawings, by the Roman's ruling (`( ) { } [ ] / \ ® ™` stay light).
- **Acceptance:** as the Roman's 2.1 and 2.3.

## W3 — Kerning
- 3.1 The copied pairs are saved to `_tmp/` and cleared. 3.2 Groups as the Roman. 3.3 Pairs measured from the outlines, all masters.
- **Acceptance:** as the Roman's W3.

## W4 — Punctuation and ASCII
- The list in the evaluation, built from the Italic's own parts; rough-ins light blue.
- **Acceptance:** each glyph exists with its Unicode value in all masters.

## W5 — Western European letters
- The combining marks (grave, circumflex and caron from his acutes, as the Roman) and the accented letters as components; Ø ø Œ œ built from his O o E e, as the Roman's.
- **Acceptance:** every Windows-1252 letter has a glyph with its Unicode value.

## W6 — Vertical metrics and loose ends
- Win metrics to the real extremes; tester and scratch glyphs off.
- **Acceptance:** no exporting glyph goes beyond `winAscent` / `winDescent`.

## W7 — Small caps
- RMX Scaler, together, with the Roman's numbers (Width 82 %, Height 75 %, Weight measured to land on `n`), named `a.sc`… so Glyphs writes `smcp` and `c2sc`. Accented small caps as components.
- **Acceptance:** small-cap height 960, stems on `n`'s weight ±2, `smcp` and `c2sc` compile.
