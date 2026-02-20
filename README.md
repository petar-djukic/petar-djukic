# Petar Djukic

Principal Architect. 20 years building production systems. PhD in Computer Engineering. 64 US patents.

I build agentic orchestration systems as a side project — driven by genuine interest and the fact that coding agents make ambitious personal projects tractable for one person.

## Projects

These are independent projects I build in my own time.

**[cobbler](https://github.com/petar-djukic/cobbler)** — A coding agent orchestrator. Manages multi-agent workflows using the Anthropic API, coordinating Claude Code instances through structured agent loops. Handles context window budgeting, task routing, and session continuity across parallel execution.

**[crumbs](https://github.com/petar-djukic/crumbs)** — A Go library for agent task management. Differs from existing tools by supporting backtracking — agents can revisit and revise earlier decisions rather than treating task completion as one-directional. Built for use with LLM orchestration pipelines.

**[cobbler-constitutions](https://github.com/petar-djukic/cobbler-constitutions)** — Templates and schemas for large software specification, designed to be ingestible by coding agents. Similar in intent to git-spec-kit but structured around the full specification lifecycle. Currently testing the lifecycle using a prototype cobbler instance running against these constitutions.

**[mcp-calc](https://github.com/petar-djukic/mcp-calc)** — A production-grade Model Context Protocol server and agent. 8,000 lines of Go, fully tested. Built using the architecture-first methodology described in my writing.

## Writing

I write about production AI systems at [Mesh Intelligence](https://meshintelligence.substack.com).

- [Three Commands to a Crude Orchestrator](https://meshintelligence.substack.com/p/three-commands-to-a-crude-orchestrator) — How three Claude skills compose into an agent loop that ships production code
- [The Architecture-First Approach](https://meshintelligence.substack.com/p/the-architecture-first-approach) — Spec-driven development with LLM orchestration: architect first, generate second
- [What Level Is Your AI Development Workflow?](https://meshintelligence.substack.com) — Applying the TM Forum autonomous networks taxonomy to agentic coding workflows

## Stack

Go · Python · Anthropic API · Claude Code · Model Context Protocol (MCP) · Docker · Linux
