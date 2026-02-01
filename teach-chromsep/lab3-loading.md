# Lab 3: Loading Effects

**Objective:** Understand how feed volume and concentration affect separation

**Scaffolding:** MEDIUM — Guided comparisons, prompt for interpretations

---

## Context

Both feed volume and concentration affect **column loading** (total mass injected). Higher loading = more product per cycle but worse separation. Key insight: Total mass = Volume × Concentration.

---

## Part A: Feed Volume Effects

### Misconception Challenge
"Many students believe doubling feed volume doubles peak height (linear scaling). What do you predict?"

This misconception comes from analytical chemistry where behavior IS linear at low concentrations.

### Setup
Initialize session, configure default compounds (from SKILL.md).

### Prediction
Ask these three questions in order:
1. "Will doubling the feed volume double the peak height?"
2. "If we inject more material, will peaks get wider or stay the same width?"
3. "Will separation get better or worse as we load more?"

### Experiment
Use `compare_simulations` with four feed volumes (20 g/L, 2.2 mL/min, 6× eluent).

### Key Points
- Low feed (5%): near-linear, symmetric peaks
- High feed (20%): nonlinear, asymmetric "shark-fin" profile
- **Shark-fin shape:** Sharp front (saturated sites → fast migration) + elongated tail (available sites → slow migration). This is characteristic Langmuir behavior, not a flaw.

---

## Part B: Feed Concentration Effects

### Prediction
"At constant 10% feed, varying concentration 5-40 g/L: Will 10% @ 40 g/L look like 20% @ 10 g/L (same total mass)?"

### Experiment
Use `compare_simulations` with four concentrations at 10% feed.

### Key Points
| Parameter | Width Effect | Shape Effect | Mechanism |
|-----------|--------------|--------------|-----------|
| Volume | Directly widens | Moderate | Mass spread over time |
| Concentration | Less width effect | Strong nonlinearity | Higher local saturation |

Concentration has stronger effect on asymmetry because it pushes the isotherm harder.

---

## Part C: Equivalent Loading

### Prediction
"These two cases have the same total mass (10% × 60 = 75% × 8). Will the chromatograms look the same?"

### Experiment
Compare equal total mass, different distributions:
- 10% @ 60 g/L (narrow, concentrated)
- 75% @ 8 g/L (wide, dilute)

Use 8× eluent for both.

### Key Points
Same mass ≠ same chromatogram:
- **Concentrated (10% @ 60 g/L):** Elutes early (~9 min for Phenylalanine)
- **Dilute (75% @ 8 g/L):** Slightly broader, elutes significantly later (~18 min for Phenylalanine)

The main difference is retention time, not peak shape. High concentration saturates binding sites → molecules move faster through the column.

---

## Key Takeaways

1. **Loading = volume × concentration** — both affect separation
2. **Volume** widens peaks; **concentration** causes asymmetry
3. **Same mass ≠ same chromatogram** — distribution matters
4. **Shark-fin profile** = characteristic Langmuir behavior at high loading

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
