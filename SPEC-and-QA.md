# MuzHouse — Figma Implementation Spec & QA

Measured from Figma file `mkmHLdjifv85Xa2UXl6hDr`, frame **"Main page 1600" (15:5)**.
All coordinates are in the 1600px canvas space. The implementation places every element at these exact values and scales the canvas to the viewport.

## Global tokens

| Token | Value | Source node |
|---|---|---|
| Canvas | 1600 × 6992 (content ≈ top 1890px; rest empty) | 15:5 |
| Page background | `#FDF6EA` | cover gradient target |
| "Black" (text/buttons/cards label) | `#4C433B` | Figma variable |
| Display headline color | `#3D362F` | 15:1395 / 15:1689 |
| Mocha (faint letters) | `#AB947B` | 15:1698… |
| Mocha (menu rule) | `#AB937B` @ 40% | 15:1662 |
| Card background | `#ECDBCA` | 15:1829 |
| Display font | **FONTSPRING DEMO – The Seasons** (Italic / Regular / Bold) | all serif text |
| UI font | **Montserrat** (Regular / Medium) | nav, subhead, button, labels |

## Section 1 — Menu (15:1661) · band left 120, width 1360, height 87

| Element | Spec | Coord |
|---|---|---|
| Logo "Muz" | The Seasons **Italic**, 60px, `#4C433B` | left 133, top 41 |
| Logo "House" | The Seasons **Bold**, 60px, `#4C433B` | left 271, top 33 |
| Nav "About Us" | Montserrat Medium 22px, `#4C433B`, capitalize | left 779, top 66 |
| Nav "Lessons" | ″ | left 943, top 66 |
| Nav "Pricing" | ″ | left 1092, top 66 |
| Nav "Teachers" | ″ | left 1232, top 66 |
| Nav "Contact" | ″ | left 1391, top 66 |
| Divider rule | `#AB937B` @ 0.4 opacity, 1360 × 1px | left 120, top 119 |

## Section 2 — Cover / Hero (15:1751) · x −18, top 169, 1700 × 836

| Element | Spec | Coord |
|---|---|---|
| Background curves ×3 | thin line vectors (raster assets 15:1694–1696) | ≈ y 186–1005 |
| Faint letters m u z h o u s e | The Seasons Italic 80px, `#AB947B`, blur 3px | 62,838 / 187,734 / 338,654 / 1034,614 / 1102,441 / 1164,299 / 1287,169 / 1444,238 |
| "Modern" | 170px `#3D362F` — **M** italic + "odern" regular | left 162, top 264 |
| "music school" | 170px `#3D362F` — **m** italic + "usic" reg + **s** italic + "chool" reg | left 427, top 448 |
| Arch image (15:1688) | 413 × 503, radius 200/200/0/0; fill scaled h 123.15% / top −6.67%; gradient to-top transparent @22% → `#FDF6EA` | left 593, top 368 |
| Star 1 | 49 × 48, mocha | left 309, top 454 |
| Star 2 | 55 × 54, mocha | left 1162, top 703 |
| Subhead | Montserrat Regular 20px `#4C433B`, line-height 1.1, letter-spacing 0.4px, centered, width 413 | left 593, top 881 |
| Button | 260 × 50, bg `#4C433B`, **radius 0**; text "Book a Lesson" Montserrat Medium 22px `#FDF6EA`, capitalize, centered | left 670, top 945 |

## Section 3 — Instruments (15:1921) · x 119, top 1106, 1361 × 783

| Element | Spec | Coord |
|---|---|---|
| Heading | The Seasons **Bold** 50px, `#4C433B` @ 0.9 opacity, line-height 55, capitalize, centered: "We come to your home for the lessons" | top 1106 |
| Card | 310 × 319, bg `#ECDBCA`, radius 20 | grid below |
| — card image | 282 × 220, radius 10 | +14 / +14 inside card |
| — card label | Montserrat Medium 32px `#4C433B` | +14 / +250 inside card |
| — card arrow | down-arrow asset 30 × 30 (rotated −90°) | +~266 / +257 inside card |
| Row 1 (top 1211) | Guitar (x120) · Violin (x470) · Piano (x820) · Voice (x1170) | |
| Row 2 (top 1570) | Drums (x120) · Bass Guitar (x470) · Saxophone (x820) · Band (x1170) | |
| Column gap | 40px | |
| Row gap | 40px | |

---

# Visual QA — mismatches between current build and Figma

Resolved (now exact): canvas size, content band, all coordinates, color tokens, nav size 22px, logo italic/bold 60px + 8px offset, menu rule `#AB937B`@40%, heading 50px Bold `#4C433B`@0.9, arch radius 200/200/0/0 + gradient stop @22% + fill scale, card/label/grid metrics, button radius 0.

Open mismatches — these require assets/decisions I will **not guess** (per your instruction to stop and ask):

| # | Mismatch | Reason | Needs from you |
|---|---|---|---|
| 1 | **Display font** is Cormorant Garamond, not "The Seasons" | "The Seasons" is a FONTSPRING **demo** font — cannot be embedded/licensed on a live site | Provide the licensed web-font files (woff2), or approve the substitute |
| 2 | **Card photos + arch photo** are placeholders | Figma image fills can't be pulled programmatically here (asset download is blocked in this environment) | Export the 9 images from Figma into `/images` with the listed filenames |
| 3 | **Background wavy curves** are hand-drawn approximations | Same — the 3 vectors (15:1694–1696) are raster fills I can't fetch | Export those 3 vectors as SVG/PNG |
| 4 | **Star sparkles** are a generic 4-point star | The Figma star asset can't be fetched | Export the star asset, or approve substitute |
| 5 | **Down-arrow** rendered as circle + chevron | Figma metadata only exposes a 30px "down-arrow" icon (rotated −90°); the exact glyph/whether it includes a circle isn't readable | Export the arrow asset, or confirm the intended glyph |

---

# Image export map (drop into `/images`, keep these exact filenames)

Export each Figma node as a JPG/PNG and save it over the matching placeholder. No code changes needed afterward — the build already points at these names.

| Save as `/images/…` | Figma node | Where it appears |
|---|---|---|
| `hero-arch.jpg` | 15:1688 (IMG_4016) | hero arch image |
| `card-guitar.jpg` | 15:1833 | Guitar card |
| `card-violin.jpg` | 15:1846 | Violin card |
| `card-piano.jpg` | 15:1853 | Piano card |
| `card-voice.jpg` | 15:1860 | Voice card |
| `card-drums.jpg` | 15:1867 | Drums card |
| `card-bass-guitar.jpg` | 15:1874 | Bass Guitar card |
| `card-saxophone.jpg` | 15:1881 | Saxophone card |
| `card-band.jpg` | 15:1888 | Band card |

Optional (currently drawn as inline SVG; export only if you want the exact raster):
- background wavy curves → `hero-curves.png` (nodes 15:1694–1696)
- star sparkle → `star.svg`/`.png` (node 15:1729/1737)
- card down-arrow → `arrow.svg`/`.png` (node 15:1841)

Export tip in Figma: select the node → right panel **Export** → add a preset (e.g. 2x PNG or JPG) → Export. Recommended ~2× the displayed size (cards ≈ 564×440px, arch ≈ 826×1006px).
