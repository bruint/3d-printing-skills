# Walls and strength

Guidance checked 2026-10-08. Use the conditions below; the highest value or most elaborate option is not inherently best.

## Wall order

Location: **Process > Quality > Advanced > Order of walls**.

| Choice | When to choose it | Tradeoff |
| --- | --- | --- |
| **inner/outer** | General starting choice, especially for overhangs: the neighboring inner wall is already present. | Inner-wall extrusion can affect the exterior. |
| **outer/inner** | Trial for surface defects from inner-wall squeezing or shrinkage. | Seams can stand out; overhangs lose adjacent-wall support. |
| **inner wall/outer wall/inner wall** | Trial for exterior finish with several walls. The wall beside the exterior prints last. | The gap beside the outer wall means it does not inherit inner/outer's overhang support. |

This is Bambu's stated mechanism and tradeoff, not a guarantee of better dimensions or strength. [Bambu advanced quality settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings).

The distinct three-stage order needs at least **three actual wall paths**. Thin sections, two-wall regions, the wall generator, and first-layer/brim handling can change the effective order. Do not promise a particular fallback for every version: inspect the extrusion sequence in Preview. [Bambu perimeter-generation implementation](https://github.com/bambulab/BambuStudio/blob/master/src/libslic3r/PerimeterGenerator.cpp).

## Walls, infill, and shells

- For shell-dominated bending parts, increase **Wall loops** or reinforce the loaded region before applying high infill everywhere. Compression, screw-bearing areas, and support beneath broad top skins can justify denser infill. Orientation and geometry still matter. This is an application of [Prusa's perimeter/infill guidance](https://help.prusa3d.com/article/infill_42), not a measured strength claim for this part.
- Practical starting range for ordinary functional PLA: **4–5 walls and 15–25% infill**, refined by load and toolpaths. More wall loops only help if the geometry has room for them; inspect narrow ribs and roots. Line width times loop count is only a rough thickness estimate because spacing and variable-width paths matter.
- Choose top/bottom material in **millimetres as well as layers**. A practical trial for broad functional faces is roughly **0.8–1.2 mm** of solid skin, adjusted for span and load. Five 0.20 mm layers equal 1.0 mm; five 0.12 mm layers equal 0.6 mm. Check both shell-layer and shell-thickness fields and the resulting slice. This range is a heuristic, not a Bambu specification.

**Infill choices:** Grid has same-layer crossings that can accumulate material and cause scraping. Gyroid avoids those crossings, but complex paths can increase slicing cost and vibration. Lightning is for economical support of top skins on decorative parts. Cross Hatch is a candidate for faster, lightly loaded parts; Bambu's current guide describes it for non-load-bearing use. Compare the actual slice rather than declaring one pattern universally strongest. [Bambu fill patterns](https://wiki.bambulab.com/en/software/bambu-studio/fill-patterns).

**Infill/Wall overlap** improves connection, but excessive overlap can bulge the exterior. Retain the preset unless the actual junction is deficient; check flow and geometry first. **Ensure vertical shell thickness** adds material near slopes. **Infill combination** makes thicker infill layers while retaining the wall layer height; inspect the resulting paths and flow demand when using it to save time. [Bambu advanced strength settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/strength-advance-settings).

**Only one wall on top surfaces** can override the requested wall count locally. Review loaded rims before using this cosmetic option. **Print infill first** changes all horizontal fill types, not just sparse infill; retain the preset unless addressing a specific problem. [Bambu advanced quality settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings).

## Wall generator and small features

Try **Arachne** when thin text or changing wall thickness disappears with fixed-width paths. **Classic** is useful for continuous, predictable loops. Compare both when there are seam artifacts, floating paths, uneven surfaces, or missing features. Arachne does not make a physically undersized rib structurally adequate; check actual line width and continuity. [Bambu wall-generator explanation](https://wiki.bambulab.com/en/software/bambu-studio/wall-generator), [Bambu troubleshooting comparison](https://wiki.bambulab.com/en/software/bambu-studio/WallGenerator).
