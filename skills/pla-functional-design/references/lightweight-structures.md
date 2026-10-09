# Open frames, lattices, and thin shells

Guidance checked 2026-10-08. When a region does not need a continuous surface, actively consider removing it or replacing it with an open structure. Preserve the actual functions of the surface: containment, touch comfort, contact area, shielding, cleanability, appearance, and structural load transfer. These selection rules are engineering judgments informed by the linked sources, not tested P2S strength ratings.

## Choose structure and visual character together

| Structure | Useful candidate | Main design check |
| --- | --- | --- |
| Open frame with a few ribs or diagonal braces | Brackets, stands, dividers, connecting bodies | Connect the real attachment and loaded regions; account for bending, twist, and buckling. |
| Perforated or honeycomb panel | Ventilated trays, guards, dividers, broad side panels | Keep a continuous border and reinforced attachments; size openings for what must stay in or out. |
| Thin shell with ribs, beads, or corrugations | Trays and covers needing a continuous face | Put section depth where it resists the load; blend stiffeners into the rim and attachment regions. |
| Flowing leaf or other shaped openings | Open walls, sleeves, stands, and expressive enclosures | Coordinate the openings on the actual surface; preserve continuous webs, tip bridges, and transitions into solid interfaces. |
| Three-dimensional beam lattice | A volume needing distributed support or several load paths | Orient printable members, join every node, and retain access for any required support removal. |
| TPMS lattice such as a gyroid surface | Distributed compliance, flow paths, or a deliberately porous volume | Set printable sheet thickness and cell scale; verify continuity and load response in the chosen process. |
| Organic or Voronoi network | Deliberate appearance or locally varying cells | Check the smallest members and irregular nodes; an organic look does not establish structural optimization. |

nTop distinguishes beam, plate, honeycomb, and TPMS lattices and identifies cell geometry, size, and member thickness as design variables. Its examples span manufacturing processes; transfer the design vocabulary, not metal/resin performance claims, to our FDM builds. [nTop lattice guide](https://resources.ntop.com/resources/blog/guide-to-lattice-structures-in-additive-manufacturing/)

Use a simple frame, perforated panel, or ribbed shell as a useful functional baseline. Also consider a more expressive structure when appearance matters: the [Can Tower leaf lattice](form-and-pattern.md#can-tower-leaf-lattice-precedent) shows how flowing openings and shaped feet can define the object. Reconsider the silhouette and layout as well as the pattern inside an existing boundary. Weigh the visual benefit and functional performance against modeling, slicing, and print difficulty; minimum geometric complexity is not the only goal. Use [thermoforming](thermoforming.md) when a thin formed sheet or heated printed blank could replace a directly printed curved shell.

## Keep solid material at the interfaces

Mark regions to retain before generating openings: screw and washer seats, nut/insert pockets, bearing surfaces, mating datums, loaded roots, feet, latch roots, and hand-contact edges. Connect these through continuous members with broad, blended roots. Keep the pattern away from required tool access and assembly clearances.

Use local density or member thickness where it addresses a load, transitioning gradually to lighter regions. Avoid a thick boss attached to a lattice through a single tiny neck. When a panel carries bending, check its depth and rim as well as the open-area fraction; a visually attractive grid is not automatically stiff in the needed direction. Inspect both tension paths and slender members that may buckle.

For topology optimization, define preserved interfaces, obstacle/clearance regions, loads and restraints for all relevant use cases, and manufacturing constraints. Autodesk's additive setup explicitly includes build orientation, overhang angle, and minimum feature thickness. An OpenSCAD pattern or hand-shaped organic frame is a design proposal unless a solver was actually run; analysis also needs assumptions appropriate to layered PLA. [Autodesk additive constraints](https://help.autodesk.com/cloudhelp/ENU/Fusion-GenerativeDesign/files/GD-ADDITIVE-REF.htm), [preserving interfaces](https://help.autodesk.com/cloudhelp/2016/ENU/InventorLT-Help/files/GUID-A6F99E9C-B82A-4145-ABD4-2B1C69FFA99A.htm)

## Make the openings printable

- Consider printing a panel flat, or use angled openings and short anchored bridges for an upright panel. Choose against the service loads and surface requirements as well as support volume.
- Parameterize member width, member depth, cell pitch, border width, root blends, and retained regions independently. Density alone does not specify a usable structure.
- At each critical slice, check that loaded members contain adequate continuous extrusion paths. A feature surviving as one narrow path is not evidence that it can carry the load. Use the actual nozzle, line widths, wall generator, and layer height.
- Join cells and frames with real overlapping solids; remove disconnected fragments, tangent-only contacts, tiny slivers, and unsupported starts. Round handling edges without turning printable undersides into difficult overhangs.
- Inspect the first layer and every change in topology. Avoid enclosed supports and places where strings or broken branches cannot be removed. A large network may trade reduced mass for more travel, starts, and fragile details.

For a common OpenSCAD construction, consult [BOSL2 structural modules](mechanism-libraries.md#lightweight-walls-and-panels). Check the pinned version's angle convention: BOSL2's documented `maxang` is measured from vertical, while Bambu's support threshold is referenced to horizontal. Neither default establishes the overhang limit of our filament and profile.

## Compare against the actual baseline

Compare a closed shell with sparse infill, a simpler frame or ribbed shell, and a lattice only where each is plausible. Use the same required function, external constraints, and quantities. New openings introduce perimeter paths; lower CAD volume does not guarantee lower printed mass. Compare sliced mass including supports, time, cleanup, stiffness, and attachment behavior. See [material efficiency](../../bambu-print-settings/references/material-efficiency.md).

Use a representative sample containing several cells, an edge, and a real node or attachment. A lone cell misses boundary behavior. Check deformation under a relevant load and repeat handling where relevant; keep any load capacity unverified until measured. Show labelled alternatives and highlight retained solid regions using [build communication](../../print-build-communication/SKILL.md).

Distinguish **CAD lattice geometry** from **exposed slicer infill**. Slicer infill becomes part of the manufactured shape only through its effective settings; retain the native project and inspect the resulting toolpaths. Read the [exposed-infill guidance](../../bambu-print-settings/references/material-efficiency.md#exposed-infill-and-open-structures) before using it as a finished surface.
