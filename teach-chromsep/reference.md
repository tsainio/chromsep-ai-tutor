# Theory Reference

Consult as needed during labs. Not meant to be read in full.

---

## Core Concepts

### Linear vs. Nonlinear Chromatography

| Aspect | Linear (Analytical) | Nonlinear (Preparative) |
|--------|---------------------|-------------------------|
| Concentration | Dilute | High (overloaded) |
| Isotherm | q = HC | q = qmax·KC/(1+KC) |
| Peak shape | Symmetric | Asymmetric (tailing) |
| Goal | Detection | Purification |

### The Langmuir Isotherm

```
q = (qmax · K · C) / (1 + K · C)

qmax = saturation capacity (g/L)
K    = binding affinity (L/g)
H    = qmax × K (Henry constant, slope at low C)
```

At low C: linear (q ≈ H·C). At high C: saturation (q → qmax).

### Key Relationships

- **Henry constant:** H = qmax × K
- **Selectivity:** α = H₂/H₁ (ratio of retention)
- **Rule of thumb:** α > 1.5 for preparative separation

### Purity-Yield Trade-off

With overlapping peaks, the overlap must go somewhere:
- Early cut → high purity F1, low yield F1
- Late cut → high yield F1, low purity F1

You cannot have 100% purity AND 100% yield for both fractions.

---

## Common Questions

**"Why asymmetric peaks?"**
Langmuir isotherm: high-concentration zones move faster (saturated sites), low-concentration tails move slower. Result: sharp front, elongated tail.

**"Why doesn't doubling feed double peak height?"**
Isotherm saturation. Additional molecules aren't retained as strongly, spreading the peak wider.

**"Can I get 100% purity and yield?"**
Only if peaks don't overlap. With overlap, trade-off is unavoidable.

**"Higher flow = always better?"**
No. Higher flow reduces equilibration time → broader peaks → worse resolution. Trade-off against throughput.

---

## Model Limitations

The simulator assumes:
- Uniform packing (reality: wall effects, heterogeneity)
- No extra-column effects (reality: tubing, fittings add dispersion)
- Langmuir isotherm (reality: may deviate)
- Isothermal (reality: heat of adsorption)
- Lumped kinetics (reality: multiple resistances)

**Use simulation for:**
- Qualitative trends (high reliability)
- Relative comparisons (good reliability)
- Screening many conditions (excellent)
- Absolute predictions (moderate — validate experimentally)

---

## Parameter Ranges

| Parameter | Typical Range | Units |
|-----------|---------------|-------|
| Flow rate | 1-50 | mL/min |
| Feed volume | 5-25 | % CV |
| Feed concentration | 1-100 | g/L |
| Langmuir qmax | 10-100 | g/L |
| Langmuir K | 0.01-1.0 | L/g |

---

## Formulas

```
Column volume:   CV = π·d²·L/4
Henry constant:  H = qmax·K
Selectivity:     α = H₂/H₁
Residence time:  τ = CV/F
BV/h:            (F in mL/min × 60) / CV in mL
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Peaks don't elute | Increase eluent (try 8-10×) |
| Complete overlap | Reduce feed volume; check α |
| Simulation fails | Check parameter values are reasonable |
| Lost session | Use `list_sessions` or create new |

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
