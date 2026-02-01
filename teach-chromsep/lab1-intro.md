# Lab 1: Introduction to the Simulator

**Objective:** Learn the simulation workflow and establish the POE learning pattern

**Scaffolding:** HIGH — First lab, explain why each step matters

---

## Context

This lab establishes a baseline case you'll reference throughout the curriculum. The workflow mirrors industrial practice: define system → set conditions → analyze output.

---

## Sequence

### 1. Initialize Session
- `init_session` — creates isolated workspace
- Explain session_id tracking

### 2. Examine Column
- `get_column` — show dimensions with physical meaning
- Calculate column volume (~26.5 mL)
- Explain: all parameters reference this volume

### 3. Configure Compounds
- `set_compound` for both (use default parameters from SKILL.md)
- Present isotherm table, calculate α = 2.0
- Explain qmax (capacity), K (affinity), H = qmax×K (retention)

### 4. Prediction (CRITICAL)

Operating conditions: 2.2 mL/min (5 BV/h), 5% feed, 6× eluent, 20 g/L each

**Ask:**
1. "Which compound will elute first, based on Henry constants?"
2. "Will peaks be symmetric (Gaussian) or asymmetric?"

Note: Students from analytical chemistry often expect symmetric peaks. Don't correct — let simulation reveal.

### 5. Run Simulation
- `run_batch_chromatography` with above parameters

### 6. Observe Results
- `plot_simulation_output` — **provide image URL**
- Ask student to describe what they see before explaining

### 7. Compare to Prediction
- Phenylalanine (lower H) elutes first — less time on stationary phase
- At 5% feed, peaks are relatively symmetric (near-linear regime)
- If student predicted asymmetric: explain we'll see that at higher loading in Lab 3

### 8. Cleanup
- `destroy_session`

---

## Key Takeaways

1. **Workflow:** Initialize → Configure → Run → Analyze
2. **Henry constant (H)** determines retention order — higher H = later elution
3. **Selectivity (α > 1.5)** needed for preparative separation
4. **This baseline** (5% feed) represents near-linear behavior

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
