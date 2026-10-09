# Fit and finish

Guidance checked 2026-10-08. Diagnose where the error occurs before applying a global correction.

## Dimensional fit

- If an otherwise consistent closed hole is undersized, trial **X-Y hole compensation**. Positive values enlarge holes; the value is an offset per side, so **+0.10 mm changes a circular diameter by about +0.20 mm**. It acts on closed holes in each sliced XY layer, not every feature called a hole in CAD. Side openings and horizontal holes need particular care.
- **X-Y contour compensation** changes outside contours separately. Check measured external error rather than using it to fix holes.
- Stabilize extrusion first. Use a coupon with the intended filament, orientation, layer height, wall generator, and wall order. Keep intentional CAD clearance separate from compensation for measured printing error; avoid applying the same correction twice.

Bambu documents the signs, offset convention, and closed-path limitation in [XY hole/contour compensation](https://wiki.bambulab.com/en/software/bambu-studio/xy-hole-contour-compensation).

If the part only binds at its bed-contact edge, inspect **Elephant foot compensation**, plate choice, and first-layer behavior before altering the whole part. Excessive compensation can compromise small first-layer features. Measure on the cooled part and repeat after a plate change. A visible brim gap in Preview can result from compensation and does not by itself prove failed adhesion. [Bambu elephant-foot guidance](https://wiki.bambulab.com/en/software/bambu-studio/parameter/elephant-foot).

## Visible walls and seams

As practical placement rules, put the seam on a hidden or acceptable edge and away from a sliding/contact face where possible. Inspect the seam inside holes as well as on the outside. Random seam placement spreads marks; it does not remove them. Check extrusion and pressure compensation before treating seam settings as the cure for blobs. Use an actual A/B coupon when comparing wall order for dimensional fit.

For smooth circular walls with no good hiding place, compare **Scarf seam** with an ordinary, deliberately placed seam. Check both filament scarf settings and process overrides. Bambu's smart application avoids unsuitable overhangs and uses ordinary seams where corners conceal them. Compare the actual seam in Preview and on a representative curved wall. **Contour and Hole** also affects hole surfaces, so check fits; extending the scarf around the entire wall can introduce bonding or surface defects. [Bambu seam and scarf settings](https://wiki.bambulab.com/en/software/bambu-studio/Seam)

For travel marks or strings crossing a visible wall, inspect travel paths and consider **Avoid crossing wall**. Its detours can add time; keep the change local to the problem and address moisture or extrusion problems as well. [Bambu advanced quality controls](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings)

## Gloss bands and transition ridges

For gloss bands, compare Preview speeds and volumetric flow across affected layers and check cooling-driven slowdowns. **Don't slow down outer walls** can improve consistency but removes one source of cooling time. Keep cooling adequate for small sections. [Bambu cooling settings](https://wiki.bambulab.com/en/software/bambu-studio/auto-cooling)

When available, trial **Smoothing Wall Speed Along Z** on continuous curved or tall presentation walls. It smooths speed changes between adjacent outer-wall layers and adds print time. Distinguish it from **Smooth speed discontinuity area**, which treats transitions between overhang and non-overhang regions along a path. Inspect the resulting speed preview before comparing prints. [Bambu advanced quality controls](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings)

A physical ridge at a floor/deck transition can also involve solid-fill changes, cooling time, and shrinkage. Compare the defect height with the layer where infill becomes solid or stops. A section retaining that transition makes a better coupon than a plain cube. Revisit wall order, fill overlap, or geometry only when the slice supports that diagnosis; a gloss setting cannot be assumed to remove a dimensional ridge. [Prusa's Benchy hull-line investigation](https://help.prusa3d.com/article/the-benchy-hull-line_124745)

## Curved inserts and orientation

For small separate inserts with shallow curved presentation faces, such as eyes, teeth, or domed details, compare flat printing with a **roughly 45° tilt** before relying only on finer layers. Choose the insert's orientation independently of the main body. Tilting can make the important visible slopes steeper relative to the bed, reducing broad contour-like terraces there; it does not eliminate layer steps from every surface. CNC Kitchen demonstrates the broader surface-finish principle with a relief printed on its side. [Orientation and surface-finish experiments](https://www.cnckitchen.com/blog/stop-printing-flat-the-45-secret-for-stronger-parts)

- Treat 45° as a trial angle, adjusted for the actual curve and overhangs. For a flat-backed insert, this means tilting its backing plane about 45° to the bed; spinning it around the build Z axis alone does not change its slopes.
- Inspect the visible face and new overhangs in the layer preview. Put support contacts on hidden, noncritical areas where practical; a hidden mating face still needs an accurate fit. Check bed contact, support stability, brim needs, and cooling for small sections.
- Compare a representative insert at the same filament and layer height first. Check appearance and assembly fit after support removal, including pegs or clips whose layer direction changed. Adjust clearance only from evidence.
- Save the selected object rotation in the native project and record it with the part's print setup, keeping assembly pose distinct from print pose. Preserve it when arranging or updating plates.

The specific 45° small-insert technique comes from the creator's account supplied by the user, describing Snorlax's belly and Gengar's eyes and teeth. [Creator's linked Gengar model](https://makerworld.com/en/models/3391336-wobbly-gengar-halloween-fidget-toy-no-ams). The linked print profile was not independently inspected; this is a candidate technique, not a tested result on the user's printer or an official Bambu setting.

## Spend resolution where it helps

After selecting orientation, use **Variable Layer Height** to reduce layer height around shallow curves and retain coarser layers elsewhere. Smooth the transitions and inspect the resulting layer profile. Stay within the selected nozzle/profile limits, preserve solid-skin thickness in millimetres, and check [support and prime-tower interactions](supports-and-bridges.md#check-interactions-before-saving-the-plate). [Bambu variable layer height](https://wiki.bambulab.com/en/software/bambu-studio/adaptive-layer-height)

Layer height primarily changes Z resolution. For missing fine lettering, slots, or XY detail, compare wall generation and line widths, enlarge the feature, or consider a smaller supported nozzle. Inspect whether the toolpaths contain the detail before printing. Finer layers cannot recover a coarse source mesh or automatically improve strength. [Prusa layer-height and resolution explanation](https://help.prusa3d.com/article/layers-and-perimeters_1748)

## Top faces

Inspect the solid skin's support before polishing its appearance: gaps or infill outlines may call for more local support beneath the top or adequate solid thickness. Judge filament flow on a broad, well-supported patch with ironing off; a tiny infill island or first-layer bulge can mislead the assessment. Use the Bambu calibration workflow with the actual filament, temperature, and intended speeds. [Ellis' extrusion-multiplier method](https://ellis3dp.com/Print-Tuning-Guide/articles/extrusion_multiplier.html)

If a residual deposition error is confined to tops, **Top surface flow ratio** can adjust top solid infill without changing all walls. Check the underlying filament flow ratio first and compare a small patch; the factors multiply. [Bambu advanced quality controls](https://wiki.bambulab.com/en/software/bambu-studio/parameter/quality-advance-settings)

**Monotonic/Monotonic line** are candidates for a consistent flat-top pattern; inspect edge connections and texture. [Bambu fill patterns](https://wiki.bambulab.com/en/software/bambu-studio/fill-patterns).

If marks from the layer immediately beneath the top are the issue, check **Sub-top surface pattern** in versions that provide it. Bambu describes Monotonic there as a way to reduce marks without changing all internal solid infill; it does not apply when that layer is a bridge. [Bambu advanced strength settings](https://wiki.bambulab.com/en/software/bambu-studio/parameter/strength-advance-settings).

Use **Ironing** selectively on visible, flat, upward-facing surfaces after achieving a sound top skin. It adds time and can worsen finish if flow, spacing, or adhesion is unsuitable. It does not smooth vertical walls or erase the staircase of curved tops. Leave it off for a utilitarian part unless that finish is requested; compare a small patch before committing a large top face. [Bambu ironing guidance](https://wiki.bambulab.com/en/software/bambu-studio/parameter/ironing).

## Deliberate texture

For a grippy or matte appearance, consider a restrained **Fuzzy Skin** on selected exterior walls. It textures wall paths rather than smoothing the geometry; top and bottom fill surfaces behave differently. Use painting or a modifier where supported, and keep it off mating holes, slideways, threads, and critical datums unless the altered fit is tested. Compare a small patch using the intended material and scale. [Bambu fuzzy-skin controls](https://wiki.bambulab.com/en/software/bambu-studio/parameter/fuzzy-skin)

For a broad flat presentation face, also consider printing it against a suitable build plate. Use [the design skill's plate-texture guidance](../../pla-functional-design/references/p2s-pla.md#minimalist-form-and-texture) when selecting that orientation.
