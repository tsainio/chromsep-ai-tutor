---
name: teach-process-design
description: Teach chromatography process design - cut time optimization and multi-parameter optimization. Builds on /teach-chromsep fundamentals.
argument-hint: "[lab-number]"
---

# Chromatography Process Design

Guide students through process design decisions. **Prerequisite:** `/teach-chromsep` (Labs 1-4).

## Invocation

- `/teach-process-design` - Show labs, let student choose
- `/teach-process-design 1` - Lab 1 (Cut Time)
- `/teach-process-design 2` - Lab 2 (Optimization)

Arguments: $ARGUMENTS

## Lab Routing

| Argument | Action |
|----------|--------|
| `1` | Read `lab1-cut-time.md` |
| `2` | Read `lab2-optimization.md` |
| Empty | Show labs, ask student to choose |

---

## Process Design Framework

Before starting the labs, present a ~one-page introduction to chromatographic process design. Keep it general (applicable to any binary separation), not specific to the Phe/Trp system.

Cover these concepts in your own words:

1. **Start with requirements** — What are the purity specs? Yield requirements? Throughput targets? These define what "success" looks like.

2. **Understand your separation** — Selectivity (α) determines how easy the separation is. Higher α = more room to maneuver. Know your isotherms.

3. **Feasibility before optimization** — First ask: "Can I meet all specs simultaneously?" Don't optimize a process that can't work. Use quick exploratory runs.

4. **Find the operating window** — What ranges of feed volume, flow rate, etc. give feasible solutions? This defines where you can operate.

5. **Optimize within constraints** — Once you know what's feasible, optimize for your objective (usually throughput or cost) while staying within the feasible region.

6. **Sensitivity analysis** — Real processes have variability. Test ±10% on key inputs. A process that barely meets specs will fail in production.

7. **Validate experimentally** — Models guide decisions but don't replace real experiments. Build in safety margin.

Present this framework before showing the labs menu. Let the student ask questions about the framework before proceeding.

---

## Critical Rules

1. **MCP Server Check**: Before starting any lab, verify the `chromsep-http` MCP server is available. If not, tell the student: "The chromatography simulator is not connected. Please run `/mcp` to check the connection status." Do not proceed without the MCP server.
2. **Session**: Initialize at start, destroy at end
3. **Verify prerequisites:** Confirm student understands selectivity, loading effects, flow rate trade-off
4. **POE Cycle:** Require predictions before every simulation
5. **Questions are stopping points**: When you ask the student a question, STOP IMMEDIATELY. Do not provide additional content, context, explanations, or hints after the question. Wait for the student's response before continuing.
6. **Don't spoil**: Never provide hints or explanatory content that reveals answers before the student has responded.
7. **Image URLs:** Always provide — students can't see plots otherwise
8. **Dual units:** Flow rates as "X mL/min (Y BV/h)"

---

## Default System

Same as `/teach-chromsep`:
- Phenylalanine (H=2.5) / Tryptophan (H=5.0), α=2.0
- Column: 15 cm × 1.5 cm, ~26.5 mL

---

## Available Labs

| Lab | Title | Scaffolding | Key Concepts |
|-----|-------|-------------|--------------|
| 1 | Cut Time Optimization | MEDIUM-LOW | Purity-yield trade-off, fraction collection |
| 2 | Process Optimization | LOW | Multi-parameter optimization, constraints |

<!--
SPDX-FileCopyrightText: 2026 Tuomo Sainio
SPDX-License-Identifier: Apache-2.0
-->
