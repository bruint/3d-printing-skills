---
name: bambu-print-settings
description: Choose, review, and tune Bambu Studio print settings for strength, fit, surface finish, material efficiency, and reliable printing, with P2S and PLA as the user's usual setup. Apply alongside CAD and OpenSCAD design when creating or revising parts intended for FDM printing, and for slicer configurations, supports, multicolour printing, purge reduction, process or filament presets, and print defects affected by settings.
---

# Bambu print settings

Recommend settings from the part's geometry, purpose, and observed print results. Explain why a setting helps and what it costs. Keep manufacturer guidance, practical starting values, and measured results distinct.

## Apply to builds by default

Apply the relevant print best practices whenever we create or revise a part intended for FDM printing, without waiting for a separate slicer question or explicit skill invocation. Coordinate orientation, wall thickness, overhangs, clearances, and visible faces with the intended print settings before finalizing geometry. Use [PLA functional design](../pla-functional-design/SKILL.md) for the geometry and load-path decisions when applicable.

For a completed build, include a concise setup suited to its actual geometry: orientation, base presets, layer height, wall order and loops, infill, shell thickness, and supports or adhesion aids where relevant. Explain consequential choices and record these recommendations with the build's editable source and printable files, following the project's existing documentation conventions. For small revisions, revisit only the print decisions affected by the change and preserve proven settings.

Use [print project organization](../print-project-organization/SKILL.md) when preparing or updating project files and plates. It covers current revisions, part quantities, compatible plate groups, captive assemblies, and keeping source, meshes, and saved Bambu projects in sync.

## Establish the print context

- The user's usual setup is a **Bambu P2S with a 0.4 mm nozzle printing PLA**. Use that as a stated assumption when context is absent; actual project settings or user instructions take precedence. Do not assume the PLA brand, subtype, build plate, or installed accessories.
- Reuse known information. Identify the nozzle, filament, plate, print orientation, important fits and visible faces, load direction, and priority among strength, finish, time, and material. Ask only for missing details that would change the recommendation; ordinary choices do not require a questionnaire.
- Start from the matching printer, filament, and process presets. Preserve deliberate, successful tuning. In an existing project, check object, part, and modifier overrides before attributing behavior to global settings. Bambu documents this hierarchy in its [slicing-parameter guide](https://wiki.bambulab.com/en/software/bambu-studio/how-to-set-slicing-parameters).
- Check the installed version when recommending an unfamiliar or recently introduced option. Use the actual Bambu Studio label and units. Do not transfer OrcaSlicer options or another printer's fan behavior without verifying availability and meaning.

## Choose the relevant rules

- For a build where finish matters, or when choosing among several possible defect fixes, read [quality workflow](references/quality-workflow.md). It maps visible symptoms to useful techniques and representative comparisons.
- For wall order, wall loops, infill, shells, and thin details, read [walls and strength](references/walls-and-strength.md).
- For dimensional error, seams, curved-insert orientation, surface appearance, and ironing, read [fit and finish](references/fit-and-finish.md).
- For speed limits, calibration, cooling, and bed adhesion, read [filament and reliability](references/filament-and-reliability.md).
- For visible undersides, support painting or materials, and bridge tuning, read [supports and bridges](references/supports-and-bridges.md).
- For material reduction, read [material efficiency](references/material-efficiency.md). For multiple colours, support-material changes, AMS waste, or prime towers, also read [multicolour and purge](references/multicolour-and-purge.md).

The references record guidance checked on **2026-10-08**. Consult the linked primary documentation when behavior is uncertain or the installed version differs. Retain conditional rules instead of accumulating universal toggles.

For a load-bearing part, assess orientation and actual deposited material before increasing infill. If settings cannot address a weak root, missing clearance, unsupported underside, or unsuitable load direction, explain the geometry change needed. Use the available `pla-functional-design` skill when the task also calls for designing or revising that geometry.

## P2S / ordinary PLA starting point

When building a profile from scratch for an ordinary functional part with the assumed 0.4 mm nozzle, propose **0.20 mm layers, 4 wall loops, and 20% gyroid infill** as a practical test baseline. This is an engineering starting point, not an official Bambu recipe or a strength rating. Retain the matching preset's line widths, temperature, flow ratio, cooling, and speed limits until geometry or evidence warrants a change. Choose wall order and shell thickness using the references. Reassess this baseline for decorative, flexible, very thin, silk, foaming, composite, or differently sized nozzle prints.

Use local reinforcement or object overrides where the need is local. Tune the smallest set of parameters that addresses the diagnosed issue, retaining a known baseline for comparison.

For full builds, assess material use alongside quality: geometry and supports, colour-change layout, then infill and purge tuning. Compare total filament for the required usable parts, including plate repeats. Preserve needed strength and finish; record untested savings as candidates until sliced or printed.

## Make the result actionable

For a full configuration, give the base presets and a compact table: **Bambu Studio setting/location | proposed value | reason and tradeoff**. Include only relevant changes and key retained values. Identify assumptions and the smallest useful coupon: a representative hole/peg, overhang, supported underside, or loaded root in the intended orientation and filament. A single-setting question needs only a focused answer.

If editing a project or preset is requested, save a named copy and preserve unrelated settings. Do not invent an importable preset schema; use an actual export or the installed version's format and verify it loads. A request for configuration advice does not itself request launching a print or calibration job.

When slicing tools are available, inspect the first layer, critical cross-sections, wall order and count, bridge anchoring, support access, seams, and speed/flow preview. Report estimated time and filament only from an actual slice. Distinguish **recommended**, **sliced**, and **physically tested** settings; never imply a load test or successful print occurred without evidence.
