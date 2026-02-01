# Chromatography Teaching Skills for Claude Code

This repository contains skill definitions for teaching chromatography concepts using Claude Code and an MCP-based simulator. These files demonstrate how to build structured, interactive educational experiences with AI assistance.

## What Are These Files?

These are **Claude Code skills** — markdown files that give Claude specialized instructions for specific tasks. When a user invokes a skill (e.g., `/teach-chromsep`), Claude reads the corresponding files and follows the embedded pedagogy.

The skills here implement a complete chromatography curriculum covering:

- **Hub** (`teach/`): Routes students to the appropriate curriculum based on their goals
- **Fundamentals** (`teach-chromsep/`): Isotherms, loading effects, flow rate (4 labs)
- **Process Design** (`teach-process-design/`): Cut time optimization, multi-parameter optimization (2 labs)

## Repository Structure

```
.
├── teach/                      # Hub skill - routes to curricula
│   └── SKILL.md                # Routes users to appropriate curriculum
├── teach-chromsep/             # Fundamentals curriculum (4 labs)
│   ├── SKILL.md                # Skill definition with YAML frontmatter
│   ├── lab1-intro.md           # Introduction to the simulator
│   ├── lab2-isotherms.md       # Selectivity and capacity
│   ├── lab3-loading.md         # Feed volume and concentration effects
│   ├── lab4-flow-rate.md       # Mass transfer and throughput trade-off
│   └── reference.md            # Theory reference for instructor
└── teach-process-design/       # Process design curriculum (2 labs)
    ├── SKILL.md                # Includes Process Design Framework intro
    ├── lab1-cut-time.md        # Purity-yield trade-off
    └── lab2-optimization.md    # Multi-constraint optimization
```

The `teach/` skill serves as a hub that helps students choose between learning paths and routes them to the appropriate curriculum.

## Skill File Format

### SKILL.md Structure

Each skill folder contains a `SKILL.md` with YAML frontmatter:

```yaml
---
name: teach-chromsep
description: Teach chromatography fundamentals using the MCP simulator.
argument-hint: "[lab-number]"
---

# Skill Title

Instructions for Claude...
```

| Field | Purpose |
|-------|---------|
| `name` | Invocation name (e.g., `/teach-chromsep`) |
| `description` | Shown in skill listings and help |
| `argument-hint` | Suggests expected arguments to users |

**Invocation examples:**
- `/teach` — Hub skill, helps choose learning path
- `/teach chromsep` or `/teach fundamentals` — Routes to fundamentals
- `/teach-chromsep` — Start fundamentals curriculum
- `/teach-chromsep 2` — Jump to Lab 2 (Isotherms)
- `/teach-process-design` — Start process design curriculum

### Lab Files

Lab files are plain markdown without frontmatter. They contain:

- **Objective** and **Scaffolding level** (HIGH/MEDIUM/LOW)
- **Context** explaining why this topic matters
- **Prediction questions** (critical for POE pedagogy)
- **Experiment sequences** with specific tool calls
- **Key takeaways** summarizing learning outcomes

## Pedagogical Design

### POE Learning Cycle

The curriculum uses **Predict-Observe-Explain**:

1. **Predict**: Ask the student what they expect before running a simulation
2. **Observe**: Run the simulation, present results
3. **Explain**: Compare prediction to outcome, address misconceptions

This approach surfaces and corrects misconceptions that passive instruction misses.

### Process Design Framework

The `/teach-process-design` curriculum introduces a general framework for chromatographic process design before diving into the labs. This framework covers:

1. **Start with requirements** — Define purity specs, yield requirements, throughput targets
2. **Understand your separation** — Know your selectivity (α) and isotherms
3. **Feasibility before optimization** — First ask: "Can I meet all specs simultaneously?"
4. **Find the operating window** — What parameter ranges give feasible solutions?
5. **Optimize within constraints** — Maximize objective while staying feasible
6. **Sensitivity analysis** — Test ±10% on key inputs for robustness
7. **Validate experimentally** — Models guide but don't replace real experiments

This framework is presented before the labs menu to establish the mindset for process design work.

### Scaffolding Levels

Labs progress from high to low scaffolding:

| Level | Instructor Role | Student Role |
|-------|-----------------|--------------|
| HIGH | Explain each step, model thinking | Follow along, ask questions |
| MEDIUM | Guide experiments, prompt interpretation | Make predictions, analyze results |
| LOW | Provide tools and constraints | Design approach, synthesize knowledge |

### Misconception Challenges

Each lab targets specific misconceptions common among students:

- "Doubling feed volume doubles peak height" (Lab 3)
- "In most manufacturing, faster processing is better — does the same apply to chromatography?" (Lab 4)
- "Can we find a single cut time that achieves ≥95% purity AND ≥90% yield for BOTH fractions?" (Process Design Lab 1)

The curriculum deliberately creates situations where these intuitions lead to wrong predictions, making the correction memorable. Opening questions present claims without hints, forcing students to reason from first principles before seeing results.

## Adapting for Your System

These skills were designed for a specific chromatography MCP server, but the patterns apply to any domain.

### Key Adaptation Points

1. **Tool References**: Replace MCP tool names (`run_batch_chromatography`, `plot_simulation_output`, etc.) with your system's equivalents

2. **Default Parameters**: Update the "Default System" section in each SKILL.md with your model compounds and column specifications

3. **Session Management**: The curriculum assumes session-based isolation. Adapt the init/destroy patterns to your system's state management

4. **Output Handling**: Labs reference specific output files (`outlettank01.dat`) and plotting conventions. Update these for your output format

### Creating New Labs

When adding labs, follow this template:

```markdown
# Lab N: Title

**Objective:** One sentence describing what students will learn

**Scaffolding:** HIGH/MEDIUM/LOW — brief justification

---

## Context

Why this topic matters. Connect to real-world applications.

---

## Opening Question

[STOP AFTER THIS QUESTION — wait for student response before continuing]

Present a claim or question that challenges intuition. Do NOT explain
the underlying concepts yet. Wait for the student's reasoning first.

---

## After Opening Question

Once the student responds, introduce the key concepts needed for
the experiment.

---

## Experiment

### Prediction

[STOP AFTER THIS QUESTION — wait for student response before running simulation]

Ask specific prediction questions BEFORE showing any results.
Do NOT provide hints. Let the student reason from prior knowledge.

### Run

Step-by-step simulation sequence with specific parameters.

### Discussion (after simulation)

Only after viewing results, discuss what was observed and why.

---

## Key Takeaways

1. Numbered list of 3-5 main concepts
2. Use bold for key terms
3. Connect back to predictions made earlier
```

Note the `[STOP AFTER THIS QUESTION — wait for student response...]` markers. These are critical for ensuring Claude pauses and waits for student input rather than continuing with explanations.

### Critical Rules for Effective Teaching

These rules are embedded in the SKILL.md files but bear emphasis:

1. **MCP Server Check** — Before starting any lab, verify the `chromsep-http` MCP server is available. If not connected, instruct the student to run `/mcp` to check connection status.

2. **Session Management** — Initialize a session at the start of each lab and destroy it at the end.

3. **Never skip predictions** — The learning happens in the gap between expectation and observation. Require predictions before every simulation.

4. **Questions are stopping points** — When you ask the student a question, STOP IMMEDIATELY. Do not provide additional content, context, explanations, or hints after the question. Wait for the student's response before continuing. This applies to opening questions, prediction questions, and reflection questions.

5. **Don't spoil outcomes** — Never provide hints or explanatory content that reveals answers before the student has responded. Tables, formulas, and concepts that help answer a pending question must come AFTER the student responds, not before.

6. **Image URLs are required** — Always provide the `image_url` from tool responses. Students cannot see plots otherwise.

7. **Use dual units** — Show flow rates as "X mL/min (Y BV/h)" for clarity.

8. **Show, don't tell** — Let simulations reveal concepts rather than lecturing first.

9. **Address misconceptions directly** — When predictions are wrong, explain why explicitly.

## The Model System

The curriculum uses phenylalanine/tryptophan separation as a running example:

| Compound | qmax | K | H = qmax×K |
|----------|------|---|------------|
| Phenylalanine | 50 | 0.05 | 2.5 |
| Tryptophan | 50 | 0.10 | 5.0 |

This system has selectivity α = 2.0, which is suitable for demonstrating both successful separations and the challenges of overlapping peaks at high loading.

Choose a model system for your domain that:
- Has well-characterized parameters
- Demonstrates all phenomena you want to teach
- Has practical relevance students can appreciate

## License

Copyright 2026 Tuomo Sainio

Licensed under the Apache License, Version 2.0. See individual files for SPDX headers.
