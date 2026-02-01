# Lab 2: Isotherm Fundamentals

**Objective:** Understand how selectivity (α) and capacity (qmax) independently affect separation

**Scaffolding:** MEDIUM — Guide experiments, prompt for interpretations

---

## Context

In real process development, one of your most important decisions is choosing the **stationary phase** (resin). Different resins interact with your target molecules differently, resulting in different isotherm parameters.

### A Thought Experiment: Shopping for Resins

Imagine you're developing a process to separate phenylalanine and tryptophan. Several vendors offer resins that could work:

| Vendor | Resin Type | What They Offer |
|--------|------------|-----------------|
| A | Standard hydrophobic | Moderate selectivity (α = 1.5), moderate capacity |
| B | Enhanced hydrophobic | Higher selectivity (α = 2.0), same capacity |
| C | Premium hydrophobic | Best selectivity (α = 3.0), same capacity |
| D | High-capacity variant | Same selectivity as B, but 4× the capacity |

Which resin should you choose? The answer depends on understanding how **selectivity** and **capacity** independently affect your separation.

In this lab, we'll use the simulator to explore these hypothetical resins. While the specific numbers are simplified for teaching, the principles apply directly to real resin selection decisions.

**Key insight:** You cannot change a resin's selectivity by adjusting operating conditions (flow rate, feed volume, etc.). Selectivity is a thermodynamic property — if your resin doesn't have adequate selectivity, no amount of optimization will fix it.

---

## IMPORTANT: Session Management for Isotherm Comparisons

When comparing different isotherm parameters (different K, qmax values), you MUST use **separate sessions** for each case. This is because:

1. Each simulation overwrites output files (`outlettank01.dat`, `batch_outlet.png`)
2. `compare_simulations` only varies operating conditions, not isotherm parameters
3. If you run multiple simulations in one session, the HTTP image URLs will only show the last result

**Correct workflow for isotherm comparisons:**

1. For each isotherm configuration:
   - `init_session` with descriptive name (e.g., "Lab 2 - alpha=1.5")
   - Set column and compound parameters
   - Run simulation
   - Plot and **save the image_url**
   - Do NOT destroy session yet
2. Present ALL image URLs to the student together (each URL points to a different session's output)
3. After student has viewed all plots, destroy all sessions

---

## Part A: Varying Selectivity

### Setup
Create THREE separate sessions, one for each selectivity value.

In each session, set Compound 1 fixed: qmax=50, K=0.1 (H=5.0)

Test three selectivities by varying Compound 2's K:

| α | Compound 2 K | Compound 2 H | Session description |
|---|--------------|--------------|---------------------|
| 1.5 | 0.15 | 7.5 | "Lab 2 - alpha=1.5" |
| 2.0 | 0.20 | 10.0 | "Lab 2 - alpha=2.0" |
| 3.0 | 0.30 | 15.0 | "Lab 2 - alpha=3.0" |

### Prediction
"As selectivity increases from 1.5 to 3.0, what happens to peak spacing and overlap?"

### Experiments
Run each case in its own session: 10% feed, 20 g/L, 2.2 mL/min. Eluent volumes (higher retention needs more eluent):
- α = 1.5: 6× eluent
- α = 2.0: 8× eluent
- α = 3.0: 11× eluent

After all three simulations complete, present all three image URLs together so the student can compare.

### Key Points
- Higher α = greater retention difference = more separation
- α > 1.5 rule of thumb for preparative work makes sense — at α = 1.5 there's significant overlap
- Selectivity is thermodynamic — you cannot change it with operating conditions

### Assessment Checkpoint
"If α = 1.1, could you achieve separation with a longer column?"

Answer: No. Column length improves efficiency but doesn't change fundamental retention difference. At α ≈ 1.0, peaks overlap regardless.

---

## Part B: Varying Capacity at Constant Selectivity

### Setup
Create TWO separate sessions (or reuse from Part A after destroying old ones).

Keep α = 2.0 constant, vary qmax while adjusting K to maintain same Henry constants:

| Capacity | qmax | K₁ | K₂ | H₁ | H₂ | Session description |
|----------|------|-----|-----|----|----|---------------------|
| Low | 25 | 0.2 | 0.4 | 5 | 10 | "Lab 2 - low capacity" |
| High | 100 | 0.05 | 0.10 | 5 | 10 | "Lab 2 - high capacity" |

### Prediction
"Both systems have same α and H values. At 15% feed (20 g/L), will peaks look the same?"

### Experiments
Run each case in its own session: 15% feed, 20 g/L, 2.2 mL/min, 8× eluent.

Present both image URLs together for comparison.

### Key Points
- Same selectivity ≠ same peak shape at high loading
- Low qmax: 20 g/L is close to saturation → nonlinear → severe tailing
- High qmax: 20 g/L is far from saturation → more linear → symmetric peaks
- **Insight:** Capacity determines how linear the system behaves at a given loading

---

## Key Takeaways

1. **Selectivity (α)** determines peak spacing — thermodynamic, can't be changed by operation
2. **Capacity (qmax)** determines linearity at a given loading
3. Both matter: high selectivity necessary but not sufficient; need adequate capacity too
4. Industrial implication: consider both when selecting resins

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
