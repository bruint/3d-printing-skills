# Mechanism libraries and references

Reviewed 2026-10-08 for the user's OpenSCAD and FDM workflow. Use these selectively when a build needs a joint, hinge, transmission, guided motion, or flexure. Recommendations below are our selection judgments; linked documentation describes the upstream projects.

## Reusable OpenSCAD components

**BOSL2 — first choice for a local general-purpose library.** It includes functional parts and tools for constructing and attaching geometry. The project declares BSD-2-Clause licensing, requires OpenSCAD 2021.01 or later, and still labels itself beta. Keep a known revision for reproducible builds. [Repository and installation guidance](https://github.com/BelfrySCAD/BOSL2), [license](https://github.com/BelfrySCAD/BOSL2/blob/master/LICENSE)

Choose the relevant documented file:

| Need | BOSL2 starting point |
| --- | --- |
| Sliding dovetails, snap pins, tension clips, indexed face joints | [joiners.scad](https://github.com/BelfrySCAD/BOSL2/wiki/joiners.scad): `dovetail`, `snap_pin`, `rabbit_clip`, `hirth` |
| Pinned or print-in-place hinges, folding hinges, snap locks | [hinges.scad](https://github.com/BelfrySCAD/BOSL2/wiki/hinges.scad) |
| Gear geometry | [gears.scad](https://github.com/BelfrySCAD/BOSL2/wiki/gears.scad) |
| Threaded connections and fastener geometry | `threading.scad` and `screws.scad`, through the [documentation index](https://github.com/BelfrySCAD/BOSL2/wiki) |
| Guided sliding parts | `sliders.scad`, through the [documentation index](https://github.com/BelfrySCAD/BOSL2/wiki) |

Read the relevant module's current source comments or matching documentation before calling it. Do not guess signatures from BOSL v1 or examples from another BOSL2 revision. Check how each module applies clearance: parameters such as `$slop`, gaps, and diameters do not necessarily express the same physical allowance. Include only the needed modules and their documented prerequisites.

**NopSCADlib — useful for assemblies with purchased hardware.** It supplies models of bearings, fasteners, motors, belts, inserts, and other nonprinted components, plus printable parts including hinges, latches, and pulleys. Its framework can generate parts lists, exports, exploded views, and assembly instructions. Add it when those capabilities justify the dependency; confirm supplier dimensions for critical interfaces. A modeled purchased part is not automatically a design for printing its replacement. The repository declares GPL-3.0. [Repository and catalog](https://github.com/nophead/NopSCADlib), [usage guide](https://github.com/nophead/NopSCADlib/blob/master/docs/usage.md)

**MCAD — an existing fallback.** It provides mechanical components such as gears, motors, and bearing models. The repository declares LGPL-2.1, with some files offering additional permissions. It was present in this Mac's OpenSCAD application bundle when checked; recheck availability before depending on that location. Prefer an existing project dependency where it already does the job. [MCAD repository](https://github.com/openscad/MCAD)

## Lightweight walls and panels

BOSL2's [walls.scad](https://github.com/BelfrySCAD/BOSL2/wiki/walls.scad) provides `sparse_wall`, `sparse_wall2d`, `sparse_cuboid`, `hex_panel`, and `corrugated_wall`. Use them as candidates for cross-braced frames, honeycomb panels, and thin corrugated structures. The documentation specifies `std.scad` and `walls.scad` includes; verify signatures against the revision actually used.

Check member dimensions, border connections, print orientation, and the meaning of `maxang` and `max_bridge`. These are geometry controls, not guarantees of support-free printing or strength. In the reviewed documentation, `maxang` is measured down from vertical. Keep mounting regions and solid interfaces under project control. Follow [lightweight-structure design](lightweight-structures.md) before selecting a pattern. Referencing these modules does not mean BOSL2 is installed locally; check before using it.

## Design references for compliant motion

**OpenFlexure — study a complete working flexure design.** Its microscope uses a printed flexure stage and provides editable OpenSCAD source. Use it to study constrained movement, actuation, and integration of flexible and stiff regions. It is a complete instrument project, so select the relevant mechanism rather than importing its whole build system. The current repository declares CERN-OHL-S-2.0 or later; preserve the applicable source license when reusing design files. [Mechanism overview](https://openflexure.org/projects/microscope/), [current source repository](https://gitlab.com/openflexure/openflexure-microscope)

**BYU Compliant Mechanisms Research — reference collection.** Its maker resources link to printable compliant pliers, flexural pivots, beam segments, folding structures, and other examples. The FlexLinks collection is particularly useful for exploring compliant segments. Consult the individual author's model page for the available source formats, printing guidance, and license; the collection is not a single uniformly licensed OpenSCAD package. [BYU maker resources](https://compliantmechanisms.byu.edu/maker-resources)

## Use a library component in a build

- Start with the required motion, travel, load, retention, access, and expected number of cycles. Select the mechanism accordingly. Decide whether it prints assembled, uses separate printed pieces, or needs hardware.
- Keep reusable upstream code separate from project adaptations. Record its repository, revision, license, local include path, and required OpenSCAD version with the build. Pin or vendor a known revision when adopting a dependency; avoid silently changing old projects through a global library update. Use the project-organization skill's existing file conventions.
- Render a minimal instance with the installed OpenSCAD version before integrating it. Then inspect the integrated motion range for interference, stops, assembly access, and support removal. A successful render establishes geometry generation, not mechanical performance.
- Make a small representative coupon in the intended material, orientation, and settings. Validate clearance, retention, actuation force, and relevant repeated motion. In PLA, distinguish a hinge intended to fold during assembly from one expected to flex repeatedly or hold a sustained deflection. A library's example values do not establish fatigue life or load capacity for our build.

Local libraries save implementation work; design references inform mechanism selection. Keep fit and print results tied to the actual component revision and process so successful examples become evidence for later builds.
