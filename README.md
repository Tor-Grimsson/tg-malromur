# TG Málrómur

Placeholder — description, images and supported languages to come.

High-contrast Didone in Roman and Italic. Both are spaced and kerned from their own outlines, cover Windows-1252 and have small caps.

Read from the shipping fonts `export/TGMalromurRomanVF.ttf` and `export/TGMalromurItalicVF.ttf` on 2026-11-12.

| | |
|---|---|
| Family name in the font | `TG Malromur`, deliberately without the accents, which aren't safe in font names. TG Málrómur is the public name. |
| Version | 1.000 (exported with Glyphs 4) |
| Format | Two variable TTFs, Roman and Italic (italic angle 16°); 14 static OTFs, one per style; WOFF2 of the VFs in `export/web/` |
| Glyphs | 355 Roman, 373 Italic (233 encoded each) |
| Masters | 3 per style: Light, Regular, Black |
| Default style | Regular / Italic (wght 400) |
| Units per em | 2048 |
| Features | small caps (`smcp`, `c2sc`), kerning |
| Licence | SIL Open Font License 1.1 (`OFL.txt`) |

## Axes

| Axis | Min | Default | Max |
|---|---|---|---|
| Weight `wght` | 300 | 400 | 900 |

## Styles — 7 per style

| Weight | Roman | Italic |
|---|---|---|
| 300 | Light | Light Italic |
| 400 | Regular | Italic |
| 500 | Medium | Medium Italic |
| 600 | SemiBold | SemiBold Italic |
| 700 | Bold | Bold Italic |
| 800 | ExtraBold | ExtraBold Italic |
| 900 | Black | Black Italic |

## Files

| Folder | Holds |
|---|---|
| `glyphs/` | `TGMalromur-Roman.glyphspackage`, `TGMalromur-Italic.glyphspackage` |
| `export/` | `TGMalromurRomanVF.ttf`, `TGMalromurItalicVF.ttf` and 14 static `.otf` (ship straight from Glyphs); `web/` WOFF2 |
| `specimen/` | proofs (not in git; rebuilt with `tools/kol-specimen/make-proof.sh` in kol-foundry) |
| `docs/` | evaluations and plans, Roman and Italic (W1–W7), first pass, `OPEN.md` |
