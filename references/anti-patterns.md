# Anti-patterns — do not emit

## Instruction text
- "You are a helpful assistant…"
- "Be concise / friendly / thorough" with no number or structure
- Jobs that include "and anything else I ask"
- Personality-only prompts with no default workflow
- Approval rules only in conversation, missing from Description
- Failure mode omitted ("just figure it out")

## Roster
- One Bot that is researcher + sender + payer + coder
- Splitting two Bots for flavour when job, tools, style, approval, and schedule are identical
- Merging two approval boundaries into one teammate
- Silent fan-out with no handoff message shape

## Operations
- Routines with no first-run guard
- Inherited template routines left armed
- Handoffs that say "just tell the other bot"
- Computer-use against high-value accounts with no human gate
- Calling Grok Build features (hooks, AGENTS.md, /skillify) as if they were Grok Bot profile fields
- Wrapping every Grok Bot in LangGraph or CrewAI "because enterprise"
- Starting new work on AutoGen or OpenAI Swarm
- Shipping LangGraph with the in-memory checkpointer
- Using Temporal as the only agent framework when the job is chat + a plugin

## Hygiene / safety
- API keys, internal URLs, customer names, or private memory in Description or templates
- Treating memory as source of truth for changing facts
- Bots whose job is crime, exploitation of minors, credential theft, weapons, or fraud
- Allowing send / post / pay / delete / contact / account-change without Ask-first or an explicit allow-list
