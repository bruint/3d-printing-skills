---
name: pla-functional-design
description: Design or revise functional FDM parts and assemblies for PLA on a Bambu P2S, balancing load paths, joints, visual character, printability, and material use. Use for functional CAD and OpenSCAD work, including expressive open structures, lattices, ribbed shells, and forming-aware designs.
---

# PLA functional design

Make the load path, print orientation, and user-facing shape work together. Preserve the user's required fit and function while changing structure or appearance. Read [P2S and PLA reference](references/p2s-pla.md) when printer limits, filament behavior, or slicer choices affect the design.

Use [print build communication](../print-build-communication/SKILL.md) for spatial explanations and design feedback. Lead with labelled views the user can point to, retaining callout identities when the geometry changes.

Apply [Bambu print settings](../bambu-print-settings/SKILL.md) alongside this skill for parts we create or revise for printing. Consider the intended slicing choices while selecting orientation and shaping the part; use the user's P2S/PLA context unless the build specifies otherwise. Include the resulting print setup as part of the build deliverable without requiring a separate request for printing advice.

## Design decisions

Read [structure and assembly](references/structure-and-assembly.md) when a build involves multiple load directions, splitting parts, fasteners, mating joints, moving features, support-saving geometry, material efficiency, or export resolution. Apply the relevant decisions during design, before producing the final meshes and plates.

For a full build, consider [material-efficient geometry](references/structure-and-assembly.md#design-for-material-efficiency), including sensible colour inserts and support-free features. Compare complete sliced material use before claiming that a lighter-looking CAD shape saves filament.

When a region need not look solid or provide a continuous barrier, actively consider [open frames, lattices, and thin shells](references/lightweight-structures.md). Preserve functional contacts and load paths. For heating and shaping a printed blank, or forming sheet over a printed tool, read [thermoforming](references/thermoforming.md); verify the actual material and equipment instead of assuming PLA is suitable tooling.

For a common joint or mechanism, consult [mechanism libraries and references](references/mechanism-libraries.md) before designing it from scratch. Prefer a suitable documented component, adapted to the build's loads, material, and print process; verify the API and behavior of the version actually used.

1. Identify where weight, clamp force, and handling loads enter the part, the supports they reach, and likely crack starts. Use a simple bending or shear estimate for critical cantilevers. Treat calculations as screening estimates; printed parts need a physical fit and load check.
2. Choose print orientation before refining details. Keep the primary tensile or bending path in continuous deposited roads where practical. Split a part when that gives each section a stronger orientation, cleaner mating surface, or a reliable fit on the P2S. Check the oriented bounding box, including room for a brim.
3. Put material at the load path: continuous outer walls, broad roots, tapered ribs or gussets, and enough thickness for several extrusion lines. Add local thickness around holes, nuts, and clamp roots. Prioritize wall loops and local reinforcement over indiscriminate high infill.
4. Replace abrupt inside corners with generous transitions. Use radiused corners, swept ribs, and tapered sections to create a softer shape that also reduces stress concentration. Use shallow scallops or finger notches in low-stress areas for access and visual rhythm. Do not remove material from a critical root merely for appearance.
5. On presentation and touch surfaces, consider a consistent small chamfer, bevel, or corner radius to soften the silhouette. Apply it selectively: keep mating faces, dimensional datums, and load-bearing contact patches flat unless a transition is needed for fit or strength. Use a related radius family rather than a different treatment on every edge.
6. Judge every curve in print orientation. A round underside facing the bed can create a severe overhang; use a chamfer, teardrop, split, or support when it prints better. Keep mating dimensions and clearance surfaces simple and adjustable. Verify thin details in the slicer's toolpath preview.
7. For sustained loads in PLA, avoid relying on a permanently flexed snap fit or excessive screw preload. Use captured nuts, bolts, broad contact pads, and multiple load paths when suitable. Account for warmth near sunlit windows or electronics.

## Form, character, and surface finish

- Treat aesthetic character as a legitimate design goal alongside fit, strength, and material use. Explore the silhouette, arrangement of members, curvature, and negative space together. A different footprint or structural layout may serve the same function more attractively; preserve the required interfaces and constraints while exploring it.
- Read [form and pattern, including the Can Tower leaf lattice](references/form-and-pattern.md) when choosing an expressive structure. Carry forward the precedent's flowing openings, coherent transitions, and integration of pattern with form. Adapt the vocabulary to the new build; botanical, geometric, folded, or sculptural approaches are all available.
- Give the shape a coherent visual language through related curves, taper, rhythm, and deliberate changes of scale or density. Exposed reinforcement and decorative shaping can contribute to that language. Judge the overall composition and the small printed details together, allowing complexity when it adds worthwhile character.
- For small curved presentation inserts, compare a roughly 45° tilt with flat printing independently of the main body. Use the [curved-insert finish guidance](../bambu-print-settings/references/fit-and-finish.md#curved-inserts-and-orientation) to balance appearance, support placement, and mating fit.
- Treat the build plate as a finishing tool. A textured PEI plate transfers its texture to the *first-layer contact face only*. Put a broad, flat presentation face on the plate when that orientation also satisfies strength, overhang, and fit needs. Preview seams, supports, and brim placement; a texture cannot hide those artifacts or make a side wall look like the first layer.
- Keep textured-bed contact off tight mating surfaces when its first-layer shape could alter fit. Choose texture and colour contrast to support the intended composition. Read the [P2S and PLA reference](references/p2s-pla.md) for plate-specific sources.

## Deliverable check

Use [print project organization](../print-project-organization/SKILL.md) when producing or updating the build's files and plates. Provide the editable source and a concise explanation of load path, orientation, fit adjustments, and the visible shaping choices. Record the build-specific print setup alongside the source and printable files using the project's existing documentation conventions; explain the settings that matter for this geometry and identify any untested assumptions. Render or otherwise validate the solid, check that each printable piece fits the P2S, and use a small fit coupon before committing to a large print when mating geometry is uncertain. State any unmeasured load capacity as unverified rather than a rating.
