# Lab 2: Process Optimization Challenge

**Objective:** Solve a realistic multi-constraint optimization problem

**Scaffolding:** LOW — Challenge statement provided, student synthesizes approach

---

## The Challenge

Design a batch process meeting these specs:

| Constraint | Requirement |
|------------|-------------|
| Phenylalanine purity | ≥ 90% |
| Tryptophan purity | ≥ 85% |
| Both yields | ≥ 80% |
| **Objective** | Maximize productivity (g/h) |

**Fixed:** Column, isotherm parameters, feed concentration (20 g/L)

**Variables:** Feed volume, flow rate (1-5 mL/min), cut time

---

## Getting Started

Initialize session, configure default system.

[STOP AFTER THESE QUESTIONS — wait for student response before proceeding]

**Ask before optimizing:**
1. What's your strategy?
2. Which variable has biggest impact?
3. How will you calculate productivity?

Do NOT provide step-by-step guidance. Let student drive the optimization process.

---

## Available Tools

| Tool | Purpose |
|------|---------|
| `run_batch_chromatography` | Single simulation |
| `compare_simulations` | Compare conditions |
| `calculate_cut_time` | Find cut for purity/yield targets |
| `optimize_feed_volume` | Find feasible feed volume |
| `parse_outlet_data` | Quantitative analysis |

---

## Checkpoints

These are questions to ask at key points — each is a stopping point.

[STOP after each checkpoint question — wait for student response]

**After exploration:** "What feed volume range meets both purity constraints?"

**After feasible region:** "What cut time and actual metrics at optimal feed?"

**After productivity:** "Show your calculation."

---

## Sensitivity Analysis

Test ±10% feed concentration (18 and 22 g/L). Does the process still meet specs? What would you recommend?

---

## Model Limitations

[STOP AFTER THIS QUESTION — wait for student response before revealing assumptions]

**Ask:** "How might a real column behave differently?"

Key assumptions that may not hold (reveal after student responds):
- Uniform packing (reality: heterogeneity)
- No extra-column effects (reality: tubing dispersion)
- Perfect Langmuir isotherm (reality: deviations)
- Isothermal (reality: heat effects)

**Takeaway:** Simulation guides decisions but doesn't replace experimental validation. Build in margin.

---

## Final Deliverable

Present optimized process parameters and results vs. specs. Include chromatogram with cut time marked.

---

## Key Takeaways

1. **Multi-objective optimization requires trade-offs**
2. **Feasibility first, then optimize** within feasible region
3. **Sensitivity analysis is essential** — process must be robust
4. **Models have limitations** — validate experimentally

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
