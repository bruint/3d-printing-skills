# Structure and assembly for FDM parts

Guidance checked on 2026-10-08. These are engineering decisions informed by the linked manufacturer guidance and first-hand experiments. Their examples support the principles; they do not establish strength ratings, universal clearances, or tested dimensions for the user's P2S and PLA.

## Choose orientation against the actual loads

Consider installation, normal use, handling, and removal. A bracket that resists its service load can still split when a fastener wedges its layers apart. Identify the likely tensile side of each bend and the roots, holes, and joints where loads concentrate. Compare plausible orientations against those loads, then consider supports, fit surfaces, bed contact, and finish.

For loads in several directions, consider splitting the assembly so each piece has a useful layer orientation. Tilting a part can redistribute its weak direction, but adds support, surface, and stability costs. CNC Kitchen's experiments show that the benefit depends on geometry and load case, including a hook that did not improve when tilted. Do not prescribe 45° or the largest flat face as a universal solution. [CNC Kitchen orientation experiments](https://www.cnckitchen.com/blog/stop-printing-flat-the-45-secret-for-stronger-parts)

## Connect the structure to the load path

Use ribs or gussets to connect a loaded feature back to its supports. Give them broad roots and gradual transitions; end them where the load can spread into the surrounding shell. A rib disconnected from the force path adds material with little benefit. Preserve room for the actual wall toolpaths around roots and holes, and inspect those sections after slicing.

Separate minimum printable thickness from adequate structural thickness. A thin feature appearing in the mesh does not establish that it prints continuously or carries the intended load. Small upright pins deserve particular attention at their roots; a larger blended base, different orientation, separately printed pin, or metal pin may suit the job better. [Protolabs FDM design guidance](https://www.hubs.com/knowledge-base/how-design-parts-fdm-3d-printing/)

## Split where assembly remains practical

Use a split to gain orientation, support access, surface quality, replaceability, or bed fit. Account for the joint's load transfer, hardware, alignment, and assembly access before adopting it. Place the joint away from a highly stressed root where practical. Use locating features to establish position and suitable retention to carry the load; a locating peg is not automatically a structural fastener.

Include lead-ins, alignment features, and an obvious assembly direction. [Prusa modeling guide](https://help.prusa3d.com/article/modeling-with-3d-printing-in-mind_164135) For these builds, use keyed geometry where assembly could be confused, and keep assembly views distinct from print orientations.

## Design fasteners and access together

Choose through-bolts with nuts, captured nuts, threaded inserts, or printed threads according to load, access, and expected disassembly. Metal threads are useful for repeated assembly. For a heat-set insert, use the actual insert supplier's hole and installation dimensions; an M3 thread designation alone does not specify its outer body. Leave enough surrounding material and space for the installation tool. Make nut pockets reachable during the planned assembly sequence. [Formlabs thread and insert guide](https://formlabs.com/blog/adding-screw-threads-3d-printed-parts/)

Provide broad bearing areas around screw heads and nuts, with washers where useful. Consider how tightening loads reach the rest of the part. Countersunk heads apply a wedging load: use them deliberately, or choose a flat bearing surface when splitting is a concern. Preserve driver access after the neighboring pieces are fitted. [CNC Kitchen's fastener example](https://www.cnckitchen.com/blog/stop-printing-flat-the-45-secret-for-stronger-parts)

## Make fits adjustable and testable

Keep nominal mating dimensions, clearance, and any measured compensation separate in the model. State whether a clearance is per side, radial, or diametral. Define fits by purpose: locating, sliding, rotating, removable retention, or interference. Use a short coupon with the production orientation, wall structure, material, and relevant surface conditions. Record the tested combination; a fit result from another orientation or revision is evidence to consider, not proof of the new fit.

For snaps, allow travel and root relief, orient the flexure deliberately, and avoid leaving ordinary PLA permanently bent to retain a sustained load. For print-in-place mechanisms, check lateral gaps and vertical separation in the actual toolpaths, including first-layer expansion, bridging, and trapped supports. Calibrate clearances to the geometry and process. [Prusa tolerance guidance](https://help.prusa3d.com/article/modeling-with-3d-printing-in-mind_164135)

## Shape surfaces for their print orientation

Keep critical mating surfaces accessible and account for support scars. Use a chamfer or other printable transition where a bed-facing fillet creates a difficult overhang. Consider reorienting a critical hole or changing its unsupported roof; a teardrop or chamfer is suitable only if the functional contact still works. Do not change a precision bearing seat's shape merely to avoid supports. [Prusa fillet and chamfer guidance](https://help.prusa3d.com/article/modeling-with-3d-printing-in-mind_164135), [Protolabs hole and overhang guidance](https://www.hubs.com/knowledge-base/how-design-parts-fdm-3d-printing/)

## Design small overhangs and cleanup features

For a downward-facing counterbore whose smaller hole would start in air, consider either a **one-print-layer sacrificial membrane** across the recess, removed after printing, or **successive short bridges in perpendicular directions** that leave the through-hole open. The latter changes the recess roof; retain the required screw-head clearance and bearing surface. Rahix documents printed examples of both approaches. [Counterbore and sacrificial-layer examples](https://blog.rahix.de/design-for-3d-printing/)

Tie layer-sized features to the intended print orientation and actual sliced heights. Variable layer height, a new first-layer height, rotation, or mesh replacement can invalidate them. Preview every transition, ensure the bridges have anchors, and verify removal access before making a membrane part of the deliverable. Label the intended cleanup in assembly notes so it is not mistaken for a blocked hole.

Where a small overhang or a tall, delicate feature still needs support, consider a designed breakaway tab or brace with contacts in accessible, noncritical areas. Keep it parameterized and distinguish it from the finished part. Compare it with slicer support painting; the removal scar and force must be acceptable for the nearby feature. This is an engineering application of Prusa's guidance on modeling removable supports. [Prusa modeling guidance](https://help.prusa3d.com/article/modeling-with-3d-printing-in-mind_164135)

## Design for material efficiency

If a solid appearance or continuous surface is unnecessary, compare an [open frame, perforated panel, lattice, or ribbed shell](lightweight-structures.md) as part of the design. For thin curved parts, also consider [forming a sheet or printed blank](thermoforming.md) when the equipment and material permit it.

Preserve the required load path while comparing shells, ribs, and local reinforcement. Reducing solid CAD volume does not necessarily reduce printed mass: cutouts introduce new perimeters, and thin webs can become almost solid. Rahix demonstrates how a simpler closed section with sparse infill can compare favourably with an I-section. Use this as a reason to compare actual slices, not a universal prohibition on holes or ribs. [Rahix cross-section examples](https://blog.rahix.de/design-for-3d-printing/)

Prioritize printable chamfers, anchored short bridges, and the removable features described above before accepting large support volumes. A split must earn its extra joint, surrounding walls, assembly work, and possible alignment error. Keep critical roots, fastener bearing surfaces, and required skins intact. Apply [material accounting](../../bambu-print-settings/references/material-efficiency.md) to the complete assembly.

Where colour is decorative, consider keyed inserts, badges, or separate panels printed in colour-specific jobs. Compare them with raised colour-by-height detail or a shallow inlaid face. Keep retained inserts accessible to assemble, provide testable fits, and preserve their independent finish orientation. Consult [multicolour design choices](../../bambu-print-settings/references/multicolour-and-purge.md#choose-how-the-colours-become-part-of-the-build) before committing to repeated colour changes throughout a tall model.

## Export curves at useful resolution

Check the exported mesh's silhouette and critical holes at the intended scale. A faceted cylinder or coarse curve in the mesh calls for a CAD/export change. In OpenSCAD, use suitable `$fa`/`$fs` values or a deliberate local `$fn`; a nonzero `$fn` overrides `$fa` and `$fs`. Use enough facets for the part's visible curvature and fit without making every small feature needlessly dense. [OpenSCAD resolution controls](https://files.openscad.org/documentation/manual/Other_Language_Features.html)

Separate a lightweight preview from the final export when useful, and ensure production exports actually use the final resolution. If simplifying an imported mesh, compare silhouettes, small features, and mating dimensions before accepting it; simplification can remove meaningful geometry. [Bambu mesh simplification](https://wiki.bambulab.com/en/software/bambu-studio/simplify-model)
