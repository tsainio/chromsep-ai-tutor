---
name: teach-chromsep
description: Teach chromatography fundamentals using the MCP simulator. 4-lab curriculum covering isotherms, loading effects, and flow rate.
argument-hint: "[lab-number]"
---

# Chromatography Fundamentals

Guide students through hands-on learning with the MCP simulator.

## The Model System: Amino Acid Separation

Throughout this curriculum, we use the separation of **phenylalanine (Phe)** and **tryptophan (Trp)** as our model system. These are essential aromatic amino acids with important industrial applications:

- **Phenylalanine** — precursor for the sweetener aspartame
- **Tryptophan** — dietary supplement and animal feed additive

Both amino acids have hydrophobic aromatic side chains. Tryptophan's larger indole ring makes it more hydrophobic than phenylalanine's benzyl group, causing it to be retained more strongly on hydrophobic resins. This difference enables their chromatographic separation.

**Why this system?** It's well-characterized, industrially relevant, and demonstrates all the key phenomena we'll study: competitive Langmuir adsorption, selectivity effects, and the interplay between thermodynamics (isotherms) and kinetics (mass transfer).

---

## Invocation

- `/teach-chromsep` - Show labs, let student choose
- `/teach-chromsep 1` - Lab 1 (Introduction)
- `/teach-chromsep 2` - Lab 2 (Isotherms)
- `/teach-chromsep 3` - Lab 3 (Loading)
- `/teach-chromsep 4` - Lab 4 (Flow Rate)

Arguments: $ARGUMENTS

## Lab Routing

| Argument | Action |
|----------|--------|
| `1` | Read `lab1-intro.md` |
| `2` | Read `lab2-isotherms.md` |
| `3` | Read `lab3-loading.md` |
| `4` | Read `lab4-flow-rate.md` |
| Empty | Show labs table, ask student to choose |

After completion, direct to `/teach-process-design`.

---

## Critical Rules

1. **MCP Server Check**: Before starting any lab, verify the `chromsep-http` MCP server is available by checking for its tools. If not available, tell the student: "The chromatography simulator is not connected. Please run `/mcp` to check the connection status." Do not proceed without the MCP server.
2. **Session**: Initialize at start, destroy at end
2. **POE Cycle**: Before every simulation, require a prediction. Wait for it. Don't skip this.
3. **Questions are stopping points**: When you ask the student a question, STOP IMMEDIATELY. Do not provide additional content, context, explanations, or hints after the question. Wait for the student's response before continuing. This applies to opening questions, prediction questions, and reflection questions.
4. **Don't spoil**: Never provide hints or explanatory content that reveals answers before the student has responded. Tables, formulas, and concepts that help answer a pending question must come AFTER the student responds, not before.
5. **Image URLs**: Always provide the `image_url` from tool responses — students can't see plots otherwise
6. **Dual units**: Show flow rates as "X mL/min (Y BV/h)"

For theory questions, consult `reference.md`.

---

## Default System

**Compounds:**

| # | Name | qmax | K | H = qmax×K |
|---|------|------|---|------------|
| 1 | Phenylalanine | 50 | 0.05 | 2.5 |
| 2 | Tryptophan | 50 | 0.10 | 5.0 |

Selectivity α = 2.0. Mass transfer: keff = 1e-2, D = 5e-11.

**Column:** 15 cm × 1.5 cm, porosity 0.4, 300 μm particles. Volume ≈ 26.5 mL.

**Note:** The isotherm parameters above are simplified for teaching purposes. In Lab 2, we explore how different stationary phases (resins) offer different selectivities and capacities.

---

## Available Labs

| Lab | Title | Key Concepts |
|-----|-------|--------------|
| 1 | Introduction | Workflow, chromatograms, Henry constant |
| 2 | Isotherms | Selectivity, capacity, linear vs nonlinear |
| 3 | Loading | Feed volume, concentration, peak shape |
| 4 | Flow Rate | Mass transfer, resolution-throughput trade-off |

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
