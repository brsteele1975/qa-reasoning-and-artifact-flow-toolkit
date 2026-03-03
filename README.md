# QRAFT - QA Reasoning and Artifact Flow Toolkit

AI-driven QA artifact generation exploring how structured LLM agents can reduce manual QA planning workload by 60-80% while keeping human testers in control of validation and exploratory testing.

---

## Project Status

This is the active development branch. Phase 1 (smart automation) is complete and tagged as v1.0 on main. This branch is building Phase 2: LangChain-based AI agents with memory, targeted revision, and inter-agent communication.

**Conversation Agent - Complete**
The human-facing portal for the system. Handles two modes: generating a structured request from a raw PRD, and processing reviewer feedback into scoped change instructions for the Builder Agent. See `conversation_agent/README.md` for usage and details.

**Builder Agent - Next**
Reads the Conversation Agent's output and produces requirements, risk assessments, and test cases. Not yet built.

---

## Why This Exists

Manual QA teams spend significant time interpreting PRDs, drafting structured requirements, writing test plans, and maintaining traceability. This project compresses that effort into an AI workflow so testers can focus on risk validation, exploratory testing, critical thinking, and product quality judgment.

The goal is not to replace QA professionals but to elevate them by removing repetitive artifact construction work.

---

## Pipeline

    PRD --> [Conversation Agent] --> generation_request.json
                                  --> revision_request.json + execution_plan.json
                                              |
                                    [Builder Agent]        <-- next
                                              |
                                    [Validators x4]
                                              |
                                    [Critic Agent]
                                              |
                                    test_plan.md

Every arrow can go backwards. Revision requests route to the specific agent that owns the problem. Human review gates are non-negotiable at every stage.

---

## How This System Improves

The workflow is designed to get better through use. When a reviewer identifies a consistent gap in agent output, the prompt is updated to encode the fix and the system is re-run to confirm the correction holds. This is the same discipline as writing a regression test after finding a bug.

Reviewers are not just approving output. They are actively improving the system through their judgment.

---

## Architecture

See ARCHITECTURE.md for the full pipeline design, agent responsibilities, shared field contracts, and the state layer.

See docs/QRAFT_CHARTER.md on main for the project charter, including design principles, scope, and open engineering questions.

---

*Open source. Built as a portfolio project exploring AI-augmented QA workflows.*
