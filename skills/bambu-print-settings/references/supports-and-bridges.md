# Cleaner undersides, supports, and bridges

Guidance checked 2026-10-08. Choose the technique around the underside's function, visibility, span, and cleanup access. Read the [basic support rules](filament-and-reliability.md#first-layer-and-supports) for support types and separation gaps.

## Place supports deliberately

Consider a better orientation or a split before committing a critical presentation or mating face to supports. Where supports are needed, paint enforcers and blockers and inspect the generated result. In Bambu's auto modes, painted enforcers add to automatically generated supports; selecting manual mode changes that behavior. Painting vertical areas can also stabilize a tall, thin part, at the cost of contact marks. [Bambu support painting](https://wiki.bambulab.com/en/software/bambu-studio/support-painting)

Check that branches, bases, and removal tools can reach their contacts. A blocked support region still needs a printable overhang or bridge. For a broad underside, inspect whether the top interface forms a sufficiently continuous platform; extra interface layers may help, but removal and the Z gap still matter. [Bambu support settings](https://wiki.bambulab.com/en/software/bambu-studio/support)

## Reduce support material deliberately

Compare **Normal Snug** for close-fitting support, trees for isolated contacts, and **Tree Hybrid** for a mixture of broad and small overhangs. None is always lightest. Adjust base spacing separately from interface layers and spacing; a sparse base still needs to carry a sound contact platform. **Lightning** support-base infill saves material at a strength cost. **Support critical regions only** is a candidate for a representative overhang test, not proof that every remaining surface prints well. Inspect the generated branches and interfaces. [Bambu support controls](https://wiki.bambulab.com/en/software/bambu-studio/support)

Treat build-plate-only supports as a placement choice: avoiding contacts on the model can require longer branches. Compare total support mass, stability, removal access, and scars. Retain an adequate Z gap for same-material support. Use painted contacts and local brims where they solve the actual issue rather than shrinking all supports indiscriminately.

For repeated production with a suitable accessible overhang, a separately printed **reusable support insert** placed during a pause can be worth a trial. Prusa demonstrates the technique. It requires a tested release surface/material pair, accurate insertion height, stable retention, and clear nozzle travel; it is an advanced design option, not a drop-in PLA support preset. Count the insert and setup prints in the saving. [Prusa reusable-support example](https://blog.prusa3d.com/10-tips-for-saving-filament-money-and-environment_71415/)

Use [whole-build material accounting](material-efficiency.md) to check whether the change actually saves filament.

## Use a different interface material when it earns its cost

A compatible support interface can improve a visible underside when reorientation or splitting is undesirable. Verify that the installed equipment supports the required material changes. Prefer the selected support material's documented profile and use it at the interface where appropriate. Inspect the actual supported surface and a material-transition region in a small test before relying on a loaded part.

For most ordinary dedicated-support workflows, use the model material for the support core and the support filament only at the interface. For compatible single-polymer multicolour jobs, **Default** support-base filament can follow the current colour and avoid forced support-colour changes. Keep material-specific exceptions in the manufacturer's recipe. [Bambu support-material guidance](https://wiki.bambulab.com/en/software/bambu-studio/support)

On a single nozzle, foreign-material support throughout the height adds changes. Consider whether CAD can place supported shelves at shared heights to reduce those changes, without compromising function; that is a design hypothesis to compare by slicing.

Bambu's current mutual-support guide specifically covers **Bambu PLA Basic with Bambu PETG Basic or PETG HF**. It excludes the listed matte, silk, filled, translucent, and third-party variants from that recipe. It supplies **P2S-specific 3MF presets** because cooling differs. Read those presets before adapting them to the part; the general page also illustrates dual-nozzle equipment. The guide calls for ventilation through the door/top in this particular workflow, including P2S. This is a specific exception to ordinary P2S PLA enclosure guidance. [Bambu PLA/PETG mutual-support guide](https://wiki.bambulab.com/en/filament-acc/filament/h2d-pla-and-petg-mutual-support)

For a single-nozzle P2S, assess flushing, material contamination, and change count as part of the setup. Retain the material-specific flushing behavior; a visually clean color transition alone is not evidence of sound layer bonding. Do not flush an incompatible support material into structural model infill. Record additional time and filament only from the actual slice.

## Tune bridges for the defect and span

A bridge needs supported endpoints. Inspect the first bridge layer and choose a direction that spans the shorter supported distance where possible. An isolated circular perimeter starting in air is not made printable by changing a bridge speed. For a hole above a recess, consider the [counterbore techniques](../../pla-functional-design/references/structure-and-assembly.md#design-small-overhangs-and-cleanup-features).

Bambu's bridge guide distinguishes gaps between neighboring bridge strands from sagging. It demonstrates increasing **Bridge flow** to close strand gaps, followed by a **Bridge speed** comparison. **Thick bridges** can help longer spans yet worsen short-span underside finish. Treat those as separate trials with the production filament and span; neither lower flow nor the slowest speed is a universal improvement. Keep whole-filament flow ratio separate from this bridge-specific adjustment. [Bambu bridge-quality guide](https://wiki.bambulab.com/en/filament-acc/filament/print-quality/bridging)

Use a short bridge coupon with the same anchors, gap, and relevant cooling. Judge both its underside and the layers supported above it. If the span remains unreliable, add an accessible support, reduce the span in CAD, split the part, or select another orientation.

## Check interactions before saving the plate

Variable layer height has support and multi-material constraints. Bambu documents incompatibility with **Tree Organic** and restrictions on differing object layer profiles when a prime tower is needed. Check the installed version's actual slice and effective support style; use a compatible style or separate plate when required. [Bambu variable-layer-height limitations](https://wiki.bambulab.com/en/software/bambu-studio/adaptive-layer-height)

Preserve support painting, interface assignments, deliberate tilts, and any designed removal features when replacing geometry. Include cleanup instructions for sacrificial features with the part's normal assembly notes.
