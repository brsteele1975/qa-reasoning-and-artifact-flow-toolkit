# QRAFT - QA Reasoning and Artifact Flow Toolkit

AI-driven QA artifact generation exploring how structured LLM agents can reduce manual QA planning workload by 60-80% while keeping human testers in control of validation and exploratory testing.

---

## Project Status

**Phase 1 (Smart Automation) - Complete, tagged v1.0**
A linear pipeline: PRD in, structured test plan out. Three components, each a single LLM call at temperature 0. No memory, no revision. This phase established the risk heuristics, JSON contracts, and severity calibration that carry forward into Phase 2.

**Phase 2 (AI Agents) - In progress on the `feat/v2-dev` branch**
LangChain-based agents with memory, targeted revision, and intent classification. The Conversation Agent is built and tested. Builder Agent is next. See the [v2 branch](https://github.com/brsteele1975/qa-reasoning-and-artifact-flow-toolkit/tree/feat/v2-dev) for current progress.

---

## Why This Exists

Manual QA teams spend significant time interpreting PRDs, drafting structured requirements, writing test plans, and maintaining traceability. This project compresses that effort into an AI workflow so testers can focus on risk validation, exploratory testing, critical thinking, and product quality judgment.

The goal is not to replace QA professionals but to elevate them by removing repetitive artifact construction work.

---

## What Phase 1 Does

A structured AI workflow that:
- Parses a PRD into discrete, testable requirements
- Identifies risk and assigns severity using calibrated heuristics
- Generates classified test cases (unit, integration, e2e, exploratory, non-functional)
- Produces a sprint-scoped Markdown test plan for human review

Constraints:
- Linear pipeline (no orchestration)
- Single LLM call per agent
- Strict JSON output contracts
- Human approval required at all times

### What This Is Not
- Not an autonomous QA system
- Not a CI/CD automation layer
- Not a replacement for exploratory testing
- Not a coverage auditing engine

### Sample Output

The `sample_output/` folder contains reference outputs generated during development across three input types: a clean agile PRD, a messy PRD, and raw meeting notes. These are preserved as examples of what the pipeline produces.

---

## How This System Improves

The workflow is designed to get better through use. During initial testing, severity heuristics were updated to better define the boundaries of the core user journey, specifically to include post-purchase communication as a high severity concern.

The pattern for iteration:
- Human reviewer identifies a consistent gap in agent output
- The agent prompt is updated to encode the fix
- The system is re-run to confirm the correction holds

Reviewers are not just approving output. They are actively improving the system through their judgment.

---

## What's Next

Phase 2 introduces true AI agents: memory across runs, targeted revision (fix one test case without rerunning the pipeline), and inter-agent communication. See `ARCHITECTURE.md` for the full pipeline design.

---

*Open source. Built as a portfolio project exploring AI-augmented QA workflows.*
