---
title: TG Málrómur Roman — first pass (W2–W6)
type: audit
status: active
updated: 2026-11-12
description: What the 2026-11-12 pass changed in the Roman, unsaved, for review — spacing, Light-only glyphs weighted, own kerning, punctuation and symbols, Western European letters, line metrics, and what is left for him.
aliases:
  - tg-malromur-first-pass
tags:
  - project/kol-foundry
  - domain/typography
related:
  - "[[01-evaluation|evaluation]]"
  - "[[02-plan|plan]]"
---

# TG Málrómur Roman — first pass (W2–W6)

Done 2026-11-12 through the Glyphs MCP on `glyphs/TGMalromur-Roman.glyphspackage`. **Everything after W1 is unsaved.** Review it in Glyphs, then save or close without saving (the W1 save on disk is the way back). Renders: `_tmp/2026-11-12-first-pass-renders/`. Scripts: `_tmp/2026-11-12-first-pass-scripts/`.

## Review first

1. **Black spacing is tighter** (W2.1). H 64 → 54, O 84 → 73, n 48 → 40, o 92 → 67 in Black; Regular moved 11 % of the way. Before/after: `w21_before.png`, `w21_after.png`.
2. **Light-blue glyphs are estimates:** the Black/Regular `# £ ¥ * ‹ › « » ' "`, all new marks and accented letters, and every new symbol.
3. **Orange = yours to draw:** Ø ø (O/o + a scaled slash) and Œ œ (O+E, o+e overlapped).
4. **Kerning is a first pass** measured from the outlines. Check it in proofs.
5. **Rough-ins that need real drawing:** ¶ (mirrored P + stem), ƒ (f lowered), ¤, µ, ‰, the ordinals ª º, superiors ¹ ² ³ and fractions ¼ ½ ¾ (scaled figures, so their strokes are thin), the tilde, ring and cedilla marks.

## W2 — Spacing

- **2.1** Black sidebearings of H O n o from Light's counter-to-space ratio (Light/Black ratio equal within 0.002), set as layer keys on Black and Regular. Everything keyed to H, O, n, o follows (426 layers re-synced).
- **2.2** Round vs straight checked against references (round sidebearing ÷ straight):

| Font | O/H | o/n |
|---|---|---|
| Málrómur Light | 1.31 | 1.92 |
| Playfair 360, display | 1.33 | 1.97 |
| Playfair 900, display | 1.24 | 1.96 |
| Didot (macOS) | 2.27 | 1.80 |

  Málrómur sits inside the references, so nothing changed. Rounds wider than straights is normal for a Didone; the evaluation's "usual relation is the reverse" was wrong for this style. Playfair's Black also spaces tighter than its Light (H 43 → 33), which agrees with 2.1.
- **2.3** Regular/Black drawn from his Light for `# £ ¥ * ‹ '` (each stroke widened in proportion to its own thickness; `#` stroke by stroke; hairlines kept in £ ¥). `« » › "` follow their components. Hyphen, en and em dash share one thickness and centre per master (64 / 68 / 104, grown like the period). Brackets, slashes, ® ™ stay light as ruled.

## W3 — Kerning

- **3.1** The Playfair-derived kerning (4726 pairs over three masters) is saved by glyph name in `_tmp/2026-11-12-playfair-kerning-removed.json` and cleared.
- **3.2** Groups for ß ẞ, the tabular figures (`tf`, not kerned), and all punctuation (period, comma, colon, quotes, guillemets, hyphen/dashes, brackets, slash, …). Ligatures take their outer letters' groups. No exporting letter, figure or punctuation mark is left without groups.
- **3.3** ≈1330 class pairs per master (Light 1328, Regular 1329, Black 1332), measured as for Gullhamrar (`measure.py`, mean profile gap against H·H / n·n, spacing-owned sides neutralised). Samples Light / Black: A·V −112 / −148, T·o −108 / −88, L·T −176 / −180, P·A −92 / −140, quote·A −60 / −92. Proof: `w33.png`.

## W4 — Punctuation and ASCII

- All printable ASCII and all of Windows-1252 now exist.
- Built from the font's own parts, in every master: + = × ÷ ± ¬ from hyphen-weight bars and the period; < > from ‹ › scaled; | ¦ at hyphen weight; ^ ~ ` ´ ¨ ¸ ¯ ˆ ˜ from the marks; nbspace; soft hyphen = hyphen; † ‡ from n's stem; ‰ from % plus a scaled zero; superiors, ordinals and fractions from scaled figures and a, o.

## W5 — Western European

- New marks, drawn from his acute (grave, circumflex, caron), his o (ring) and comma (cedilla), plus a macron bar and a tilde wave, each with a `.case` version. Anchors added to C N S Z c n s z (and bottom anchors to C c); no outline of his touched.
- 46 accented letters as components (À Â Ã Ä Å Ç È Ê Ë Ì Î Ï Ñ Ò Ô Õ Ù Û Ü Š Ž Ÿ and lowercase, ÿ), each with its base letter's groups.

## W6 — Line metrics and loose ends

- `winAscent` 1680 / `winDescent` 490 on all masters (tallest: Ä Black 1675; deepest: f_j −484). Typo/hhea unchanged.
- `tester` no longer exports. Font metadata is left alone until the designer name is settled.
- The variable export's `Decompose Glyphs` list now covers every glyph built on the smart parts (including the new accented ones).

## W7 — Small caps

Not done: RMX Scaler runs from the Filter menu and has no documented script interface. It's his step, after Ø Œ are drawn.

## Checks run

| Check | Result |
|---|---|
| Windows-1252 missing | none |
| Exporting glyphs incompatible across masters | none |
| `_` or scratch glyphs exporting | none |
| Test VF export (scratchpad) | 294 glyphs, `fvar` 300–400–900, default "Regular", win 1680/490, kerning in GPOS |
