# 3D printing skills

Four complementary Codex skills for designing functional FDM prints, choosing Bambu Studio settings, preparing project files and plates, and discussing builds through labelled images.

The defaults reflect a **Bambu P2S, 0.4 mm nozzle and PLA** workflow. The actual printer, material, project settings and user instructions take precedence. Material changes need their own fit and process checks; these skills do not establish a part's load rating.

## Included skills

| Skill | What it covers |
| --- | --- |
| [bambu-print-settings](skills/bambu-print-settings/SKILL.md) | Wall order, strength, tolerances, surface finish, orientation, supports, calibration, material efficiency, multicolour printing and purge reduction. |
| [pla-functional-design](skills/pla-functional-design/SKILL.md) | Load paths, joints, mechanisms, print orientation, expressive forms, hollow and lattice structures, and thermoforming approaches. |
| [print-project-organization](skills/print-project-organization/SKILL.md) | Editable source, exported parts, revision identity, quantities, native Bambu projects, plate planning and slice verification. |
| [print-build-communication](skills/print-build-communication/SKILL.md) | Labelled CAD views, stable feature callouts, sections and close-ups, and translating physical fit feedback into precise changes. |

The folders are siblings under `skills/` so their relative links work both here and when installed together. Each contains `SKILL.md` and Codex UI metadata; detailed guidance and source links live in the relevant `references/` directory.

## Install in Codex

Use Codex's bundled skill installer:

```sh
python3 "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-installer/scripts/install-skill-from-github.py" \
  --repo bruint/3d-printing-skills \
  --path skills/bambu-print-settings \
         skills/pla-functional-design \
         skills/print-project-organization \
         skills/print-build-communication
```

Access to this repository is required if it is private. Installed skills are available on the next turn in Codex. The installer refuses to overwrite an existing skill directory; compare and back up existing copies before replacing them. Install all four to retain the linked workflow.

Alternatively, copy the four complete skill folders into your configured Codex skills directory, preserving their sibling layout. This repository contains a snapshot of the skills; installed copies do not update automatically when the repository changes.

## Use

The skills support automatic selection for relevant work, or explicit invocation:

```text
Use $pla-functional-design and $bambu-print-settings to design a desk bracket,
choose its print orientation and prepare a small fit test.

Use $print-project-organization to prepare the source files, individual parts
and named Bambu Studio plates for this assembly.

Use $print-build-communication to show a labelled underside view and section
so I can identify the surface that needs changing.
```

The workflow distinguishes proposed geometry, exported meshes, actual slices and physical test results. Preparing a print project does not authorize sending a print job.

## References and design examples

Guidance includes links to manufacturer documentation, research and mechanism libraries. The references record when they were checked; recheck version-sensitive settings and material data when applying them. Linked third-party libraries remain separate dependencies with their own licenses.

The functional-design skill includes two Can Tower CAD render snapshots showing the leaf-lattice tubes and base. They illustrate reusable form and structure choices. The original Can Tower design project and other print-build files are not part of this repository, and the images do not establish physical performance.

This package preserves the existing skill guidance, including the preference for labelled build images, while replacing machine-specific Can Tower links with portable provenance notes.
