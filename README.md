# Petar Djukic

Principal Architect. 20 years building production systems. PhD in Computer Engineering. 67 US patents.

I build agentic orchestration systems as a side project — driven by genuine interest and the fact that coding agents make ambitious personal projects tractable for one person.

## Projects

These are independent projects I build in my own time.

**[cobbler](https://github.com/petar-djukic/cobbler)** — A coding agent orchestrator. Manages multi-agent workflows using the Anthropic API, coordinating Claude Code instances through structured agent loops. Handles context window budgeting, task routing, and session continuity across parallel execution.

**[crumbs](https://github.com/petar-djukic/crumbs)** — A Go library for agent task management. Differs from existing tools by supporting backtracking — agents can revisit and revise earlier decisions rather than treating task completion as one-directional. Built for use with LLM orchestration pipelines. Generated entirely from specification using a semi-manual orchestrator (L3→L4: the system proposed its own work breakdown from documented intent, with human review before execution).

**[cobbler-scaffold](https://github.com/petar-djukic/cobbler-scaffold)** — Specification constitutions and Mage orchestration for cobbler. YAML schemas govern Claude across design, planning, and execution phases. Implements measure-stitch: specs in, working code out.

**[research-engine](https://github.com/petar-djukic/research-engine)** — An end-to-end research workflow backed by a structured knowledge base. Claude generates tools, skills, and retrieval context on demand as research questions arise — rather than pre-defining them via MCP. An active experiment in whether dynamic tool generation makes static tool registries obsolete.

**[mcp-calc](https://github.com/petar-djukic/mcp-calc)** — A production-grade Model Context Protocol server and agent. 8,000 lines of Go, fully tested. Generated entirely from specification using a manual orchestrator (L3: human-scheduled tasks, agent-implemented). The methodology is described in [The Architecture-First Approach](https://meshintelligence.substack.com/p/the-architecture-first-approach).

## Writing

I write about production AI systems at [Mesh Intelligence](https://meshintelligence.substack.com).

- [IT DOESN'T MATTER What Your Favourite Programming Language Is](https://meshintelligence.substack.com/p/it-doesnt-matter-what-your-favourite) — Choose languages based on what works with your AI tools, not personal preference
- [What Level of Autonomy Is Your AI Development Workflow?](https://meshintelligence.substack.com/p/what-level-of-autonomy-is-your-ai) — Applying the TM Forum autonomous networks taxonomy to agentic coding workflows
- [Three Commands to a Crude Orchestrator](https://meshintelligence.substack.com/p/three-commands-to-a-crude-orchestrator) — How three Claude skills compose into an agent loop that ships production code
- [The Architecture-First Approach](https://meshintelligence.substack.com/p/the-architecture-first-approach) — Spec-driven development with LLM orchestration: architect first, generate second

## Stack

Go · Python · Anthropic API · Claude Code · Model Context Protocol (MCP) · Docker · Linux
