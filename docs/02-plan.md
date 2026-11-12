---
title: TG Málrómur Roman — plan
type: plan
status: draft
updated: 2026-11-12
description: Six workstreams that take the Roman from the 2026-11-12 evaluation to a standard, kerned Western European release. They cover VF standards, spacing, own kerning, punctuation and ASCII, WE letters, and vertical metrics with loose ends.
aliases:
  - tg-malromur-plan
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
  - "[[01-evaluation|evaluation]]"
  - "[[05-italic-plan|Italic plan]]"
---

# Plan — TG Málrómur Roman

**Raised:** 2026-11-12, from [[01-evaluation|the 2026-11-12 evaluation]]. Follows `docs/operations/02-family-pipeline.md` step 2. Roman only; the Italic follows as its own pass, with the same workstreams. Points verbatim, 2026-11-12: *"I think they just mean that they dont scale they are light in both light and black."* (the red tags) · *"But what about the weights are they correct?"*
**Status:** W1 built and saved; W2–W6 first pass built 2026-11-12, unsaved, see [[03-first-pass|first pass]]. Open: his review of the first pass; Ø ø Œ œ to draw; W7 small caps (his RMX step).
**Shape:** W › phase › list.
**Laws carried:** the work is done through the Glyphs MCP on `glyphs/TGMalromur-Roman.glyphspackage`. Nothing is saved without his word, and every edit is previewed first. From W1 on there are three masters (Light `m01`, Regular, Black `m002`), and they are edited together. Kerning is measured from the font's own outlines, never copied (ARCHITECTURE §7). His drawings are never replaced. Any change to an outline is checked in a render before it is shown.
**How a phase closes:** the measurable acceptance line comes first and is read back through the MCP, or from the exported font with fontTools. Then he looks at the result in Glyphs. A font has no page, so there is no Playwright step.

---

## W1 — VF standards (ARCHITECTURE §6)

This is the Gullhamrar route, done in Glyphs with no build script.

### 1.1 — Even weight steps (answers *"what about the weights are they correct?"*) — ✅ built 2026-11-12
- The masters are right, but the instances are placed unevenly. H stems are 144 · 177 · 202 · 227 · 261 · 294 · 344, so the steps are +33 +25 +25 +34 +33 **+50**. Medium and SemiBold sit close together, and Black jumps.
- The five middle instances move to internal 366 / 444 / 534 / 639 / 759. With a 1.156 ratio for every step, that gives H stems of 144 · 166 · 192 · 222 · 257 · 297 · 344. Regular gets lighter (177 → 166). Agreed 2026-11-12.
- This comes first because 1.2 turns the new Regular into a master.
- **Acceptance:** at each static instance, the H stem divided by the previous weight's H stem is 1.156 ± 0.01. The hairlines stay at 32–36.

### 1.2 — Regular as the default — ✅ built 2026-11-12
- Font Info › Instances › Regular (now at 366) › "Add Instance as Master". That gives three masters: Light, Regular and Black.
- `Variable Font Origin` moves from `m01` to the new Regular master.
- **Acceptance:** there are three compatible masters, and the Regular master's H stem is 166. The exported VF's `fvar` default is 400 and it names out as "Regular".

### 1.3 — Axis Location — ✅ built 2026-11-12
- Corrected 2026-11-12: the first test export was misread. Glyphs 4 ignores the `Axis Location` custom parameter and the middle weights exported at 0. The locations are now set as Glyphs 4's external axis values (custom parameter removed), and the export reads `fvar` 300/400/900 with all seven instances at 300…900. Glyphs 4 only exports the VF with a `Decompose Glyphs` parameter on the variable instance, listing the 29 glyphs built from smart parts; the source keeps its parts.
- `Axis Location` goes on the three masters and on every instance, so the userspace weights are 300 / 400 / 500 / 600 / 700 / 800 / 900. These map to internal 300 / 366 / 444 / 534 / 639 / 759 / 900.
- **Acceptance:** the exported VF's `avar` maps 400→366, 500→444, 600→534, 700→639 and 800→759 (in internal values), and `font-weight: 700` renders the Bold instance.

---

## W2 — Spacing

### 2.1 — Black sidebearings — ✅ built 2026-11-12 (unsaved)
- 147 of 197 glyphs have the same sidebearings in Light and Black. He ruled 2026-11-12: *"yeah you calculate it."*
- The reference sidebearings (H, O, n, o) are calculated from the counter-to-space relation Light already has: Black's sidebearing over its counter equals Light's. The rest follows through the existing metrics keys, and Regular comes from interpolation.
- A Black proof (`HOHOHOH`, `nonono`, text) is printed before and after, and he looks at both.
- **Acceptance:** for H, O, n and o, the Black sidebearing divided by the Black counter width matches the Light ratio within ±0.02. Every keyed glyph is in sync with its key in all masters.

### 2.2 — Round vs straight, checked against Playfair and a Didone — ✅ checked 2026-11-12: O/H 1.31, o/n 1.92 sit inside Playfair (1.24–1.33 / 1.96–1.97) and Didot (2.27 / 1.80); no change
- Rounds get more space than straights in both cases: O 84 / H 64, o 92 / n 48. The usual relation is the reverse.
- He ruled 2026-11-12: *"I have looked at playfair quite a bit in this font so I recommend checking that as reference as well as didone."* Playfair (`docs/reference/Playfair-master/`) and one classic Didone (Bodoni or Didot) are measured: the round-to-straight ratio for O/H and o/n, scaled to Málrómur's UPM, at Light and Black.
- If Málrómur sits outside both references, the rounds move towards them, and the changes are proofed before kerning starts.
- **Acceptance:** Málrómur's O/H and o/n ratios are written next to both references' ratios in this plan, and each lies between the two references or within ±0.1 of one of them.

### 2.3 — Glyphs drawn only in Light (the red tags) — ✅ built 2026-11-12 (unsaved, light blue)
- Cause: 24 red glyphs are identical in Light and Black, so they don't scale (answers *"they dont scale they are light in both light and black"*). These are `hyphen * # / \ ( ) { } [ ] « » ‹ › " ' ® ™ £ ¥`. The en dash, em dash and underscore scale only slightly (32 → 40). ı and ȷ do scale.
- Ruled 2026-11-12 (*"sure"*). These get a Black drawing: `hyphen * # « » ‹ › " ' £ ¥`. These stay light on purpose, as in a Didone and in Playfair: `( ) { } [ ] / \ ® ™`.
- Black versions are built from his Light drawings at the masters' stem ratio, and he reviews them.
- The dashes always scale: the en and em dashes take the hyphen's thickness and centre in each master.
- **Acceptance:** every glyph he marks to scale has a Black layer that differs from its Light layer, and its main stroke is within ±5% of the master's stem ratio. In every master, the three dashes have the same thickness and the same centre height.

---

## W3 — Kerning

### 3.1 — Clear the copied kerning — ✅ built 2026-11-12 (unsaved)
- The Playfair kerning (≈1570 pairs per master, ≈990 of them glyph exceptions) is exported to a JSON file in `_tmp/` and then removed from all masters.
- Ruled 2026-11-12 (*"sounds good"*): the method is the Gullhamrar route, measured from the outlines, class by class. Playfair's pair list can show which pairs need kerning, but its values are not used.
- **Acceptance:** the font has no kerning left from the copy, and the removed pairs are kept in `_tmp/` as a file.

### 3.2 — Groups — ✅ built 2026-11-12 (unsaved)
- Groups for ß ẞ, the tabular figures, period/comma/colon/semicolon, quotes, guillemets, hyphen and dashes, brackets and slash. Ligatures take the outer letters' groups (`f_i` left = `f`, right = `i`).
- **Acceptance:** every exporting letter, figure and listed punctuation mark has both groups.

### 3.3 — Kern the classes, all masters — ✅ first pass 2026-11-12 (unsaved; proofs pending)
- Group against group: round · straight · diagonal (A V W Y T) · L P F · lowercase against the caps · quotes and punctuation against letters.
- **Acceptance:** every pair of groups listed above has a value or a deliberate zero in **all three** masters. A proof string for each pair is checked in Glyphs at Light, Regular and Black.

---

## W4 — Punctuation and ASCII — ✅ built 2026-11-12 (unsaved, rough-ins light blue)

- Missing ASCII: `+ < = > ^ \` | ~`.
- Missing: nbspace, softhyphen, spacing accents `´ ¨ ¸ ¯ ˆ ˜`, `¶ † ‡ ‰ × ÷ ± ¬ ¦ ¤ ƒ µ`, ordinals `ª º` (for `ordn`), superiors `¹ ² ³`, fractions `¼ ½ ¾`.
- They are built from the font's own parts wherever possible. Anything that can't be built is roughed in light blue for his review.
- **Acceptance:** each listed glyph exists with its Unicode value in all masters, and `ordn` compiles with ª º.

---

## W5 — Western European letters — ✅ built 2026-11-12 (unsaved; Ø ø Œ œ orange, his to draw)

- Marks: `gravecomb circumflexcomb tildecomb ringcomb cedillacomb caroncomb macroncomb`, with `.case` versions. These are drawn from the existing acute and dieresis in the font's contrast, and he reviews them.
- Letters built from components:
  - capitals: À Â Ã Ä Å Ç È Ê Ë Ì Î Ï Ñ Ò Ô Õ Ù Û Ü Š Ž Ÿ
  - lowercase: à â ã ä å ç è ê ë ì î ï ñ ò ô õ ù û ü ÿ š ž
- Drawn by him: Ø ø Œ œ (orange placeholders until then).
- Each new glyph takes its base letter's kerning groups and metrics keys.
- **Acceptance:** every Windows-1252 letter has a glyph with its Unicode value, and every accented letter shares its base letter's width and kerning groups in all masters.

---

## W6 — Vertical metrics and loose ends

### 6.1 — Win metrics — ✅ built 2026-11-12 (unsaved): 1680 / 490
- After W5, `winAscent` and `winDescent` are set to the real extremes across all masters. Today those are 1675 and 484, before the WE capitals are added. Typo and hhea stay at 1510 / −400 / 100.
- **Acceptance:** no exporting glyph in any master goes beyond `winAscent` or `winDescent`.

### 6.2 — Small caps
- Moved to W7, ruled 2026-11-12. Small caps are back in v1, because RMX Scaler loads in Glyphs 4 (RMX 1.1.22; 1.1.20 couldn't load).

### 6.3 — Ligatures — dropped 2026-11-12
- Not needed. The drawn f-ligatures already take their sidebearings from `f`, `i` and `l` through metrics keys, and a new Regular master interpolates them like every other glyph. Rebuilding them would only replace his drawings.

### 6.4 — Loose ends — ✅ tester off 2026-11-12; metadata waits for the designer name
- `tester` export is turned off.
- The metadata gets Dylgjur's placeholders for copyright, license and manufacturer.
- **Acceptance:** no scratch or `_` glyph exports.

---

## W7 — Small caps (after W5) — ✅ built 2026-11-12: RMX Width 82 % · Height 75 % · Weight 0/−12/−96 from source; named `a.sc`… (Glyphs writes `smcp`/`c2sc`); 29 accented as components. 7.2 kerning still open

`smcp` and `c2sc` are on, but only the small-cap figures and `t_h.smcp` exist. Small caps were set out of v1 in May. They're back in v1 now, because he has RMX and it runs in Glyphs 4.

### 7.1 — Generate
- `A.smcp`…`Z.smcp` and the Icelandic and Western European capitals (`Thorn.smcp`, `Eth.smcp`, `AE.smcp`, accented forms built from components) are made with Filter › RMX Scaler from the finished capitals. They are scaled to the master's `smallCapHeight` (1080 in the May log, to be checked in the source) with stems held at the lowercase stem weight. `A.smcp` (currently not exporting) is replaced or aligned.
- He reviews them in Glyphs before anything is kept.
- **Acceptance:** every exporting capital has a `.smcp` glyph in all masters. Its height equals the small-cap height ±2, its vertical stem is within ±5% of `n`'s stem in that master, and `smcp` and `c2sc` compile with all of them.

### 7.2 — Spacing and kerning
- The small caps take metrics keys from their capitals scaled, and kerning groups of their own (`@A.smcp`…), measured as in W3.
- **Acceptance:** every `.smcp` glyph has both kerning groups, and the round, straight and diagonal group pairs have a value or a deliberate zero in all masters.
