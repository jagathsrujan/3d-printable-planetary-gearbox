# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

static HTML/CSS/JS, multi-file (`index.html` + `styles.css` + `deck.js` + `assets/`). Confirmed by the user over a single self-contained file and over a Vite/framework build. No build step, no server: the deck must open by double-clicking `index.html`.

## Users

Primary: the repository owner — a maker/mechanical-engineering audience who has (or is planning) the printed parts on the bench. Situation: they have the STLs, a NEMA 17, and the hardware, and they want to understand the mechanism and the build decisions before/during assembly. Secondary: anyone shown the deck — a class, a team, or a maker-community audience.

## Product Purpose

A presentation-webpage that explains how planetary gears work and documents this specific two-stage 16:1 3D-printed gearbox end to end: mechanism, transmission ratios, design rules, CAD, print settings, assembly, and measured backlash/torque. Success: the viewer can explain the mechanism and the 16:1 derivation, and knows what the printed parts are and how they go together.

## Positioning

A generic "how planetary gears work" explainer exists everywhere; a generic gearbox teardown does not have the parts. This deck's differentiator is that its 3D renders are generated from *this repository's own STL meshes* — the ring gear, carriers, planets, and sun shown are the exact files in `Two%20stage%20planetary%20gearbox%20-%20STL%20Files/`, not stock CAD imagery. The measured performance section reports the actual tested numbers, including the corrected torque figures.

## Operating Context

- Source tutorial: How To Mechatronics, "How Planetary Gears Work" (design by Dejan), originally modelled in Onshape. Credited, not claimed.
- The repository collects the printable STLs plus build documentation in `README.md`.
- Hardware on hand: 6 mm x 22 mm pins, 8 mm bushings, 6805/6803/6802 bearings, M3 heat-set inserts, M6 washers, M3 bolts.
- Viewer usage: presented live (keyboard navigation) and also read alone on a laptop.
- Fabrication context: FDM, PLA, slicer horizontal-expansion tuning.

## Capabilities and Constraints

Confirmed deck content, in order: mechanism and the four components; the three holding-member configurations and their ratios; transmission-ratio formulas; the 16:1 two-stage derivation; the two planetary design rules plus co-prime tooth choice and module; CAD approach; print settings; assembly sequence; NEMA 17 mounting; backlash and torque results.

Constraints and terminology: gear module, tooth counts (sun 15T / planet 15T / ring 45T), helical profile, backlash in arcminutes, co-prime teeth. Axial loads from helical teeth are a real design caveat. Bushings instead of bearings are the efficiency bottleneck.

Binding factual constraint: the source article states gearbox torque as "200 Nm" and bare-motor torque as "28 Nm", which is off by a factor of 10. `README.md` corrects these to ~2 Nm and ~0.28 Nm. The deck must use the corrected values and label the discrepancy rather than republishing the source figures.

## Brand Commitments

- Attribution to How To Mechatronics is required wherever the design or its photographs appear. The design is theirs; the STLs and build notes are this repository's.
- The article's part colours are a legible build key and should be preserved as a visual convention: input shaft gold, stage 1 carrier orange, planets white, stage 2 carrier/output blue, housing grey.

## Evidence on Hand

- 46 photographs from the source tutorial, downloaded to `assets/raw/` (mechanism diagrams, CAD screenshots, print/assembly photos, test setups).
- 13 STL meshes in `Two%20stage%20planetary%20gearbox%20-%20STL%20Files/` (binary STL, 7k–158k triangles), including 4 `CUTOUT -` sectioned variants. These are the ground truth for all part renders.
- `README.md`: measured bolt lengths, insert depths, counterbore/countersink dimensions, BOM, assembly steps, and the corrected performance figures.
- No fabricated testimonials, prices, or benchmarks. The only numbers are the article's measured results and the README's measured hardware dimensions.

## Product Principles

1. Renders come from the repository's own meshes. If a part appears, it is a real part in this build.
2. Ratios and design rules are shown as arithmetic that can be checked, not as asserted facts.
3. Credit the original designer wherever their design or photographs carry the slide.
4. Where the source material is wrong, report the correction inline rather than silently fixing or silently repeating it.
5. Explain the trade-off, not just the number: backlash and efficiency move in opposite directions here, and the deck should say so.
