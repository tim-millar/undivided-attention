# Undivided Attention - LLM Exercise Progression Roadmap

1. Transformer in 12 bullets (done)

2. Why attention scales — and where it breaks

3. Why decoder-only models dominate

4. What scaling laws imply for model design

5. Why retrieval and tools are not “add-ons” but structural fixes

6. Why alignment and instruction-following change inference dynamics

---

## Exercise: Undivided Attention I — Transformer Architecture in Twelve Statements
### Context

You are studying the Transformer architecture as introduced in Vaswani et al., “Attention Is All You Need” (2017). This exercise is intended to test and consolidate your conceptual understanding of the model at the level required to reason about performance, scalability, and inference behaviour, rather than implementation detail.

### Task
Produce a note titled “Transformer in 12 Bullets” consisting of exactly twelve bullet points. Each bullet must be:
- A complete, grammatically correct sentence.
- Conceptual rather than procedural (no step-by-step instructions).
- Independent (no bullet should rely on another to be understood).
- Written in your own words.

### Content Requirements
Across the twelve bullets, you must collectively address all of the following:
- The core problem the Transformer was designed to solve.
- The role of self-attention and what it replaces.
- The meaning and function of queries, keys, and values.
- Why attention is scaled and where the scaling factor comes from.
- The purpose of multi-head attention beyond simple parallelism.
- The function of positional information and why it must be injected.
- The role of residual connections in the architecture.
- The role of layer normalization and its placement.
- The distinction between encoder and decoder attention.
- The computational complexity characteristics of self-attention.
- The implications of the architecture for parallelism during training.
- One performance or scaling implication relevant to inference or deployment.

### Constraints
Do not include equations.
Do not include code.
Do not quote directly from the paper.
Do not exceed twelve bullets or combine ideas to “cheat” the count.

### Submission Guidance
Your final note should be understandable to a technically literate engineer who has not read the paper, and it should leave them with a correct mental model of what the Transformer is, why it works, and where its costs lie. Clarity, precision, and conceptual compression are the goals of this exercise.

---

## Exercise: Attention at Scale — Why It Works, and Where It Breaks
### Context

You are studying the attention mechanism as used in modern large language models built on the Transformer architecture. While attention enables powerful modeling of relationships within sequences and supports highly parallel training, it also introduces fundamental computational, memory, and latency constraints that shape how large models are trained, deployed, and used in practice.

This exercise is intended to test and consolidate your understanding of why attention scales effectively, where its limits arise, and how those limits influence real-world LLM systems, rather than your ability to describe architectural components or reproduce implementation details.

### Task

Produce a note titled:

*“Why Attention Scales — and Where It Breaks — in 8 Bullets”*

The note must consist of exactly eight bullet points.

Each bullet must be:

- A single, complete, grammatically correct sentence
- Conceptual rather than procedural (no step-by-step descriptions)
- Independent (no bullet should rely on another to be understood)
- Written in your own words
- Focused on reasoning, not definition

### Content Requirements

Across the eight bullets, you must collectively address all of the following:

- Why attention is more scalable than recurrence for sequence modeling
- How attention enables parallelism during training
- Why attention quality improves with scale and data
- The computational and memory costs inherent to attention
- At least one hard limitation attention introduces as context length grows
- The impact of attention costs on inference latency and deployment
- Why architectural or algorithmic workarounds (e.g., approximations or retrieval) are needed
- One implication of attention’s limits for the future design of LLM systems

You may cover these ideas in any order, but you must not merge multiple requirements into a single bullet to avoid the count.

### Constraints

Do not include equations
Do not include code
Do not quote or paraphrase directly from research papers
Do not reference specific libraries, APIs, or implementations
Do not exceed eight bullets

### Submission Guidance

Your final note should be understandable to a senior software engineer or systems engineer who has not studied the Transformer literature but is capable of reasoning about performance, scalability, and production constraints.

The goal of this exercise is to demonstrate a correct and compressed mental model of attention as a scaling mechanism, a bottleneck, and a design constraint in modern LLM systems.

Clarity, precision, and conceptual compression are the goals of this exercise.
