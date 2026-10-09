# Filament and reliability

Guidance checked 2026-10-08. Use the actual filament and printer profiles; numeric limits from another hotend or PLA blend are not transferable.

## Filament condition before tuning

For appearance-critical prints with uncertain filament storage, or new bubbles, pits, rough extrusion, or stringing, check moisture before compensating with retraction or flow. Dry according to the actual filament and drying equipment guidance, then keep it sealed. A bed setpoint, forced-air dryer setpoint, and AMS drying setting are different methods; do not copy a temperature between them or assume all AMS models provide active drying. Check spool temperature limits as well. [Bambu filament-drying recommendations](https://wiki.bambulab.com/en/filament-acc/filament/dry-filament)

## Three different flow controls

| Control | What it addresses | Practical decision |
| --- | --- | --- |
| **Flow ratio / Flow Rate calibration** | Overall deposited amount; persistent gaps or ridges. | Check dry filament and a sound nozzle before calibrating. Do not use XY compensation to conceal over-extrusion. |
| **Flow Dynamics / pressure compensation** | Extrusion response during speed changes, including corner bulges or gaps. | Use the printer's supported calibration workflow after a relevant filament, nozzle, temperature, or flow-limit change. |
| **Max volumetric speed** | Sustainable material throughput, in mm³/s. | Retain the matching filament limit until a throughput test justifies changing it. A higher requested travel/print speed does not increase melt capacity. |

[Bambu Flow Rate calibration](https://wiki.bambulab.com/en/software/bambu-studio/calibration_flow_rate), [Bambu Flow Dynamics calibration](https://wiki.bambulab.com/en/software/bambu-studio/calibration_pa), [Prusa's explanation of volumetric limits](https://help.prusa3d.com/article/max-volumetric-speed_127176).

For a rough check, `flow ≈ line width × layer height × print speed`. Thus 0.45 × 0.20 × 150 is about **13.5 mm³/s**. The slicer's extrusion-area model is more precise; use its flow preview to verify. Wider lines and thicker layers can hit the flow limit sooner. A visually acceptable maximum is not proof of adequate bonding for a loaded part.

**P2S distinction:** it supports automatic Flow Dynamics calibration. Do not infer automatic flow-ratio or maximum-throughput calibration from that feature, or substitute P1-series limitations. Verify which calibration the current firmware/UI offers and whether the chosen pre-print mode reuses or overrides saved results. [Bambu Flow Dynamics guide, P2S section](https://wiki.bambulab.com/en/software/bambu-studio/calibration_pa#h2dh2sp2sx2d-printer).

## Cooling and speed

Retain the matched filament preset's cooling as the starting point. Small tips and overhangs can need more cooling or time even when broad walls print well. Minimum layer time, minimum print speed, and overhang rules interact; the requested speed is not necessarily the sliced speed. Keep dedicated overhang/bridge cooling unless there is a specific reason to change it. [Bambu cooling settings](https://wiki.bambulab.com/en/software/bambu-studio/auto-cooling).

For small features that remain hot despite slowing down, compare several useful copies spaced apart in **by-layer** mode so the nozzle leaves each part between layers. This can improve tips and overhangs, but adds travel and may increase stringing. By-object printing does not give the same between-object cooling benefit. Validate the intended production arrangement; a crowded test plate can hide overheating that returns when printing one part alone. [Ellis' cooling and layer-time experiments](https://ellis3dp.com/Print-Tuning-Guide/articles/cooling_and_layer_times.html)

For a weak or separating functional print, inspect orientation, extrusion, temperature, speed, and cooling together; do not treat more fan or slower speed as universal fixes. Stay within the material/nozzle guidance and compare a representative specimen when changing thermal conditions.

The **P2S Adaptive Airflow System** admits outside air for low-temperature filaments, and Bambu describes printing them with the door closed. Do not impose older P1S/X1 enclosure advice as a P2S requirement. Follow the current P2S profile and investigate actual heat or warping symptoms; door position is a contextual adjustment. Check which fan a control actually operates rather than assuming part, auxiliary, chamber, and adaptive-airflow controls are interchangeable. [Bambu P2S introduction](https://blog.bambulab.com/the-icon-redefined-meet-the-p2s-a-completely-reengineered-version-of-the-ultra-productive-p1-series/).

For PLA/PETG mutual-support jobs, consult the [specific P2S recipe and enclosure exception](supports-and-bridges.md#use-a-different-interface-material-when-it-earns-its-cost) instead of extending ordinary PLA guidance to that higher-temperature workflow.

## First layer and supports

For lifting or poor first-layer adhesion, check the correct plate selection, plate-specific cleaning and temperature, nozzle condition, and leveling before increasing heat or adding material. A brim is useful for a narrow footprint or lifting corners; account for removal and dimensional cleanup. Use the actual plate manufacturer's adhesive/release-agent guidance rather than applying glue to every plate by default.

If only sharp corners need extra adhesion, trial **painted brim ears** rather than adding brim around every edge. Inspect the first layer to confirm contact and removal clearance; brim gap and elephant-foot compensation interact. Use per-object brims for tall or narrow pieces as needed. [Bambu brim guide](https://wiki.bambulab.com/en/software/bambu-studio/auto-brim)

Choose **normal/snug or hybrid supports** for broad flat undersides and consider **tree supports** for isolated or organic overhangs. Inspect contact locations and whether supports can be removed. For the **same material** in model and interface, retain a nonzero Top Z distance: less gap improves underside finish but worsens removal. Zero gap belongs to a verified compatible support-material configuration, not a general PLA improvement. Dedicated support material is usually most economical at the interface only. On a single-nozzle machine, also check material-change count, flushing, and contamination of the structural filament. [Bambu support settings](https://wiki.bambulab.com/en/software/bambu-studio/support).

Bambu's support **Threshold angle is measured from horizontal**: increasing it can generate more supports. Do not transplant a numeric overhang threshold from a slicer using another convention. [Bambu support-angle definition](https://wiki.bambulab.com/en/software/bambu-studio/support#threshold-angle).

For critical supported surfaces, material interfaces, painted contacts, and bridge coupons, read [supports and bridges](supports-and-bridges.md).
