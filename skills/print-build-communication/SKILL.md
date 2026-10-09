---
name: print-build-communication
description: Discuss and review 3D-printing builds through labelled images, stable feature callouts, and useful close-ups. Apply when explaining a CAD design, gathering spatial feedback, identifying a print problem, or showing revisions to a part or assembly.
---

# Print build communication

The user prefers **labelled images they can point to**. Make visual identification the main interface for discussing a build. The user can speak naturally, refer to a callout number, or mark a location; do not require CAD terminology or a structured request form.

## Show the relevant geometry

Start with a clear overview and the close-up needed for the current decision. Add an underside, section, or exploded view when the feature is hidden or its relationship is unclear. Show the assembled orientation for use and fit discussions; identify a separate print-orientation view when discussing slicing. Avoid generating a full drawing pack for a small change.

Use renders from the actual CAD or mesh for geometry decisions and photographs for observed print results. Keep illustrative sketches identifiable as sketches. Identify an older render as a reference rather than treating it as the current revision. Do not invent dimensions, hidden surfaces, or physical test results from an image.

Put a short build name, revision when known, and view name on or beside each view. Establish front, rear, left, right, top, and underside from the object's installed or operating position. Keep those names when the camera rotates. Use a labelled reference edge or direction arrow where orientation is otherwise ambiguous.

## Compare form concepts

When the overall form is open and a visual comparison would help, show a small set of labelled alternatives with meaningfully different silhouettes, structural layouts, or negative space. Keep the required interfaces and functional constraints comparable, and use matched camera angles and scale where practical. Identify concept sketches or rough CAD as such. Let the user refer to “A's flowing ribs” or “B's wider feet,” and explain the consequence of combining them. For an established design, retain its feature callouts within each named option. Routine detail changes do not require fresh alternatives.

## Give features stable callouts

Use simple numbered callouts with short plain-language names: `1 — bin socket`, `2 — end wall`, `3 — metal grip`, `4 — support rib`. Point leaders to the exact feature and keep labels readable and clear of the geometry. Label the features relevant to the discussion, with additional detail views when an overview becomes crowded.

Keep the same identifier for the same feature across views and revisions. Do not silently reuse a retired identifier for another feature. Distinguish repeated instances when scope matters: separate callouts, an instance suffix, or a clear position name. A label for a whole family should explicitly say so, such as “all three grips.”

Keep a small mapping from callouts to actual part and feature names with the project's existing documentation when the discussion is likely to continue. Record the corresponding CAD parameter only when it helps future changes. An integral feature is still part of its printed body; a callout does not imply a separate printable part. Keep labels and arrows in the discussion view, separate from production geometry.

Use color as an additional highlight, paired with numbers or names. Distinguish illustration colors from actual filament assignments. For an interactive view, keep labels visible and provide equivalent named controls so precise clicking is optional; selection must also be understandable in a still image.

## Translate feedback into a concrete change

Resolve the target from the image and context, then state the intended change briefly: “I’ll thicken the root of 4 and keep 3’s mating gap unchanged.” Continue when the meaning is clear. If “this side” could refer to two materially different features, show or name the candidates and ask only that clarification.

Useful information is **target, desired result, and what must stay fixed**, but gather it conversationally. “3 catches when sliding on” is enough to begin examining the grip's entry and fit. Separate what the user observed from the suspected cause; do not treat “too tight” as proof that the entire part needs scaling.

When a number matters, mark the dimension or gap on the relevant view in millimetres. Distinguish thickness from width, opening from outside size, and clearance per side from total clearance. Identify nominal CAD values separately from measurements of a physical print.

## Close the feedback loop

For a meaningful geometry revision, show the changed feature from the same useful viewpoint, retaining its callout. Use a matched before/after view when it clarifies the change, and identify the revisions. Briefly say what changed, which important fit or interface was preserved, and whether the result is rendered, sliced, or physically tested.

Store useful views in the project's existing preview location and keep the callout mapping with its build notes. Apply [print project organization](../print-project-organization/SKILL.md) when updating deliverables. Use [PLA functional design](../pla-functional-design/SKILL.md) for the underlying geometry decisions; the labelled views communicate those decisions rather than replacing their validation.
