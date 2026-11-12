---
title: TG Málrómur Roman — evaluation
type: audit
status: active
updated: 2026-11-12
description: First look at the Roman since May 2026. Covers variable-font standards, vertical metrics, sidebearings, the copied kerning, coverage and what is missing for Western European.
aliases:
  - tg-malromur-evaluation
tags:
  - project/kol-foundry
  - domain/typography
sources:
  - typefaces/tg-malromur/glyphs/TGMalromur-Roman.glyphspackage
related:
  - "[[02-plan|plan]]"
  - "[[04-italic-evaluation|Italic evaluation]]"
---

# TG Málrómur Roman — evaluation

## 2026-11-12 — first look since May 2026

Read live through the Glyphs MCP. Nothing in the font was changed. The Roman was saved today as `TGMalromur-Roman.glyphspackage`, and the old `TG Malromur Roman.glyphs` is in `_tmp/2026-11-12-malromur-roman-glyphs/`. The Italic (`TG Malromur Italic.glyphs`) is still a single file and gets its own pass after the Roman.

**Font:** variable, wght 300–900, two masters (Light Upright `m01`, Black Upright `m002`). UPM 2048. Cap height 1280, x-height 920, ascender 1384, descender −400, italic angle 0. 239 glyphs, 197 of them exporting (the rest are `_` component parts, `A.smcp`, `t_h.smcp`, `s.dollar` and `tail.Q`), and 142 of them encoded. The two masters are fully compatible (paths, components and anchors match). Features: `aalt ccmp ordn lnum pnum tnum onum c2sc smcp case dlig liga ss01 ss02` (all automatic). Instances: one variable (`TGMalromurRomanVF`) and seven statics, Light to Black. Last export: `export/TGMalromurRomanVF.ttf`, 2026-05-26. That is also the file in `tg-collection/tg-malromur/`.

### 1. Where it stands

It's a working Latin basic + Icelandic Didone: A–Z, a–z, Á É Í Ó Ö Ú Ý Ð Þ Æ and lowercase, ß, four figure sets (proportional, tabular, old-style, small-cap), core punctuation, 15 ligatures, and stylistic sets for `a g` (ss01) and `J &` (ss02). Its spacing is keyed throughout. But its kerning was copied from Playfair, the variable font breaks the foundry standard, and the vertical metrics clip.

### 2. Variable-font standards (ARCHITECTURE §6)

These are the same faults Gullhamrar had, and the fix is the same.

| Fault | Now | Needs |
|---|---|---|
| Default style | `Variable Font Origin = m01`, so the VF opens at Light 300 | Regular 400 as the default |
| Instance positions | Medium 475, SemiBold 550, Bold 650, ExtraBold 750 on the axis | `Axis Location` so CSS 500/600/700/800 land on those designs |
| Axis Location | none on masters or instances | on every master and instance |

### 3. Vertical metrics

Typo and hhea are 1510 / −400 / gap 100, win is 1510 / 400, and Use Typo Metrics is on.

- **Accented capitals clip.** The tallest glyph is Ö Black at 1675, and Ý Light reaches 1628, but `winAscent` is 1510. Windows cuts everything above it. The Western European capitals (Â Ê Å…) will reach higher still.
- **`f_j` clips too.** It goes down to −484, but `winDescent` is 400.
- The win values have to cover the real extremes once W5 is done. Typo and hhea can keep their line spacing.

### 4. Sidebearings

The font is spaced with metrics keys (175 of 197 exporting glyphs carry one: `=64` on H, `n`/`o` on b d p q, `=|` on the tabular figures). LSB / RSB:

| Glyph | Light | Black |
|---|---|---|
| H | 64 / 64 | 64 / 64 |
| O | 84 / 84 | 84 / 84 |
| E | 64 / 96 | 64 / 96 |
| A | −24 / 16 | −24 / 16 |
| T | 52 / 52 | 52 / 52 |
| n | 48 / 48 | 48 / 48 |
| o | 92 / 92 | 92 / 92 |
| a | 64 / 32 | 64 / 32 |
| e | 92 / 80 | 92 / 80 |
| v | 0 / 0 | 0 / 0 |

- **147 of 197 glyphs have the same sidebearings in Light and Black.** Black is likely to set tight, as Gullhamrar's did. Proof it before deciding.
- **Rounds get more space than straights, in caps and lowercase alike:** O 84 vs H 64, and o 92 vs n 48. In a Didone that is normal: Playfair and Didot do the same (checked 2026-11-12, see [[03-first-pass|first pass]] § W2).
- The figures are consistent. Tabular figures are keyed to `zero.tf`, 1000 / 1200 wide.

### 5. Kerning

- **The kerning was copied from Playfair** (May 2026, `kol-steal-kerning.py`, scaled ×1.76). That makes 1572 pairs in Light and 1576 in Black. About 990 of them are glyph exceptions rather than group pairs. ARCHITECTURE §7 says this has to be replaced by kerning measured from Málrómur's own outlines.
- 8 pairs exist in only one master, for example `y·v` (Light only) and `H·o`, `a·y`, `o·v`, `r·f`, `y·o` (Black only).
- The letter groups are sound, and the accented letters follow their base (Á→A, É→H/E, Ö→O…).
- **Groupless:** ß and ẞ, all 15 ligatures, the tabular figures, and nearly all punctuation (comma, colon, quotes, guillemets, dashes, brackets, slash…).

### 6. Missing

**ASCII (8):** `+ < = > ^ \` | ~`.

**Western European letters (52):** À Â Ã Ä Å Ç È Ê Ë Ì Î Ï Ñ Ò Ô Õ Ø Ù Û Ü Š Ž Ÿ Œ, plus their lowercase and ÿ. The only marks in the font are `acutecomb`, `dieresiscomb`, `dotaccentcomb` and `strokeshortcomb` (with `.case` versions). Grave, circumflex, tilde, ring, cedilla, caron and macron need drawing as marks. After that the rest compose. Ø ø Œ œ need drawing.

**Punctuation and symbols:** nbspace, softhyphen, spacing accents `´ ¨ ¸ ¯ ˆ ˜`, `¶ † ‡ ‰ ƒ × ÷ ± ¬ ¦ ¤ µ`, ordinals `ª º`, superiors `¹ ² ³`, fractions `¼ ½ ¾`. `ordn` is on, but there are no ordinals for it to substitute.

### 7. Harmony and loose ends

- **Dashes:** the hyphen is 64 thick and 360 wide in **both** masters, so it doesn't gain weight towards Black. The en dash is 35 → 43 thick and the em dash 32 → 40, so they are thinner than the hyphen and share only its top edge (488). All three should share one weight and height that follow the masters.
- **Small caps:** `smcp` and `c2sc` are on, but only the small-cap figures and `t_h.smcp` exist (`A.smcp` doesn't export). The May decision was that small caps are out of v1. Either the features come off, or they stay as figure-only.
- **Ligatures:** `f_f f_f_i f_f_l f_i f_l` are drawn outlines, and their sidebearings are keyed to `f`, `i` and `l`, so spacing changes follow. `o_o` and `c_t` use components.
- `tester` exports. It's a scratch glyph built from parts and should not ship.
- 29 glyphs are tagged red. Red means **they don't scale** (his words, 2026-11-12). 24 of them are identical in Light and Black: `hyphen * # / \ ( ) { } [ ] « » ‹ › " ' ® ™ £ ¥`. The en dash, em dash and underscore scale only slightly, and ı ȷ do scale.
- **Weight steps are uneven.** H stems at the seven instances are 144 · 177 · 202 · 227 · 261 · 294 · 344, so the steps are +33 +25 +25 +34 +33 +50. Hairlines stay at 32–36 throughout.
- Font metadata has designer "Tór Grímsson" and URL `kolkrabbi.io`, but no copyright, license or manufacturer. Dylgjur's and Gullhamrar's placeholders apply.

### 8. Suggested order

1. **Standards (§6):** a Regular master, Variable Font Origin set to Regular, and Axis Location on masters and instances.
2. **Spacing:** decide the Black sidebearings and the cap round/straight relation against proofs, and fix the dashes.
3. **Kerning:** clear the copied kerning, group the punctuation, then measure pairs in all masters together.
4. **Punctuation and ASCII:** the 8 missing ASCII, nbspace and softhyphen, spacing accents and symbols.
5. **Western European:** the missing marks, the composable letters, and Ø ø Œ œ drawn.
6. **Vertical metrics, small caps and loose ends:** win values set to the real extremes, the small-cap decision, `tester` off.
