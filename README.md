# Tree Influence Check — AS 2870 Appendix H

A self-contained, standalone browser tool that screens a tree's proximity to footings on reactive soil
using the **AS 2870 Appendix H** proximity-ratio method (after Cameron &amp; Earl). Exports a branded
"Comps" report.

## Run it
Open `index.html` in any browser. Keep `logo.js` alongside it for the PDF header.

## Method
Required clearance **D<sub>min</sub> = ratio × H**, where H is the species' **mature** height and the
proximity ratio is set by site reactivity:

| Site reactivity | Risk | Single-tree ratio | Row/group (×1.5) |
|---|---|---|---|
| Class S — slightly reactive | low | 0.5 | 0.75 |
| Class M — moderately reactive | moderate | 0.75 | 1.125 |
| Class H1/H2/E — highly+ reactive | high | 1.0 | 1.5 |
| Class A — non-reactive | minimal | n/a | n/a |

- **D ≥ D<sub>min</sub>** → outside the zone of significant influence; standard design for the site class.
- **D &lt; D<sub>min</sub>** → within the zone of influence; the footing must be designed for the additional
  reactive movement from tree drying (deeper design suction change / increased differential movement) per
  AS 2870 Appendix H, or the tree removed/relocated.

Inputs: site classification, tree arrangement (single / row-group), mature height H, distance D, an
editable proximity ratio (auto-derived), optional tree water demand (informational) and design suction
depth H<sub>s</sub> / pier depth for a quick founding-vs-H<sub>s</sub> note.

## Rigid slab (raft) check

Beyond the clearance screen, an optional **rigid-raft differential-movement check** (SLOG-style):

- estimates the **tree movement increment** from Appendix H as `Δys = α · ys · (1 − D/Dmin)` — i.e. it
  grows as the tree sits further inside the zone of influence (α editable);
- gives the **design surface movement** `ys,design = ys + Δys` and the resulting **effective site class**
  (so you see when a tree pushes, e.g., H1 → E);
- compares the **differential deflection** against **AS 2870 Table 4.1** for the wall type — clad frame
  (L/300, 40 mm), articulated masonry veneer (L/400, 30 mm), articulated full masonry (L/800, 15 mm),
  full masonry (L/2000, 10 mm), all editable;
- uses your **slab design Δ** (e.g. from SLOG) when entered for the real check, otherwise a conservative
  `k · ys,design` estimate flagged as indicative.

This is a **screening check**, not the full Mitchell-method raft design (AS 2870 Section 4 / Appendix F,
e.g. SLOG), which governs.

## Important
- AS 2870 **does not** factor tree species / water demand into the ratio — the tool flags high-water-demand
  species for caution only.
- This is a **planning / clearance screen**. Footing design within the zone of influence requires a
  site-specific geotechnical assessment.
- Confirm the site classification, mature tree height and method against **AS 2870-2011 Appendix H** and the
  geotechnical report. The design engineer remains responsible; outputs do not constitute design
  certification.
