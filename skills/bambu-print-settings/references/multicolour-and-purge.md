# Efficient multicolour printing and purge

Guidance checked 2026-10-08 for single-nozzle workflows, including the user's usual P2S. Confirm the available filament-changing equipment; AMS ownership is not assumed. Use [whole-build material accounting](material-efficiency.md#count-the-complete-job) before claiming savings. Examples from Prusa explain transferable principles; their controls and numeric presets are not P2S recipes.

## Choose how the colours become part of the build

| Approach | Useful for | Design and printing checks |
| --- | --- | --- |
| Separately printed colour inserts or panels | Eyes, badges, buttons, decorative trim | Provide locating features, a suitable retention method, and tested clearance. Compare the extra joints, shells, supports, and assembly effort. |
| Colour changes at selected heights | Raised lettering, signs, horizontal bands | Keep each required colour thick enough for coverage. Preview the actual layer transition and check the printer's supported change/pause workflow. |
| A shallow coloured face printed against the plate | Flat badges and inlaid artwork | Keep mixed-colour geometry to the necessary depth; inspect first-layer detail, opacity, bonding, and bed texture. This is a design candidate, not a fixed layer-count recipe. |
| Repeated multi-colour toolpaths | Curved patterns or inseparable features | Inspect changes by layer and compare production batch layouts. |

Grouping loose single-colour parts into colour-specific jobs is supported by Bambu's multi-plate workflow. [Bambu multi-plate guide](https://wiki.bambulab.com/en/studio-handy/multi-plate-printing) Prusa demonstrates raised designs with colour changes by height and explains why translucent filament needs enough coverage. [Colour-change examples](https://blog.prusa3d.com/practical-uses-of-color-change-in-prusaslicer_59563/)

Bambu's **Change Filament** command in Preview requires an AMS. A manual swap needs an appropriate **Add Pause** and verified printer unload/load/resume procedure; do not copy Prusa's colour-change G-code into a P2S job. [Bambu layer operations](https://wiki.bambulab.com/en/software/bambu-studio/view-slicing-information)

## Reduce changes before reducing each flush

Colours per layer and the number of mixed layers drive change count. Compare rotations that concentrate colour into fewer layers, including their support and finish costs. Coarser layers can reduce repeated changes where detail permits. Identical copies aligned in Z can share changes; different stripe heights can make a same-palette batch less efficient than separate jobs. Slice both plans for the required quantities. [Bambu waste-reduction guide](https://wiki.bambulab.com/en/software/bambu-studio/reduce-wasting-during-filament-change)

Retain **Auto** filament sequence unless a specific surface or process need justifies an override. For later layers, Bambu tries to reuse the preceding layer's last filament and choose a sequence with less flushing. First-layer Auto uses contour-area logic. A fixed light-to-dark order is not always the cheapest sequence over the whole job. [Bambu filament sequence](https://wiki.bambulab.com/en/software/bambu-studio/parameter/filament-sequence-for-different-layers)

## Reuse necessary purge where the result is acceptable

Candidate Bambu controls are **Flush into objects' infill**, **Flush into objects' support**, and **Flush into this object**. Support flushing requires the prime tower. A flush object needs a multicolour job producing flush material. Recalculate the complete job after enabling routing. [Bambu flushing controls](https://wiki.bambulab.com/en/software/bambu-studio/reduce-wasting-during-filament-change)

An existing, useful, appearance-insensitive object can accept colour transitions. Its available toolpaths must coincide with the changing layers: a short object cannot absorb later flushes, while additional height may print with fresh filament. Flow transients can also affect its finish. Dark infill may show through pale or translucent shells. These effects are documented in Prusa's comparable workflow. [Prusa wipe-to-infill and wipe-object guidance](https://help.prusa3d.com/article/wipe-tower_125010)

Use compatible materials and exclude precision or highly loaded regions from an unvalidated mixed-material route. A support polymer that separates readily from PLA can also weaken a PLA part if deposited inside it. Follow the [support-material guidance](supports-and-bridges.md#use-a-different-interface-material-when-it-earns-its-cost); retain its material-specific flushing requirements. Do not increase infill or add unwanted objects merely to absorb purge. Inspect both the total mass and the receiving part's function.

## Tune colour transitions with evidence

Treat each transition as directional: dark-to-light often needs more purge than the reverse, and additives or support materials change the requirement. Test the actual spool pair and hotend rather than importing another machine's volumes. [Prusa purge-matrix explanation](https://help.prusa3d.com/article/purging-volumes-mmu_125097)

In Bambu, begin with the matching presets and calculated flushing matrix. Trial small reductions, inspecting both transition directions. Prefer targeted matrix changes when only certain pairs allow reductions. Save the matrix first: **Re-calculate** replaces manual entries. A global multiplier affects every pair. [Bambu matrix and multiplier](https://wiki.bambulab.com/en/software/bambu-studio/reduce-wasting-during-filament-change)

Judge light surfaces under consistent lighting and check bonding when polymers differ. Record the spool identity, nozzle, settings, and tested directions. Do not interpret a visually clean transition as a measured strength result.

## Keep priming distinct from purging

Bambu's **Prime volume** controls tower extrusion used to stabilize pressure and collect residue; flushing clears the previous filament and may go to the chute or eligible object paths. Tower width, minimum footprint, and stability interact with its calculated depth. A smaller width alone does not establish an equivalent material saving. Inspect the sliced tower.

The ordinary multicolour tower reaches the last colour-change layer. **Smooth Mode** timelapse can require a tower even for a single-colour job and extends it to the tallest model. If smooth timelapse is unnecessary, compare the appropriate alternative/off setting and re-slice. **Rib Wall** offers a supported tower design to compare while retaining stability. Do not routinely disable priming to save filament. [Bambu prime-tower guide](https://wiki.bambulab.com/en/software/bambu-studio/parameter/prime-tower)

## Advanced options need their own small trial

- **No sparse layers:** Bambu Studio 2.8.2 documents this under **Others > Prime Tower** with Developer Mode enabled. It allows tower layers without changes to be skipped. It remains experimental, has model/tower placement requirements, and adds Z travel that can cause oozing or stringing. Inspect clearance throughout the motion and test before production. It is distinct from **Skip points**, which changes tower entry gaps. [Bambu 2.8.2 release notes](https://github.com/bambulab/BambuStudio/releases/tag/v02.08.02.60), [Skip points explanation](https://wiki.bambulab.com/en/software/bambu-studio/parameter/prime-tower)
- **Long retraction when cut (experimental):** installed Studio **02.08.02.61** labels it experimental and warns of clogging/printing problems; its tooltip calls for current printer firmware. Check effective printer and filament overrides and retain the matching P2S preset before considering a change. The installed P2S presets contain this control, but that does not establish reliable settings for the user's filament. Avoid universal retraction distances or custom tool-change G-code. Primary local evidence: `/Applications/BambuStudio.app/Contents/Resources/i18n/en/BambuStudio.mo` and `profiles/BBL/machine/Bambu Lab P2S 0.4 nozzle.json` under the same Resources directory. Recheck after software/profile updates.

Do not enable both experiments while also cutting purge aggressively. Establish each change's effect on colour, extrusion, and successful loading first; record results with the build.
