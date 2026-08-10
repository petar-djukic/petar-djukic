# Petar Djukic

Principal AI Architect. 20+ years building production systems. PhD in Computer Engineering. 69 US patents.

I design agentic systems that hold up in production — the part that comes after the demo.

**[declarative-agents](https://github.com/Nokia-Bell-Labs/declarative-agents)** — I designed and built this agent framework; **Nokia Bell Labs open-sourced it.** Agents are verifiable state machines: states, signals, and transitions declared in YAML and checked before they run — no dead states, no unhandled signals. Every run is traced end-to-end with OpenTelemetry and can be rolled back. Tools are declared the same way: typed inputs, outputs, side effects, and an undo. Written in Go — built for places where a free-running agent is not acceptable.

Independently, I build a spec-driven code-generation toolchain — coding agents make an ambitious project the work of one person.

## How the projects fit together

```mermaid
graph TD
    CS[cobbler-scaffold<br><i>specs & constitutions</i>] -->|governs| C[cobbler<br><i>agent orchestrator</i>]
    C -->|measure-stitch| P[press<br><i>agent runtime</i>]
    P -->|generates| GUU[go-unix-utils<br><i>123 utilities, 77K LOC</i>]
    C -->|orchestrates| CR[crumbs<br><i>task management</i>]
    CR -->|backtracking support| C
    RA[research-agent<br><i>dynamic tool generation</i>] -.->|same pattern:<br>agent loop| C
    CS -->|test fixture| SHW[sdd-hello-world<br><i>minimal SDD project</i>]

    style C fill:#2d5016,stroke:#4a8c2a,color:#fff
    style CS fill:#1a3a5c,stroke:#2a6cb0,color:#fff
    style P fill:#5c1a3a,stroke:#b02a6c,color:#fff
    style GUU fill:#5c3a1a,stroke:#b07a2a,color:#fff
    style CR fill:#1a3a5c,stroke:#2a6cb0,color:#fff
    style RA fill:#4a2a4a,stroke:#8c4a8c,color:#fff
    style SHW fill:#3a3a3a,stroke:#6a6a6a,color:#fff
```

cobbler is a coding agent orchestrator. cobbler-scaffold provides the YAML specifications and constitutions that govern it. Together they implement a measure-stitch pipeline: the measure agent proposes work from specs, press executes it — invoking the LLM, running tools, and producing code. go-unix-utils is the primary output — 123 Unix utilities regenerated in Go and verified against GNU reference binaries via differential testing. crumbs provides task management with backtracking for the agent loops. research-agent applies the same agent-driven approach to research workflows, generating its own tools on demand rather than relying on pre-defined MCP registries.

The projects are at different stages of maturity:

| Stage | Description | Projects |
|-------|-------------|----------|
| **Fully automated** | End-to-end generation from spec via cobbler | go-unix-utils |
| **Spec complete** | Built manually, awaiting automated building | crumbs |
| **Spec draft** | Specifications in progress | press |

## Projects

**[cobbler](https://github.com/petar-djukic/cobbler)** — A coding agent orchestrator. Manages multi-agent workflows using the Anthropic API, coordinating Claude Code instances through structured agent loops. Handles context window budgeting, task routing, and session continuity across parallel execution.

**[cobbler-scaffold](https://github.com/petar-djukic/cobbler-scaffold)** — Specification constitutions and Mage orchestration for cobbler. YAML schemas govern Claude across design, planning, and execution phases. Implements measure-stitch: specs in, working code out.

**[press](https://github.com/petar-djukic/press)** — Agent runtime for specification-to-code generation. The execution engine inside a cobbler pipeline: takes a specification, invokes the LLM, runs tools, and produces code. The model proposes; the runtime decides what executes. Currently in specification phase.

**[go-unix-utils](https://github.com/petar-djukic/go-unix-utils)** — Go reimplementations of 123 Unix utilities (coreutils, moreutils, grep, findutils), generated from specification using cobbler. Each command is verified for functional parity against the GNU reference binary via differential testing. 77,000 lines of Go across 107 commands, all produced through the measure-stitch pipeline.

**[crumbs](https://github.com/petar-djukic/crumbs)** — A Go library for agent task management. Supports backtracking — agents can revisit and revise earlier decisions rather than treating task completion as one-directional. Built for use with LLM orchestration pipelines. Spec complete, built manually, awaiting automated rebuilding via cobbler.

**[research-agent](https://github.com/petar-djukic/research-agent)** — An end-to-end research workflow backed by a structured knowledge base. Claude generates tools, skills, and retrieval context on demand as research questions arise — rather than pre-defining them via MCP. An active experiment in whether dynamic tool generation makes static tool registries obsolete.

**[coding-skills](https://github.com/petar-djukic/coding-skills)** — Claude Code slash commands for spec-driven development through GitHub issues and pull requests. An issue-per-change workflow — `make-work` plans units, `gh-issue-push` writes them as issues with acceptance criteria, `gh-issue-pop` executes each in its own git worktree and opens the PR — mirrored to Cursor, OpenCode, Codex, and GitHub Copilot from one canonical tree.

**[writing-skills](https://github.com/petar-djukic/writing-skills)** — Claude Code skills that rewrite AI-drafted prose until it reads as human, measured against the Pangram AI detector. A three-step pipeline — structural rewrite, AI-tell removal, cross-model diction — with detector scores recorded before and after each step, plus reference management and citation auditing against a CSL-YAML bibliography.

**[agentic-coding-book](https://github.com/petar-djukic/agentic-coding-book)** — *Agentic Coding*, a book in progress, written in the open: requirements agents can execute, verification the agent cannot grade itself on, and orchestration that scales past one context window. Chapters run first as articles on Mesh Intelligence.

**[agentic-applications-book](https://github.com/petar-djukic/agentic-applications-book)** — *Agentic Applications*, the companion volume: building applications from agents — declared as configuration, with tool contracts, undo, and rollbacks. Based on the Declarative Agents patterns.

**[sdd-hello-world](https://github.com/petar-djukic/sdd-hello-world)** — Minimal spec-driven development test fixture for cobbler-scaffold. A toy project that exercises the full measure-stitch pipeline end-to-end without the complexity of a real codebase.

**[mcp-calc](https://github.com/petar-djukic/mcp-calc)** — A production-grade Model Context Protocol server and agent. 8,000 lines of Go, fully tested. Generated entirely from specification using a manual orchestrator (L3: human-scheduled tasks, agent-implemented). The methodology is described in [The Architecture-First Approach](https://meshintelligence.substack.com/p/the-architecture-first-approach?utm_source=github&utm_campaign=petar-djukic).

## Writing

I write about production AI systems at [Mesh Intelligence](https://meshintelligence.substack.com?utm_source=github&utm_campaign=petar-djukic).

- [How to Build a Writing Pipeline](https://meshintelligence.substack.com/p/how-to-build-a-writing-pipeline?utm_source=github&utm_campaign=petar-djukic) — Writing and fact-checking an article with AI: a draft, a hostile critic that checks every citation, a voice pass, and an SEO pass, behind a human gate
- [How to Stay on Track with Opus 5](https://meshintelligence.substack.com/p/how-to-stay-on-track-with-opus-5?utm_source=github&utm_campaign=petar-djukic) — Opus 5 reads your instructions, agrees with your corrections, then does what it was going to do anyway; the fix is not a better argument
- [How to Use Git Worktrees with Coding Agents](https://meshintelligence.substack.com/p/how-to-use-git-worktrees-with-coding?utm_source=github&utm_campaign=petar-djukic) — One checkout per agent: why parallel coding agents need git worktrees, and where shared checkouts and full clones break
- [How to Loop Engineering](https://meshintelligence.substack.com/p/how-to-loop-engineering?utm_source=github&utm_campaign=petar-djukic) — The human is the loop: running an agent loop with four commands in Claude Code or OpenCode, and staying in charge of it
- [How to Code with GLM 5.2 on OpenCode](https://meshintelligence.substack.com/p/how-to-glm-52-on-opencode?utm_source=github&utm_campaign=petar-djukic) — Decide the architecture and interfaces first, then let a cheap local model write the code on a fixed Ollama plan
- [The Loop Is the Easy Part](https://meshintelligence.substack.com/p/the-loop-is-the-easy-part?utm_source=github&utm_campaign=petar-djukic) — Every coding agent has the same fifty-line loop; the harness is the engineering
- [What Five Coding Agents Taught Me About Building My Own](https://meshintelligence.substack.com/p/what-five-coding-agents-taught-me?utm_source=github&utm_campaign=petar-djukic) — Aider, Goose, SWE-agent, OpenHands, OpenCode, and Claude Code converge on one architecture, and most of it may be unnecessary
- [The Architecture-First Approach](https://meshintelligence.substack.com/p/the-architecture-first-approach?utm_source=github&utm_campaign=petar-djukic) — Spec-driven development with LLM orchestration: architect first, generate second
- [Dude, Where's My Code?](https://meshintelligence.substack.com/p/dude-wheres-my-code?utm_source=github&utm_campaign=petar-djukic) — After 320,000 lines generated and deleted, specs are the source and code is the binary
- [What Level of Autonomy Is Your AI Development Workflow?](https://meshintelligence.substack.com/p/what-level-of-autonomy-is-your-ai?utm_source=github&utm_campaign=petar-djukic) — A six-level taxonomy for agentic coding, from autocomplete to full autonomy
- [Three Commands to a Crude Orchestrator](https://meshintelligence.substack.com/p/three-commands-to-a-crude-orchestrator?utm_source=github&utm_campaign=petar-djukic) — How three Claude skills compose into an agent loop that ships production code
- [What Does $33 of AI Code Generation Buy You?](https://meshintelligence.substack.com/p/what-does-33-of-ai-code-generation?utm_source=github&utm_campaign=petar-djukic) — Cost breakdown of generating 4,586 lines of Go — context loading, not model intelligence, is where tokens go
- [Two Claude Skills and a Worktree Rule](https://meshintelligence.substack.com/p/two-claude-skills-and-a-worktree?utm_source=github&utm_campaign=petar-djukic) — GitHub issues as single source of truth plus git worktrees for human review checkpoints
- [When the Agent Never Stops](https://meshintelligence.substack.com/p/when-the-agent-never-stops?utm_source=github&utm_campaign=petar-djukic) — Agentic burnout is a planning problem, not a tooling problem
- [IT DOESN'T MATTER What Your Favourite Programming Language Is](https://meshintelligence.substack.com/p/it-doesnt-matter-what-your-favourite?utm_source=github&utm_campaign=petar-djukic) — Choose languages based on what works with your AI tools, not personal preference
- [Your AI will be a Black Box Until You Add Logging](https://meshintelligence.substack.com/p/your-ai-will-be-a-black-box-until?utm_source=github&utm_campaign=petar-djukic) — Production-grade logging of token usage and cache behavior is the actual fix for slow, costly AI
- [Running Multiple Claude Code Accounts with Containers](https://meshintelligence.substack.com/p/running-multiple-claude-code-accounts?utm_source=github&utm_campaign=petar-djukic) — Running parallel Claude Code instances in Docker with clean credential boundaries

## Stack

Go · Python · Anthropic API · Claude Code · Model Context Protocol (MCP) · Docker · Linux
