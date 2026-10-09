# Material efficiency for a complete build

Guidance checked 2026-10-08. Minimize filament for the required, usable parts while preserving their fit, finish, load capacity, and print reliability. The comparison workflow below is an engineering convention; savings require actual slices and, where relevant, a representative print.

## Count the complete job

Hold the required quantities and acceptance criteria constant. Compare **total grams per complete assembly or required batch**, alongside time, cleanup, and assembly effort. Include every production plate and its repeats. Keep optional spares and trials separate. A lower waste percentage obtained by adding unwanted objects is not a reduction in the filament needed for the build.

After slicing, use **Preview > Filament** for model, flushing, and prime-tower estimates, and **Line type** for support, interface, brim, and other toolpaths. Check how the installed version groups them before adding subtotals; do not count support twice. Treat startup/calibration material omitted from the estimate separately when it affects the comparison. [Bambu slicing information](https://wiki.bambulab.com/en/software/bambu-studio/view-slicing-information)

Record only useful comparison fields:

| Variant | Required output | Total estimated g | Support/interface g | Flushing g | Prime-tower g | Time | Quality or assembly cost |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Baseline / candidate | Same parts and quantities | Actual slice | Subset, where available | Actual slice | Actual slice | Actual slice | Specific tradeoff |

If a field is unavailable, mark it unknown. Once tested, retain observed failure and rework information; a lighter slice that repeatedly fails may consume more filament overall.

## Remove the largest avoidable cost first

1. **Geometry and orientation:** compare a support-free orientation or sensible split before tuning support density. Preserve layer strength, presentation faces, and practical joints. Use the [design guidance](../../pla-functional-design/references/structure-and-assembly.md#design-for-material-efficiency).
2. **Support volume:** use selected contact regions, suitable support style, and adequate interfaces. Read [efficient supports](supports-and-bridges.md#reduce-support-material-deliberately).
3. **Colour changes:** choose separate colour parts, colour by height, or an efficient same-layer batch before tuning purge. Read [multicolour and purge](multicolour-and-purge.md).
4. **Model material:** inspect walls, solid skins, sparse infill, and local reinforcement independently. Keep a sound top-surface foundation and the required load path.
5. **Failure prevention:** use a representative fit, support, or colour-transition test before a costly batch. Preserve the production orientation, filament, and relevant cooling context. Follow the [quality comparison workflow](quality-workflow.md#make-the-comparison-representative).

This order is a screening strategy. Prioritize the largest category shown by the actual slice rather than changing every setting.

## Choose infill for its job

For a decorative model, **Lightning** can support the roof with little internal material. It does not provide a general structural core. **Support Cubic** is another candidate for economical internal support on visual models; inspect the resulting roof foundation. Prusa discusses both uses, and Bambu offers these patterns. [Prusa material-saving guidance](https://blog.prusa3d.com/10-tips-for-saving-filament-money-and-environment_71415/), [Bambu fill patterns](https://wiki.bambulab.com/en/software/bambu-studio/fill-patterns)

For functional parts, place walls and reinforcement where the load requires them. A local modifier may avoid applying dense infill throughout the part. Check actual deposited paths around ribs, screw seats, and roots. See [walls and strength](walls-and-strength.md). Do not use reduced flow ratio as a material-saving technique; it changes extrusion calibration.

Treat **Infill combination** and faster infill patterns primarily as time-saving options unless the slice also shows lower mass. Likewise, coarser layers do not automatically reduce the amount of polymer in a single-colour model. Any multicolour saving may instead come from fewer filament changes.

## Exposed infill and open structures

When a continuous face is unnecessary, consider [CAD frames, lattices, and ribbed shells](../../pla-functional-design/references/lightweight-structures.md). CAD controls the actual openings and retained attachment regions. Exposed slicer infill is a separate option for suitable parts; removing walls or skins changes the structural part, not just its appearance.

Bambu documents **Locked Zag** for applications using infill as an exterior, with separate skin/skeleton density, line width, and overlap controls. Check availability in the installed version. Its guide's instruction to hide walls in Preview is only a display operation; exposing the printed structure requires intentional wall and top/bottom-shell settings verified in the slice. Do not transfer footwear or flexible-material strength claims to PLA. [Bambu exposed-infill overview](https://wiki.bambulab.com/en/software/bambu-studio/fill-patterns), [Locked Zag controls](https://wiki.bambulab.com/en/software/bambu-studio/manual/locked-zag)

Inspect frame connections, modifier boundaries, islands, bridges, and the first layer. Keep solid attachment pads and useful rims where needed. Save the native project and effective settings because an STL alone cannot reproduce a structure created by infill. Compare it with a CAD lattice using the same functional requirements; neither the pattern name nor infill percentage establishes equal strength.

## Preserve savings through revisions

Keep the chosen print orientation, colour assignment, support painting, and overrides in the native project. Record the source revision, Studio version, comparison quantities, actual estimates, and whether the candidate was only sliced or also printed. Re-slice affected plates after changes. Coordinate with [plate planning](../../print-project-organization/references/bambu-plates.md#plan-colour-and-material-efficiency) so an efficient part becomes an efficient complete build.
