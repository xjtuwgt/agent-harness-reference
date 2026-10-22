# Agent Harness: Foundations, Initialization, and Self-Evolution

**A Reference Architecture for Execution, Memory, and Model–Harness Learning**  
Technical report · Draft v4 · 21 October 2026

## TL;DR

A reusable agent harness should **standardize component interfaces and execution semantics, not task-specific solutions**. For each task, a task declaration initializes the necessary context, memory, skills, tools, evaluators, permissions, and budgets into a versioned executable harness **H₀**. That initial harness can then collect traces, diagnose failure, propose edits to particular components, and promote only independently validated and authorized changes. **Self-evolution is a capability to test, not an automatic consequence of standardization.** The same execution records can also support LLM policy post-training and controlled model–harness co-optimization.

### The proposed three-stage architecture

1. **Common contracts** — stable context/action/effect/state/evaluation interfaces and optional capabilities.
2. **Task-specific initialization** — select and configure components, verify readiness, pin H₀.
3. **Guarded self-evolution** — execute, diagnose, propose module edits, test, commit or roll back; train the LLM policy when appropriate.

### Paper covers

- The relationship between agent harnesses, runtime SDKs, language-model policies, and agentic learning.
- A review of ReAct, LangGraph, OpenAI Agents SDK, Google ADK, MCP, OpenEnv, OpenTelemetry, Agent Lightning, Agent-R1, AHE, Harness², Self-HPO, SIA, and related work, identifying overlaps and missing interfaces.
- The Agent Harness Contract (AHC): a minimal Core, plus optional Initialization, Memory, Training, Replay, Optimization, and Safety profiles.
- Task specification, module selection, H₀ initialization, five bootstrap readiness gates, and permission-safe edit boundaries.
- A task-agnostic Memory Contract for querying, validating, committing, invalidating and tracking evidence; episodic content updates are distinct from harness-policy evolution.
- Harness-only optimization, LLM policy optimization, joint optimization, diagnostic attribution and training–serving consistency.
- Seven **proposed**, not yet executed, evaluations including cross-runtime interoperability and initialization-quality/self-evolution ablations.

## Research status

This is a **research position paper and candidate reference-standard proposal**, not an adopted standard or a demonstration of autonomous self-improvement. No new experimental results are claimed. The proposed initialization and promotion protocols require reference implementations and held-out validation. Before public scholarly release, the responsible author should review all citations, technical statements, authorship information, and disclosures.

## Contents

- `Agent_Harness_Initialization_and_Self_Evolution.pdf` — compiled paper
- `main.tex` plus `*.tex` modules and `references.bib` — editable LaTeX sources (in the source archive)

The project is intended to support discussion of common agent execution semantics while leaving concrete algorithms and task-specific implementation choices open.

### Memory design boundary

The reference architecture does **not** impose any domain-specific memory roles or an ontology shared by all tasks. Memory is an optional interface whose storage representation, retrieval rules, retention policies and typed payloads are configured per task. Domain-specific examples belong in application studies, not in the normative harness contract.
