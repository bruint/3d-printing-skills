# Choosing techniques for print quality

Guidance checked 2026-10-08. This workflow combines the linked manufacturer guidance and first-hand experiments. The sequence and comparison method are working practices for our builds; individual results still need to be checked with the actual part and filament.

## Plan the important surfaces

Identify the presentation faces, mating faces, and loaded features before choosing orientation. A flat presentation face may benefit from bed texture; a curved insert may benefit from tilting; a precision underside may justify a split or a different support interface. Assign those choices per part. Use labelled views to show the user which surface each decision affects.

Start with the actual printer/nozzle/filament/plate presets and preserve known successful settings. For an existing defect, match the symptom before changing a profile. A photo in consistent lighting plus the corresponding layer preview is usually more informative than a list of global settings.

## Match the symptom

| Observation | First useful investigation or technique |
| --- | --- |
| Contour-like terraces on shallow curves | Compare orientation, then local variable layer height. See [curved inserts](fit-and-finish.md#curved-inserts-and-orientation). |
| Straight facets around an intended curve, also visible in the mesh | Improve CAD/export tessellation before adjusting the printer. See [geometry resolution](../../pla-functional-design/references/structure-and-assembly.md#export-curves-at-useful-resolution). |
| A vertical seam or scattered start/stop marks | Paint a suitable seam location; compare a scarf seam on smooth contours. See [seams](fit-and-finish.md#visible-walls-and-seams). |
| Horizontal shiny/matte bands with little change in shape | Compare outer-wall speed, volumetric flow, and cooling changes. Consider smoothing wall speed along Z. See [bands](fit-and-finish.md#gloss-bands-and-transition-ridges). |
| A ridge where a floor, shelf, or solid region ends | Inspect the solid-fill transition and layer time; this may be a geometry/thermal transition. See [transition ridges](fit-and-finish.md#gloss-bands-and-transition-ridges). |
| Ripples echoing after corners or lettering | Investigate vibration, motion calibration, and outer-wall speed/acceleration using the printer's own guidance. See the distinction below. |
| Random pits, bubbles, or new stringing | Check filament condition, nozzle condition, and temperature before tuning retraction. See [filament condition](filament-and-reliability.md#filament-condition-before-tuning). |
| Small tips become soft, curled, or smeared | Check layer cooling time and compare by-layer printing of several useful parts. See [cooling](filament-and-reliability.md#cooling-and-speed). |
| Flat tops show gaps, ridges, or infill outlines | Inspect the supporting infill and solid skin; tune deposition before ironing. See [top faces](fit-and-finish.md#top-faces). |
| Rough supported undersides or sagging bridges | Evaluate orientation, support contacts, interface material, and bridge direction separately. See [supports and bridges](supports-and-bridges.md). |
| Bed-edge flare or lifted corners | Diagnose first-layer/plate behavior and local adhesion; compare painted brim ears if only corners lift. See [first layer](filament-and-reliability.md#first-layer-and-supports). |
| A fit binds although the surfaces look sound | Measure the cooled part and distinguish CAD clearance, XY error, and bed-edge flare. See [dimensional fit](fit-and-finish.md#dimensional-fit). |

Prusa identifies ghosting as a vibration effect that can respond to lower printing speed. Apply that diagnostic principle with P2S-specific maintenance and calibration; its belt-tension procedures are for Prusa hardware. Repeated artifacts throughout a wall deserve investigation separately from a single geometry-linked ridge. [Prusa ghosting explanation](https://help.prusa3d.com/article/ghosting_1801)

## Make the comparison representative

- Use the smallest sample that preserves the problem: the curved face and attachment peg, the real counterbore, a supported underside, or a strip containing the floor-to-wall transition. Cutting away all surrounding geometry may remove the cause.
- Compare a known baseline with one change or a small, deliberate matrix. Label variants in the project and record the setting values. First inspect the actual toolpaths, support access, and effective overrides.
- Match the production filament, orientation, shell structure, and relevant thermal conditions. Several parts printed together get different cooling time than one part alone. When cooling or gloss matters, keep the comparison plate consistent and confirm the selected result under the intended production layout.
- Judge the relevant outcomes: appearance in consistent light, support cleanup, cooled mating fit, and any affected loaded feature. A cosmetic improvement alone does not establish strength.
- Save the successful setup with the native project and record printer/nozzle, filament brand/type/color, plate, slicer version, orientation, changed settings, and the observed result. State whether it is recommended, sliced, or physically tested; retain the baseline until the comparison succeeds.

Do not require a full calibration suite for every build. Reuse a proven material/setup combination and test the feature whose result is uncertain.
