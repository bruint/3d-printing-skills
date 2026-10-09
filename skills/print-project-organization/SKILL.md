---
name: print-project-organization
description: Organize 3D-printing projects, editable CAD or OpenSCAD source, exported parts, revisions, and Bambu Studio plates. Apply when creating or revising print-build deliverables, preparing multi-part assemblies or print packs, and arranging test and production plates.
---

# Print project organization

Make it clear what to edit, what to print, how many of each part are needed, and which files belong together. Apply this as part of producing a printable build, without requiring a separate request for file organization. Match the project's scale and preserve useful existing conventions.

## Keep the authoritative files clear

- Keep one identifiable editable source for each design or assembly, including the parameters needed to reproduce its variants. In OpenSCAD, share geometry and interface dimensions between assembly views, printable-part modes, and coupons. Separate the assembly position from each part's print orientation.
- Treat imported originals as inputs and preserve their provenance and any supplied licensing information. Identify modified derivatives. Export one file per independently printable part or intentional multipart print unit, in its intended print orientation where practical. Preserve the relative positions of captive or print-in-place components. Keep assembly previews out of the production mesh set.
- Keep geometry exports and saved Bambu projects traceable to the source revision. A Bambu project is a saved preparation of meshes and settings; editing the CAD does not automatically refresh it. Distinguish the native project `.3mf`, a geometry-only `.3mf` or STL, and derived sliced output such as `.gcode.3mf`. Check contents and how Studio opens the file; the extension alone does not prove readiness.
- A small build can stay flat. For a larger project, use the existing layout or consider `inputs/`, `exports/`, `bambu/`, and `previews/`, with a short root `README.md`. Add `archive/` for superseded releases or `validation/` for useful checks when needed. Create only directories that contain useful work. Add an export script when repeated variants justify it, and say which steps it actually performs.
- For a [formed build](../pla-functional-design/references/thermoforming.md#count-the-process-and-preserve-the-files), distinguish the finished shape, flat blank, mould/jig, and trimming aids; mark tooling separately from final parts. For exposed slicer infill, keep the native project and effective settings as part of the design, since the geometry-only export omits the manufactured open structure.

## Name parts and revisions consistently

Use stable, descriptive part names across CAD export modes, mesh filenames, the Bambu object list, and the parts list. Include meaningful distinctions such as left/right, size, fit variant, or revision; label alternatives as alternatives. Avoid ambiguous names such as `final-final`.

For design discussions, use [print build communication](../print-build-communication/SKILL.md). Keep its labelled previews and feature-callout mapping with the build so the user's image references remain meaningful across revisions.

Make the current printable revision explicit. Keep superseded or incompatible sets separate from current print files while retaining useful tested versions. Record mating compatibility when an interface changes; unchanged parts may retain their own revision. For a published print pack, identify the matching source, mesh, and Bambu project versions. Use a small table or existing version control rather than adding a release system to every small build.

## Plan the plates as print jobs

Read [Bambu plate planning](references/bambu-plates.md) when arranging or saving plates. Prefer one native multi-plate project for a compatible build or subassembly. Use separate projects for configurations that cannot coexist reliably, or when existing project conventions make separate test and production files clearer.

Name plates by purpose, such as `01-fit-test`, `02-base-PLA`, or `03-connectors-x8`. Group parts by compatible process and material requirements, then by assembly or replacement use. Put uncertain fits or finish techniques on a small test plate before committing to a large batch. Use the [quality comparison workflow](../bambu-print-settings/references/quality-workflow.md#make-the-comparison-representative) to keep variants labelled and representative of the production layout. Keep alternatives and optional spares identifiable so printing all production plates yields the intended set.

Record each plate's contents, part counts, required repeats, and purpose. Count only printable instances; modifiers, reference geometry, and disabled objects are not physical parts. Preserve selected orientation and multipart relationships when arranging.

For full builds, use the [material and colour plate plan](references/bambu-plates.md#plan-colour-and-material-efficiency). Compare total filament for the required quantities, including supports, flushing, and towers. Preserve colour-change alignment and any validated purge settings when arranging or revising a batch.

## Keep revisions and delivered files in sync

When geometry changes, update the affected exports and replace their geometry in the Bambu project, retaining deliberate settings where compatible. Recheck placement, quantities, modifiers, support or color painting, and fit-test relevance. Slice affected plates again. If a tool is unavailable, mark the remaining preparation step explicitly and identify the usable files; do not present an old slice as current.

Open the delivered project through available Bambu tooling and verify its plates, parts, scale, settings, and slice state. A valid ZIP/XML package alone does not demonstrate that the project loads or prints. Report **exported**, **opened**, **sliced**, and **physically tested** only when each is supported by evidence.

The README should lead with the current file to open, the first plate to print, quantities and assembly order, consequential print settings, and known fit results. For useful comparison prints, retain the tested material/setup, changed parameters, observed appearance or fit, and labelled photos with the build notes. Include source/export instructions when useful. Report time and material from an actual slice and keep implementation logs out of the normal printing instructions.

For geometry and joints, use [PLA functional design](../pla-functional-design/SKILL.md) when relevant. For profile choices and tuning, use [Bambu print settings](../bambu-print-settings/SKILL.md). An organization-only task need not revisit proven geometry or settings.
