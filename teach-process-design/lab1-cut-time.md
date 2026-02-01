# Lab 1: Cut Time Optimization

**Objective:** Master the purity-yield trade-off through fraction collection decisions

**Scaffolding:** MEDIUM-LOW — Present tools, student decides strategy

---

## Context

Present a short explanation of what cut time is in preparative and production scale chromatography: switching collection vessels, Fraction 1 vs Fraction 2, and why the timing matters.

Then explain: The cut time directly impacts purity, yield, and economics. The trade-off is fundamental and cannot be circumvented.

---

## Setup

Initialize session, configure default compounds. Run with deliberate overlap: 15% feed, 20 g/L, 2.2 mL/min, 6× eluent.

Plot and ask student to identify the overlap region.

---

## Critical Question

[STOP AFTER THIS QUESTION — wait for student response before continuing]

**Ask directly:**
> "Can we find a single cut time that achieves ALL of these simultaneously?
> - Phenylalanine: ≥95% purity AND ≥90% yield
> - Tryptophan: ≥95% purity AND ≥90% yield
>
> Yes or no?"

**Don't answer yet.** Discover empirically.

---

## Experiments

### 1. Early Cut (Prioritize Phenylalanine Purity)
`calculate_cut_time`: criterion=`purity_fraction_1`, target=95%, generate_plot=true

Present results table. Ask: "What happened to Phenylalanine yield?"

### 2. Late Cut (Prioritize Tryptophan Purity)
`calculate_cut_time`: criterion=`purity_fraction_2`, target=95%, generate_plot=true

Compare to early cut.

### 3. Answer the Challenge
Can we achieve 95% purity for BOTH at the same cut time? Try it.

**Key insight:** The overlap MUST go somewhere. This is physics, not a tool limitation. A different simulator or better algorithm would give the same answer.

### 4. Equal Yield Cut
`calculate_cut_time`: criterion=`equal_yield`, generate_plot=true

When is this useful? When both compounds have similar value.

### 5. Trade-off Table
Run cut time analysis at F1 purity targets: 90%, 92%, 94%, 96%, 98%

Build and present the trade-off table showing how F2 metrics respond.

---

## Application

**Scenario:** Customer requires Phenylalanine at 98% purity.
1. What yield can you expect?
2. What will Tryptophan purity be?
3. Options if Tryptophan purity is too low?

Options: accept lower purity, reprocess F2, collect recycle fraction, reduce loading.

---

## Key Takeaways

1. **Cut time divides overlap** — doesn't eliminate it
2. **Higher purity = lower yield** — fundamental trade-off, not tool limitation
3. **95%/95% purity for both is impossible** with overlapping peaks — this is thermodynamic
4. **Optimal cut depends on requirements** — product value, specs, acceptable waste

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
