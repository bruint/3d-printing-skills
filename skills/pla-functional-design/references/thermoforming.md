# Thin parts made by forming

Guidance checked 2026-10-08. Consider forming when a thin curved shell can provide the required function with less material or support than direct printing. Confirm the available heating, forming, clamping, and trimming equipment before choosing a production workflow. The user's usual P2S/PLA setup does not establish that a thermoforming machine or heat-resistant tooling material is available.

## Choose between two processes

**Form purchased sheet over a tool.** Heat a thermoplastic sheet, then form it over or into a mould using the chosen vacuum, pressure, or mechanical process. Useful candidates include shallow covers, trays, liners, and panels. A printed tool may be reusable across a batch. The printed tool and final sheet are separate materials and deliverables. [Formlabs thermoforming overview](https://formlabs.com/global/white-papers/low-volume-rapid-thermoforming-with-3d-printed-molds/)

**Print a flat blank, then heat and shape it.** Candidate blanks can contain designed openings, local thickness changes, and locating features. This may avoid supports for a curved part, but does not guarantee a lower final mass. Research demonstrates flat-printed PLA parts being heated, formed, cooled, and mechanically tested. Treat that as feasibility evidence; the specimen results do not establish our forming temperature, strength, or long-term stability. [Printed-PLA thermoforming research](https://pmc.ncbi.nlm.nih.gov/articles/PMC10305231/)

Prefer a jig for controlled geometry. Heating above the material's softening region allows movement, but can also alter dimensions and mechanical behavior. Validate temperature, dwell, bending force, cooling restraint, and springback on the actual filament and blank. Recheck fit and load response after forming; distinguish reshaping from a validated annealing process. Do not promise increased heat resistance from forming alone.

## Design a formable part and removable tool

- Choose which face is the dimensional reference. The mould-contact face and opposite face differ by a wall thickness that changes during drawing.
- Provide draft and a release direction. Treat undercuts as a tool-removal problem: remove them, change the split, or design a multipart tool. Use mould-specific guidance rather than a universal draft angle.
- Prefer generous transitions and manageable draw depth. Stretching thins the sheet, especially around difficult geometry; initial sheet thickness is not the minimum final thickness.
- For vacuum forming, connect pockets and last-contact areas to a working air path. Place vents where their marks are acceptable. Include a clamping margin, a trim line, and access for trimming and later assembly.

These rules follow Formlabs' draft, venting, corner, and draw-ratio guidance. Its resin printing dimensions and curing procedures are not FDM presets. A surface-area draw ratio is an early planning estimate, not proof of uniform final thickness. [Vacuum-forming design guide](https://formlabs.com/blog/prototyping-vacuum-forming/)

For a formed printed blank, simpler bends are easier to control than compound curvature requiring stretching or compression. Keep precision fits out of highly strained regions where possible, and plan any final drilling or trimming after forming. A perforated blank changes cell shape as it bends; verify that nodes, narrow ligaments, and boundary edges remain intact. These are design checks to test, not a universal forming recipe.

## Keep the tool light enough and stiff enough

A hollow or ribbed tool can reduce material while supporting the forming surface. Keep connected air passages when vacuum is required; separate the intentional vacuum route from leaks at the platen or joints. Do not assume ordinary Bambu skin and infill settings reproduce the controlled porosity of an industrial FDM process.

Account for pressure, heat buildup over repeated cycles, surface finish transfer, attachment loads, and cooling. Stratasys' FDM guide shows that cap surfaces can deform into sparse internal cells under hot-sheet pressure, and that tested performance depends strongly on tool material, sheet, and cycle conditions. Its PC/ULTEM results do not qualify an ordinary PLA tool. [Stratasys FDM thermoforming guide](https://www.stratasys.com/en/resources/resource-guides/fdm-thermoforming/)

Choose tool material from the actual sheet temperature, contact time, pressure, and cycle count. For a PLA-only setup, retain heat-sensitive tooling as an unverified candidate until a small representative forming test proves adequate. A different tool material or fabrication method may be needed.

## Count the process and preserve the files

Compare direct printing against **tool and jig material + all sheet blanks or printed blanks + setup trials and failures** for the required quantity. Count sheet clamping margins and trimmed scrap, as well as support savings and tool reuse. A mould made for one part can cost more material than direct printing.

Keep separately named, revision-linked files for the final formed shape, printed flat blank when used, mould/jig components, and trim/drill templates. Show print and forming orientations separately. Label tooling plates so they are not confused with final product parts. Record sheet/filament identity, thickness, forming settings, cooling method, and measured results. Only report rendered, sliced, formed, or tested states when actually verified.
