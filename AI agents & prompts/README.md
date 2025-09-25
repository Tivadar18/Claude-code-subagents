# AI Agents & Prompts Workspace

This workspace captures a reusable prompt library, lightweight knowledge base, and orchestration guidelines for the GTM and lead-generation subagents described in the source brief. It is structured so new terminal-capable agents can share common resources, inherit an execution template, and log their work consistently.

## Folder Structure
- `kb/` — summarized enablement notes agents can reference (personas, industries, competitors, legal, tooling, and geo insights).
- `agents/` — drop-in prompt files for each subagent, following the shared execution template.
- `out/` — placeholder for runtime artifacts (not versioned here, but referenced by prompts).
- `Makefile` — convenience entry point for invoking agents with `make run agent=<slug>`.

Refer to the per-agent files for specific inputs, outputs, and success criteria.
