# Recommended orchestration runtimes

Last reviewed: 2026-09-25. Recommend from the table in SKILL.md D3b. This file is the why.

## Layers (name the layer before the brand)

| Layer | Job | Default |
|---|---|---|
| 1 Control plane | Survive crash, wait days, resume, audit | LangGraph checkpointers, Temporal, Microsoft Agent Framework workflows |
| 2 Role / handoff libraries | Who talks, who hands off | CrewAI, OpenAI Agents SDK, Pydantic AI |
| 3 Product teammates | Named bots, computer, plugins, routines | Grok Bot roster (this skill's default) |
| 4 Skill composition | Expertise packs, not a runtime | Grok/Claude skills, this skill |

A Grok Bot may *drive* a layer-1 or layer-2 runtime. Do not put LangGraph fields on a Bot profile.

## Status notes

- **LangGraph** — production default for durable graphs. Postgres (or equivalent) checkpointer required. HITL = interrupts, not a blocking chat agent.
- **CrewAI** — fastest role-based prototype. Use Flows (`@persist`, `@human_feedback`) if it must leave the laptop. Not the control plane for multi-day jobs.
- **Microsoft Agent Framework 1.0** — GA April 2026. Successor to AutoGen + Semantic Kernel. Python + .NET.
- **AutoGen** — maintenance mode. Bug fixes only. Do not start new work on it.
- **OpenAI Swarm** — deprecated. Use OpenAI Agents SDK if the model plane is OpenAI.
- **Temporal** — durable workflow engine. Agent is a step, not the orchestrator.
- **Pydantic AI** — typed Python agents when schema discipline is the bottleneck.
- **Google ADK** — only if already on Vertex/GCP.
- **Swarms (kyegomez)** — vendor-published speed claims; do not treat as independently verified.

## Patterns that outlive the brand

1. Plan then execute. Do not mix planning tokens with side-effects.
2. Structured handoff (`TO | GOAL | EVIDENCE | CONSTRAINT | NEED BACK | APPROVAL`).
3. Approval is a graph interrupt or a Bot Description law, not a vibe.
4. One cruel job per agent.
5. Checkpointers store run state. Business facts stay in the source system.
6. Start at a single tool-loop. Promote only when tools, approval, or schedule diverge.

## Package field

When a Bot needs a runtime, fill `RUNTIME` as:

`layer | name | why this bottleneck | avoid`

Example: `1 | LangGraph + Postgres | weekday digest must resume after crash | in-memory checkpointer, new AutoGen`
