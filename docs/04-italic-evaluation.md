---
title: TG Málrómur Italic — evaluation
type: audit
status: active
updated: 2026-11-12
description: First look at the Italic, read against the Roman as it stands after its 2026-11-12 first pass. Covers the masters and axis, vertical metrics, the copied kerning, coverage and small caps.
aliases:
  - tg-malromur-italic-evaluation
tags:
  - project/kol-foundry
  - domain/typography
sources:
  - typefaces/tg-malromur/glyphs/TGMalromur-Italic.glyphspackage
related:
  - "[[05-italic-plan|Italic plan]]"
  - "[[01-evaluation|Roman evaluation]]"
---

# TG Málrómur Italic — evaluation

## 2026-11-12 — first look

Read live through the Glyphs MCP; nothing in the font was changed. Saved today as `TGMalromur-Italic.glyphspackage`; the old `TG Malromur Italic.glyphs` is in `_tmp/2026-11-12-malromur-italic-glyphs/`.

**Font:** variable, axes `wght` 300–900 and `ital` (both masters at 1). Two masters, Light Italic `m01` and Black Italic `m002`, fully compatible. UPM 2048, cap height 1280, x-height 920, ascender 1384, descender −400, italic angle 16°. 277 glyphs, 214 exporting, 142 encoded. Features: `aalt ccmp ordn lnum pnum tnum onum c2sc smcp case dlig liga ss01 ss02 ss03` (all automatic). One variable instance (`Variable Font Origin` = Light) and seven statics.

| Area | Italic now | Roman after its first pass |
|---|---|---|
| Masters | Light, Black | Light, Regular (internal 366), Black |
| Instances (internal) | 300 · 400 · 475 · 550 · 650 · 750 · 900 | 300 · 366 · 444 · 534 · 639 · 759 · 900 |
| Axis Location | external value = internal, so CSS 500–800 miss their designs; VF opens at Light | 300–900, default Regular 400 |
| Win metrics | 1510 / 400; Ö Black reaches 1675, J.ss01 Black −421 | 1680 / 490 |
| Kerning | 1532 pairs (Light), 1550 (Black); taken to be the Playfair copy, as in the Roman | own, measured |
| Spacing | metrics-keyed (176 glyphs) | same, Black sidebearings recalculated |
| Coverage | ≈70 Windows-1252 characters short | Win-1252 complete |
| Small caps | `.smcp` figures only | `a.sc`…, 60 glyphs, `smcp` + `c2sc` |

**Missing against the Roman:** `+ < = > ^ \` | ~`, ¤ ¦ ¨ ª ¬ soft hyphen ¯ ± ² ³ ´ µ ¶ ¸ ¹ º ¼ ½ ¾ × ÷ ƒ ˆ ˜ † ‡ ‰, À Â Ã Ä Å Ç È Ê Ë Ì Î Ï Ñ Ò Ô Õ Ø Ù Û Ü Œ Š Ÿ Ž and their lowercase, the combining grave, circumflex, tilde, macron, ring, caron and cedilla.

**Glyph colours:** 35 red, 39 yellow, 6 blue, 13 grey, 4 orange-red, 2 orange. The red tags are read the same way as in the Roman, against Light and Black, in the plan's W2.
