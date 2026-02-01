# Lab 4: Flow Rate Effects

**Objective:** Understand how flow rate affects mass transfer and the resolution-throughput trade-off

**Scaffolding:** MEDIUM — Guided comparisons with analysis

---

## Context

Flow rate affects **equilibration time** — how long molecules have to exchange between phases. This completes your understanding of fundamental phenomena.

## Opening Question

[STOP AFTER THIS QUESTION — wait for student response before continuing]

Present this claim and ask if it's true:

> "In most manufacturing, faster processing is better. Does the same apply to chromatography — is faster flow rate always better?"

Do NOT explain residence time, equilibration, or mass transfer yet. Wait for the student's reasoning first.

---

## After Opening Question

Once the student responds to the opening question, introduce residence time:

**Residence time** tells us how long the mobile phase spends in the column: τ = Column Volume / Flow Rate

Present the flow rates we'll test (WITHOUT characterization hints):

| BV/h | mL/min | Residence Time |
|------|--------|----------------|
| 2 | 0.88 | 30 min |
| 5 | 2.21 | 12 min |
| 10 | 4.42 | 6 min |

---

## Experiment

### Setup
Initialize session, configure default compounds. Use low loading (5% feed, 10 g/L) to isolate flow rate effects from loading effects.

### Prediction

[STOP AFTER THIS QUESTION — wait for student response before running simulation]

"We'll run three separations at 2, 5, and 10 BV/h. Before we run them:
1. How will peak **width** change as flow rate increases?
2. Will **retention time** change?
3. Which flow rate will give the **best separation**?"

Do NOT provide hints about equilibration or mass transfer limits. Let the student reason from residence time alone.

### Run
Use `compare_simulations` with three flow rates (5% feed, 10 g/L, 5.5× eluent).

### Discussion (after simulation)

Only after viewing results, discuss:

| Flow Rate | Cycle Time | Peak Width | Resolution |
|-----------|------------|------------|------------|
| 2 BV/h | longest | narrowest | best |
| 5 BV/h | medium | medium | good |
| 10 BV/h | shortest | widest | reduced |

**Key concepts to introduce now:**
- **Mass transfer:** Lower flow → more equilibration → sharper peaks
- **Trade-off:** Speed vs. resolution

**Why peaks broaden at higher flow:** Mass transfer kinetics. With keff = 0.01 (1/s), characteristic time is 100s. At 2 BV/h (30 min residence), plenty of equilibration. At 10 BV/h (6 min), molecules can't fully equilibrate.

---

## The Trade-off

"If faster flow broadens peaks, why use it?"

**Throughput.** At 2 BV/h: ~6 batches/day. At 10 BV/h: ~30 batches/day. Even with worse separation per batch, 5× more material processed. If separation is still acceptable, faster wins.

**Analytical vs. Preparative:** Analytical HPLC uses 3-5 μm particles (fast kinetics, keff ~10× higher). Preparative uses 20-50 μm (manageable pressure). Large-scale industrial processes (e.g., sweeteners industry) use up to 350 μm particles. Larger particles = slower kinetics = more sensitive to flow rate.

---

## Key Takeaways

1. **Flow rate affects equilibration** — faster = less time to equilibrate = broader peaks
2. **Throughput-resolution trade-off** — fundamental to process design
3. **Mass transfer kinetics (keff)** determine sensitivity to flow rate
4. **Practical range:** 2-10 BV/h for preparative chromatography

---

## Curriculum Complete

You now understand isotherms, loading, and flow rate. Continue to `/teach-process-design` for cut time optimization and process design.

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
