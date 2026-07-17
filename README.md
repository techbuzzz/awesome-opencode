<div align="center">

<img src="https://raw.githubusercontent.com/sindresorhus/awesome/main/media/badge.svg" alt="Awesome" />
<img src="https://img.shields.io/github/stars/techbuzzz/awesome-opencode?style=social" alt="Stars" />
<img src="https://img.shields.io/github/forks/techbuzzz/awesome-opencode?style=social" alt="Forks" />
<img src="https://img.shields.io/badge/OpenCode-Compatible-blueviolet" alt="OpenCode Compatible" />
<img src="https://img.shields.io/badge/PRs-Welcome-brightgreen" alt="PRs Welcome" />
<img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License" />

# 🚀 Awesome OpenCode

**A curated collection of skills, plugins, agents, MCP servers, configs, and tips for [OpenCode](https://opencode.ai) — the AI coding agent for the terminal.**

*Focused on: **C# · .NET · Go · C++ · TypeScript · JavaScript · Astro · Tailwind CSS***

[Website](https://opencode.ai) · [Discord](https://discord.gg/opencode) · [Contributing](CONTRIBUTING.md) · [Report Issue](https://github.com/techbuzzz/awesome-opencode/issues)

</div>

---

## 📖 Contents

- [🚀 Getting Started](#-getting-started)
- [🧠 Skills](#-skills)
  - [By Language & Stack](#by-language--stack)
  - [Development Workflow](#development-workflow)
  - [Universal / Cross-Stack](#universal--cross-stack)
- [🔌 Plugins](#-plugins)
  - [Orchestration & Multi-Agent](#orchestration--multi-agent)
  - [Memory & Context](#memory--context)
  - [Productivity & Notifications](#productivity--notifications)
  - [Code Quality & Review](#code-quality--review)
  - [Security](#security)
- [🛠️ MCP Servers](#️-mcp-servers)
  - [Essential / Starter Pack](#essential--starter-pack)
  - [Development & Code](#development--code)
  - [Databases](#databases)
  - [Web & Browser](#web--browser)
  - [DevOps & Infrastructure](#devops--infrastructure)
  - [Communication & Productivity](#communication--productivity)
  - [AI & LLMs](#ai--llms)
- [🤖 Agents](#-agents)
- [⚙️ Configuration](#️-configuration)
  - [opencode.jsonc Examples](#opencodejsonc-examples)
  - [AGENTS.md Templates](#agentsmd-templates)
- [💡 Tips & Tricks](#-tips--tricks)
- [🎨 Themes](#-themes)
- [📚 Resources & Learning](#-resources--learning)
- [🤝 Contributing](#-contributing)

---

## 🚀 Getting Started

### Install OpenCode

```bash
# via npm
npm install -g opencode-ai

# via curl (macOS/Linux)
curl -fsSL https://opencode.ai/install.sh | sh

# via Homebrew
brew install opencode-ai/tap/opencode
```

### Quick Setup

```bash
# Run in your project directory
opencode

# Or with a specific model
opencode --model anthropic/claude-sonnet-4-5

# Check MCP servers
opencode mcp list
```

### Install a Skill

```bash
# Using npx skills CLI (recommended)
npx skills add <owner/repo>

# Or clone manually
git clone https://github.com/owner/skill-repo ~/.agents/skills/skill-name

# Project-local skill
mkdir -p .opencode/skills/my-skill && cp SKILL.md .opencode/skills/my-skill/
```

> **Skill Discovery Paths:**
> | Scope | Path | Convention |
> |-------|------|------------|
> | Project | `.opencode/skills/` | OpenCode-native |
> | Project | `.claude/skills/` | Claude Code-compatible |
> | Project | `.agents/skills/` | Agent Skills open standard |
> | Global | `~/.config/opencode/skills/` | OpenCode-native |
> | Global | `~/.claude/skills/` | Claude Code-compatible |
> | Global | `~/.agents/skills/` | Agent Skills open standard |

---

## 🧠 Skills

Skills are reusable `SKILL.md` instruction packages that teach OpenCode how to handle specific tasks. Skills are loaded on-demand — the agent only reads the full body when the skill is relevant, keeping context lean.

### By Language & Stack

#### C# & .NET

| Skill | Description | Install |
|-------|-------------|---------|
| **[dotnet-expert](skills/dotnet-expert/)** | C#/.NET best practices: async/await, Entity Framework, ASP.NET Core, SOLID principles | [↓ Local](skills/dotnet-expert/SKILL.md) |
| **[csharp-testing](https://github.com/topics/csharp-opencode-skill)** | xUnit/NUnit/MSTest patterns, mocking with Moq/NSubstitute, integration tests | `npx skills add dotnet/csharp-testing` |
| **[aspnetcore-api](https://github.com/topics/aspnetcore-skill)** | REST API design with ASP.NET Core: minimal APIs, controllers, middleware, Swagger | - |
| **[dotnet-architecture](https://github.com/topics/dotnet-skill)** | Clean Architecture, DDD, CQRS with MediatR patterns for .NET | - |
| **[ef-core](https://github.com/topics/efcore-skill)** | Entity Framework Core: migrations, queries, performance, relationships | - |
| **[blazor-skill](https://github.com/topics/blazor-skill)** | Blazor Server/WASM component patterns, state management, JS interop | - |
| **[azure-dotnet](https://github.com/topics/azure-dotnet-skill)** | Azure SDK for .NET: Service Bus, Blob Storage, Functions, KeyVault | - |
| **[nuget-publishing](https://github.com/topics/nuget-skill)** | NuGet package creation, versioning, publishing to nuget.org | - |

#### Go

| Skill | Description | Install |
|-------|-------------|---------|
| **[go-expert](skills/go-expert/)** | Go idioms, error handling, goroutines, interfaces, modules | [↓ Local](skills/go-expert/SKILL.md) |
| **[go-testing](https://github.com/topics/go-testing-skill)** | Table-driven tests, subtests, benchmarks, testify, mocking | - |
| **[go-microservices](https://github.com/topics/go-microservices-skill)** | gRPC, HTTP servers, middleware, observability, Docker | - |
| **[go-cli](https://github.com/topics/go-cli-skill)** | CLI tools with cobra/urfave, flags, subcommands, config | - |
| **[go-generics](https://github.com/topics/go-generics-skill)** | Generic types, constraints, type parameters (Go 1.18+) | - |
| **[go-concurrency](https://github.com/topics/go-concurrency-skill)** | Goroutines, channels, sync primitives, context cancellation | - |
| **[gopls-mcp](https://go.dev/gopls/features/mcp)** | Go language server as MCP — code nav, analysis, refactoring | Via gopls |

#### TypeScript & JavaScript

| Skill | Description | Install |
|-------|-------------|---------|
| **[typescript-expert](https://github.com/topics/typescript-skill)** | Advanced TypeScript: generics, decorators, mapped types, utility types | - |
| **[typescript-astro](skills/typescript-astro/)** | Astro framework patterns, islands, SSR/SSG, content collections | [↓ Local](skills/typescript-astro/SKILL.md) |
| **[node-api](https://github.com/topics/nodejs-skill)** | Node.js REST/GraphQL APIs with Express, Fastify, Hono | - |
| **[react-patterns](https://github.com/topics/react-skill)** | React hooks, context, performance, testing with RTL | - |
| **[nextjs-expert](https://github.com/topics/nextjs-skill)** | Next.js App Router, Server Components, RSC, Route Handlers | - |
| **[vitest-skill](https://github.com/topics/vitest-skill)** | Unit and integration testing with Vitest | - |
| **[bun-skill](https://github.com/topics/bun-skill)** | Bun runtime, bundler, test runner patterns | - |

#### Astro & Tailwind CSS

| Skill | Description | Install |
|-------|-------------|---------|
| **[astro-skill](skills/typescript-astro/)** | Astro v4/v5: components, layouts, routing, integrations, Starlight | [↓ Local](skills/typescript-astro/SKILL.md) |
| **[tailwind-ui](skills/tailwind-ui/)** | Tailwind CSS v4 patterns, design systems, component variants, dark mode | [↓ Local](skills/tailwind-ui/SKILL.md) |
| **[tailwind-components](https://github.com/topics/tailwind-skill)** | Building reusable Tailwind component libraries, CVA, shadcn/ui patterns | - |
| **[astro-seo](https://github.com/topics/astro-seo-skill)** | SEO optimization for Astro: meta tags, sitemaps, structured data | - |
| **[astro-content](https://github.com/topics/astro-content-skill)** | Content collections, MDX, Markdown processing in Astro | - |

#### C++

| Skill | Description | Install |
|-------|-------------|---------|
| **[cpp-modern](https://github.com/topics/cpp-skill)** | Modern C++17/20/23: RAII, smart pointers, ranges, concepts | - |
| **[cmake-skill](https://github.com/topics/cmake-skill)** | CMake build system, targets, dependencies, CPM | - |
| **[cpp-testing](https://github.com/topics/cpp-testing-skill)** | Google Test, Catch2, benchmark testing | - |
| **[cpp-performance](https://github.com/topics/cpp-perf-skill)** | Profiling, cache optimization, SIMD, memory layout | - |
| **[vcpkg-skill](https://github.com/topics/vcpkg-skill)** | vcpkg package manager, manifests, triplets | - |

---

### Development Workflow

| Skill | Description | Install |
|-------|-------------|---------|
| **[Firecrawl](https://github.com/mendableai/firecrawl)** | Live web access: search, scrape, crawl, browser interaction | `npx -y firecrawl-cli@latest init --all` |
| **[Handoff](https://github.com/mattpocock/skills)** | Compress session into markdown for continuity or delegation | `npx skills@latest add mattpocock/skills` |
| **[Grill Me](https://github.com/mattpocock/skills)** | Interviews you relentlessly about a plan before any code is written | `npx skills add mattpocock/skills --skill grill-me` |
| **[Obra Superpowers](https://github.com/obra/superpowers)** | Full multi-agent dev framework: TDD, worktrees, subagents, debugging | See [docs](https://github.com/obra/superpowers) |
| **[Understand-Anything](https://github.com/Egonex-AI/Understand-Anything)** | Turns any codebase into interactive knowledge graph with semantic search | `curl -fsSL .../install.sh \| bash -s opencode` |
| **[Caveman](https://github.com/JuliusBrussee/caveman)** | Cuts output tokens ~65% by stripping narration, keeps all facts | `curl -fsSL .../install.sh \| bash` |
| **[stop-slop](https://github.com/hardikpandya/stop-slop)** | Strips AI writing tells: em dashes, jargon, throat-clearing | `git clone ... ~/.agents/skills/stop-slop` |
| **[skill-optimizer](https://github.com/hqhq1025/skill-optimizer)** | Mines session history for skill-worthy workflows, personalizes skills | See [docs](https://github.com/hqhq1025/skill-optimizer) |
| **[tdd](skills/tdd/)** | Test-Driven Development workflow for any language | [↓ Local](skills/tdd/SKILL.md) |
| **[git-flow](skills/git-flow/)** | Git branching, PR workflow, commit conventions, changelogs | [↓ Local](skills/git-flow/SKILL.md) |
| **[code-review](skills/code-review/)** | Structured code review: security, performance, maintainability | [↓ Local](skills/code-review/SKILL.md) |

---

### Universal / Cross-Stack

| Skill | Description |
|-------|-------------|
| **[MCP Builder](https://github.com/composiohq/awesome-claude-skills)** | Guides creation of high-quality MCP servers |
| **[software-architecture](https://github.com/composiohq/awesome-claude-skills)** | Design patterns, SOLID, DDD, hexagonal architecture |
| **[test-driven-development](https://github.com/Prat011/awesome-llm-skills)** | TDD cycle for any language or framework |
| **[Changelog Generator](https://github.com/composiohq/awesome-claude-skills)** | Auto-creates changelogs from git commits |
| **[security-audit](skills/security-audit/)** | OWASP checks, secret scanning, dependency audit | 
| **[using-git-worktrees](https://github.com/composiohq/awesome-claude-skills)** | Isolated git worktrees for parallel development |
| **[root-cause-tracing](https://github.com/Prat011/awesome-llm-skills)** | Trace back execution errors to original triggers |
| **[Skill Creator](https://github.com/composiohq/awesome-claude-skills)** | Guidance for creating effective skills from scratch |
| **[Composio](https://github.com/composiohq/awesome-claude-skills)** | 1000+ SaaS integrations: GitHub, Linear, Slack, Stripe | `npx skills add composiohq/skills` |

---

## 🔌 Plugins

Plugins are JavaScript/TypeScript modules that hook into OpenCode runtime events. Unlike skills (which instruct the agent), plugins change how OpenCode itself behaves.

### Orchestration & Multi-Agent

| Plugin | Description | Stars |
|--------|-------------|-------|
| **[FlowDeck](https://github.com/awesome-opencode/awesome-opencode)** | 25 specialist agents, 4-phase cycle: discuss → plan → execute → review | ⭐ |
| **[CrewBee](https://github.com/awesome-opencode/awesome-opencode)** | Task-specific agent teams with built-in coding+review team | ⭐ |
| **[OpenCode Ensemble](https://github.com/awesome-opencode/awesome-opencode)** | Parallel agent teams | ⭐ |
| **[OpenCode Swarm](https://github.com/awesome-opencode/awesome-opencode)** | Verification-gated swarm intelligence | ⭐ |
| **[Open Conclave](https://github.com/awesome-opencode/awesome-opencode)** | Multi-agent debates moderated by a captain agent | ⭐ |
| **[hiai-opencode](https://github.com/awesome-opencode/awesome-opencode)** | Canonical 12-agent model with bundled skills, MCP, LSP | ⭐ |
| **[Background Agents](https://github.com/awesome-opencode/awesome-opencode)** | Async agent delegation for background tasks | ⭐ |
| **[Subagent Reporter](https://github.com/awesome-opencode/awesome-opencode)** | See exactly what your subagents are doing | ⭐ |

### Memory & Context

| Plugin | Description |
|--------|-------------|
| **[Harness Memory](https://github.com/awesome-opencode/awesome-opencode)** | Auto-captures evidence from tool interactions, structured memory |
| **[Honcho](https://github.com/awesome-opencode/awesome-opencode)** | AI-native long-term memory |
| **[Magic Context](https://github.com/awesome-opencode/awesome-opencode)** | Lossless context management with background compression |
| **[Opencode Mem](https://github.com/awesome-opencode/awesome-opencode)** | Persistent memory with vector database |
| **[oc-mnemoria](https://github.com/awesome-opencode/awesome-opencode)** | Persistent shared memory (hive mind) for agent teams |
| **[Simple Memory](https://github.com/awesome-opencode/awesome-opencode)** | Git-based memory |
| **[Dynamic Context Pruning](https://github.com/awesome-opencode/awesome-opencode)** | Optimize token usage automatically |
| **[opencode-short-term-memory](https://github.com/awesome-opencode/awesome-opencode)** | Maintain user instructions throughout long sessions |

### Productivity & Notifications

| Plugin | Description |
|--------|-------------|
| **[Opencode Notify](https://github.com/awesome-opencode/awesome-opencode)** | Native OS notifications |
| **[WakaTime](https://github.com/awesome-opencode/awesome-opencode)** | WakaTime coding time tracking integration |
| **[Opencode Token Tracker](https://github.com/awesome-opencode/awesome-opencode)** | Real-time token usage, cost, and latency tracking |
| **[Smart Title](https://github.com/awesome-opencode/awesome-opencode)** | Auto-generate meaningful session titles |
| **[Opencode Worktree](https://github.com/awesome-opencode/awesome-opencode)** | Zero-friction git worktrees |
| **[Opencode Snippets](https://github.com/awesome-opencode/awesome-opencode)** | Instant inline text expansion |
| **[Vibe Coding Slack Notifier](https://github.com/awesome-opencode/awesome-opencode)** | Slack DM alerts for task completion |
| **[Morph Fast Apply](https://github.com/awesome-opencode/awesome-opencode)** | 10,500+ tokens/sec code editing |
| **[Opencode Quota](https://github.com/awesome-opencode/awesome-opencode)** | Quota toasts and real-time token tracking |

### Code Quality & Review

| Plugin | Description |
|--------|-------------|
| **[opencode-review](https://github.com/awesome-opencode/awesome-opencode)** | Automatic structured code review on every change |
| **[Tree-sitter Language Pack](https://github.com/awesome-opencode/awesome-opencode)** | Code intelligence for 300+ languages |
| **[TypeUI](https://github.com/awesome-opencode/awesome-opencode)** | Design systems, UI prompts, and layout variation guidance |
| **[OpenCodeRAG](https://github.com/awesome-opencode/awesome-opencode)** | Local-first RAG plugin for semantic code search |
| **[Ralph Wiggum](https://github.com/awesome-opencode/awesome-opencode)** | Self-correcting agent loops |
| **[Semantic Anchors](https://github.com/awesome-opencode/awesome-opencode)** | Runtime contract enforcement |

### Security

| Plugin | Description |
|--------|-------------|
| **[Envsitter Guard](https://github.com/awesome-opencode/awesome-opencode)** | Prevents `.env` and secrets from leaking to the agent |
| **[CC Safety Net](https://github.com/awesome-opencode/awesome-opencode)** | Safety net catching destructive shell commands |
| **[Cupcake](https://github.com/awesome-opencode/awesome-opencode)** | Policy enforcement layer for agent actions |

---

## 🛠️ MCP Servers

Model Context Protocol servers extend OpenCode with external tools and services. Add them to your `opencode.jsonc`:

> ⚠️ **Context Warning:** Each MCP server adds tool definitions to every LLM turn. Be selective — a GitHub MCP server alone can consume 10k+ tokens. Use [glob patterns](#managing-mcp-servers) to disable globally and enable per-agent.

### Essential / Starter Pack

| Server | Description | Config |
|--------|-------------|--------|
| **[Context7](https://context7.com)** | Up-to-date library docs — prevents hallucinating outdated APIs | [↓ Config](#context7) |
| **[GitHub MCP](https://github.com/github/github-mcp-server)** | Repos, PRs, issues, code search, actions | [↓ Config](#github) |
| **[Filesystem](https://github.com/modelcontextprotocol/servers)** | Read/write local files | [↓ Config](#filesystem) |
| **[Grep by Vercel](https://grep.app)** | Search code snippets across GitHub | [↓ Config](#grep-by-vercel) |
| **[Sentry](https://sentry.io)** | Query Sentry projects, issues, error data | [↓ Config](#sentry) |

### Development & Code

| Server | Description | Install |
|--------|-------------|---------|
| **[gopls MCP](https://go.dev/gopls/features/mcp)** | Go language server: code nav, analysis, refactoring | `gopls mcp` |
| **[go-dev-mcp](https://github.com/fpt/go-dev-mcp)** | Go/Rust/Python docs, GitHub code search, diffs | `npx -y go-dev-mcp` |
| **[dotnet-mcp](https://learn.microsoft.com/dotnet/ai/quickstarts/build-mcp-server)** | .NET/C# tools via ModelContextProtocol SDK | Custom |
| **[Playwright](https://github.com/microsoft/playwright-mcp)** | Browser automation for testing and web interaction | `npx -y @playwright/mcp` |
| **[Stagehand](https://github.com/browserbase/stagehand)** | AI-native browser control | `npx -y @browserbasehq/stagehand-mcp` |
| **[opencode-mcp](https://github.com/AlaeddineMessadi/opencode-mcp)** | Delegate coding tasks to OpenCode from other AI clients | `npx -y opencode-mcp` |
| **[Firecrawl MCP](https://github.com/mendableai/firecrawl-mcp-server)** | Web scraping, crawling, search with clean markdown output | `npx -y firecrawl-mcp` |
| **[AgentDeals](https://github.com/awesome-opencode/awesome-opencode)** | MCP aggregating developer tool deals | - |

### Databases

| Server | Description | Install |
|--------|-------------|---------|
| **[PostgreSQL](https://github.com/modelcontextprotocol/servers)** | Safe read-only SQL against PostgreSQL | `npx -y @modelcontextprotocol/server-postgres` |
| **[SQLite](https://github.com/modelcontextprotocol/servers)** | Local SQLite database operations | `npx -y @modelcontextprotocol/server-sqlite` |
| **[Supabase](https://github.com/supabase-community/supabase-mcp)** | Full Supabase access: DB, auth, storage, edge functions | `npx -y @supabase/mcp-server-supabase` |
| **[MongoDB](https://github.com/mongodb-developer/mongodb-mcp-server)** | MongoDB queries and aggregations | `npx -y @mongodb-js/mongodb-mcp` |
| **[Redis](https://github.com/redis/mcp-redis)** | Redis cache operations | `npx -y @redis/mcp-redis` |

### Web & Browser

| Server | Description | Install |
|--------|-------------|---------|
| **[Playwright MCP](https://github.com/microsoft/playwright-mcp)** | Full browser automation via accessibility snapshots | `npx -y @playwright/mcp` |
| **[Puppeteer](https://github.com/modelcontextprotocol/servers)** | Chrome DevTools Protocol automation | `npx -y @modelcontextprotocol/server-puppeteer` |
| **[Fetch](https://github.com/modelcontextprotocol/servers)** | HTTP requests, web scraping | `npx -y @modelcontextprotocol/server-fetch` |
| **[Firecrawl](https://github.com/mendableai/firecrawl-mcp-server)** | Advanced web crawling and scraping | `npx -y firecrawl-mcp` |

### DevOps & Infrastructure

| Server | Description | Install |
|--------|-------------|---------|
| **[Docker](https://github.com/docker/mcp-servers)** | Container management, images, compose | `npx -y @docker/mcp` |
| **[Kubernetes](https://github.com/kubernetes-sigs/mcp-kubernetes)** | K8s cluster management | `npx -y k8s-mcp` |
| **[Terraform](https://github.com/hashicorp/terraform-mcp-server)** | Terraform operations via HashiCorp | Custom |
| **[AWS](https://github.com/aws-samples/amazon-bedrock-mcp-server)** | AWS services access | Custom |
| **[Azure](https://github.com/microsoft/azure-mcp)** | Azure resource management | Custom |
| **[Vercel](https://github.com/vercel/mcp-adapter)** | Vercel deployments, projects, domains | Remote |
| **[Cloudflare](https://developers.cloudflare.com/mcp)** | Workers, KV, R2, D1, Tunnels | Remote |

### Communication & Productivity

| Server | Description | Install |
|--------|-------------|---------|
| **[Slack MCP](https://github.com/modelcontextprotocol/servers)** | Send messages, read channels | `npx -y @modelcontextprotocol/server-slack` |
| **[Linear](https://github.com/linear/linear-mcp-server)** | Issues, projects, cycles | `npx -y @linear/mcp-server` |
| **[Jira](https://github.com/atlassian/mcp-atlassian)** | Jira issues, sprints, boards | Remote |
| **[Notion](https://github.com/makenotion/notion-mcp-server)** | Read/write Notion pages, databases | `npx -y @notionhq/mcp` |
| **[GitHub Actions](https://github.com/github/github-mcp-server)** | Trigger and monitor CI/CD pipelines | Via GitHub MCP |

### AI & LLMs

| Server | Description | Install |
|--------|-------------|---------|
| **[Composio](https://composio.dev/mcp)** | 1000+ app integrations via single MCP gateway | Remote |
| **[LiteLLM](https://github.com/BerriAI/litellm)** | Proxy for 143+ LLM providers | `npx -y opencode-litellm` |
| **[Ejentum](https://github.com/awesome-opencode/awesome-opencode)** | Reasoning, code, anti-deception, and memory tools | - |

---

### MCP Configuration Examples

Copy-paste these configs into your `opencode.jsonc` under the `"mcp"` section:

#### Context7

```jsonc
"context7": {
  "type": "remote",
  "url": "https://mcp.context7.com/mcp",
  "enabled": true
}
```

**Usage:** Add `use context7` to your prompts.

#### GitHub

```jsonc
"github": {
  "type": "remote",
  "url": "https://api.githubcopilot.com/mcp/",
  "oauth": {},
  "enabled": false
}
```

**Authenticate:** `opencode mcp auth github`  
**Usage:** Add `use the github tool` to your prompts.

#### Filesystem

```jsonc
"filesystem": {
  "type": "local",
  "command": ["npx", "-y", "@modelcontextprotocol/server-filesystem", "."],
  "enabled": true
}
```

#### Grep by Vercel

```jsonc
"gh_grep": {
  "type": "remote",
  "url": "https://mcp.grep.app",
  "enabled": true
}
```

**Usage:** `use the gh_grep tool to find examples of [pattern]`

#### Sentry

```jsonc
"sentry": {
  "type": "remote",
  "url": "https://mcp.sentry.dev/mcp",
  "oauth": {},
  "enabled": false
}
```

**Authenticate:** `opencode mcp auth sentry`

---

### Managing MCP Servers

**Disable globally, enable per-agent (recommended for large setups):**

```jsonc
// opencode.jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "github": { "type": "remote", "url": "https://api.githubcopilot.com/mcp/" },
    "playwright": { "type": "local", "command": ["npx", "-y", "@playwright/mcp"] }
  },
  "tools": {
    "github_*": false,      // disable GitHub tools globally
    "playwright_*": false   // disable Playwright globally
  },
  "agent": {
    "pr-reviewer": {
      "tools": { "github_*": true }  // enable only for this agent
    },
    "e2e-tester": {
      "tools": { "playwright_*": true }
    }
  }
}
```

**Debug MCP connectivity:**
```bash
opencode mcp list                    # list all servers + auth status
opencode mcp debug <server-name>     # diagnose connection + OAuth
opencode mcp auth <server-name>      # trigger OAuth flow
opencode mcp logout <server-name>    # clear stored tokens
```

---

## 🤖 Agents

Custom agents defined in `.opencode/agents/` with YAML frontmatter.

| Agent | Description |
|-------|-------------|
| **[Agentic](https://github.com/awesome-opencode/awesome-opencode)** | Modular AI agents for complex workflows |
| **[Claude Subagents](https://github.com/awesome-opencode/awesome-opencode)** | Claude Code subagents reference collection |
| **[deliberation](https://github.com/awesome-opencode/awesome-opencode)** | Expert subagents for second opinions via MCP |
| **[Gem Team](https://github.com/awesome-opencode/awesome-opencode)** | Multi-agent orchestration harness |
| **[NERV](https://github.com/awesome-opencode/awesome-opencode)** | Invisible engineering infrastructure for AI agents |
| **[server-manager](https://github.com/awesome-opencode/awesome-opencode)** | Non-blocking background server management |
| **[Python Expert Agent](https://github.com/awesome-opencode/awesome-opencode)** | Python Expert Agent toolkit |

**Create your own agent** in `.opencode/agents/my-agent.md`:

```yaml
---
name: dotnet-reviewer
description: Expert C# and .NET code reviewer focusing on performance and best practices
model: anthropic/claude-sonnet-4-5
tools:
  bash: false       # read-only agent
  write: false
  skill: true
permission:
  skill:
    "code-review": "allow"
    "dotnet-expert": "allow"
    "*": "deny"
---

You are an expert C#/.NET architect with 15+ years of experience.
Focus on: async patterns, memory management, LINQ optimization, and Clean Architecture.
Always check for: null reference exceptions, proper disposal of IDisposable, and thread safety.
```

---

## ⚙️ Configuration

### opencode.jsonc Examples

**Starter config for .NET / Go / TypeScript projects:**

```jsonc
// ~/.config/opencode/opencode.jsonc (global)
{
  "$schema": "https://opencode.ai/config.json",
  "autoupdate": true,
  "model": "anthropic/claude-sonnet-4-5",
  
  "mcp": {
    "context7": {
      "type": "remote",
      "url": "https://mcp.context7.com/mcp",
      "enabled": true
    },
    "filesystem": {
      "type": "local",
      "command": ["npx", "-y", "@modelcontextprotocol/server-filesystem", "."],
      "enabled": true
    },
    "gh_grep": {
      "type": "remote",
      "url": "https://mcp.grep.app",
      "enabled": false
    },
    "playwright": {
      "type": "local",
      "command": ["npx", "-y", "@playwright/mcp"],
      "enabled": false
    }
  },
  
  "tools": {
    "gh_grep_*": false,
    "playwright_*": false
  },
  
  "permission": {
    "skill": {
      "*": "allow",
      "experimental-*": "ask"
    }
  },
  
  "instructions": [
    "AGENTS.md",
    "docs/ARCHITECTURE.md"
  ]
}
```

**Project-level config for ASP.NET Core API:**

```jsonc
// ./opencode.jsonc (project root)
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "postgres": {
      "type": "local",
      "command": ["npx", "-y", "@modelcontextprotocol/server-postgres"],
      "environment": {
        "POSTGRES_CONNECTION_STRING": "{env:DATABASE_URL}"
      },
      "enabled": true
    },
    "sentry": {
      "type": "remote",
      "url": "https://mcp.sentry.dev/mcp",
      "oauth": {}
    }
  },
  "instructions": [
    "AGENTS.md",
    "src/README.md"
  ]
}
```

**Config for Go microservices:**

```jsonc
// ./opencode.jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "gopls": {
      "type": "local",
      "command": ["gopls", "mcp"],
      "enabled": true
    },
    "github": {
      "type": "remote",
      "url": "https://api.githubcopilot.com/mcp/",
      "oauth": {},
      "enabled": false
    }
  },
  "tools": { "github_*": false },
  "agent": {
    "pr-reviewer": {
      "tools": { "github_*": true }
    }
  }
}
```

**Config for Astro + Tailwind frontend:**

```jsonc
// ./opencode.jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "playwright": {
      "type": "local",
      "command": ["npx", "-y", "@playwright/mcp"],
      "enabled": false
    },
    "context7": {
      "type": "remote",
      "url": "https://mcp.context7.com/mcp"
    }
  },
  "tools": { "playwright_*": false },
  "agent": {
    "e2e-tester": {
      "tools": { "playwright_*": true }
    }
  },
  "instructions": ["AGENTS.md"]
}
```

---

### AGENTS.md Templates

See [`agents/`](agents/) directory for full templates. Quick reference:

**[C# / ASP.NET Core](agents/AGENTS-dotnet.md)**
```markdown
# Project: MyApi (.NET 9 / ASP.NET Core)

## Stack
- ASP.NET Core 9 Minimal APIs + Controllers
- Entity Framework Core 9 (PostgreSQL)
- xUnit + Testcontainers for integration tests
- MediatR for CQRS, FluentValidation

## Code Standards
- Use `async`/`await` throughout — no `.Result` or `.Wait()`
- Prefer `ILogger<T>` over `Console.Write`
- All public APIs must have XML doc comments
- Use `record` types for DTOs and value objects
- Follow Clean Architecture: Domain → Application → Infrastructure → API

## Naming Conventions
- Interfaces: `IServiceName`
- Handlers: `CommandNameHandler`, `QueryNameHandler`
- Tests: `MethodName_Scenario_ExpectedResult`
```

**[Go Microservice](agents/AGENTS-go.md)**
```markdown
# Project: MyService (Go 1.23)

## Stack
- Standard library HTTP + chi router
- pgx/v5 for PostgreSQL
- testify for testing, golangci-lint

## Code Standards
- Handle all errors explicitly — never ignore with `_`
- Use `context.Context` as first parameter in all functions
- Prefer table-driven tests
- Use `slog` for structured logging
- Export only what's necessary — keep packages focused

## Project Layout
- `cmd/` — main packages
- `internal/` — private application code
- `pkg/` — reusable public packages
```

**[Astro + Tailwind](agents/AGENTS-astro.md)**
```markdown
# Project: MySite (Astro 5 + Tailwind CSS v4)

## Stack
- Astro 5 (SSG/SSR hybrid)
- Tailwind CSS v4
- TypeScript strict mode
- Vitest for unit tests

## Code Standards
- Prefer Astro components over framework components for static content
- Use content collections for all data-driven pages
- Tailwind: prefer utility classes over custom CSS
- Mobile-first responsive design
- All images must have alt text; use Astro's `<Image />` component

## File Structure
- `src/components/` — reusable UI components
- `src/layouts/` — page layouts
- `src/content/` — content collections
- `src/pages/` — file-based routing
```

---

## 💡 Tips & Tricks

### Context & Token Optimization

```bash
# Check token usage before starting large tasks
opencode mcp list    # see what's loaded

# Use Caveman skill to cut output tokens ~65%
npx skills add JuliusBrussee/caveman

# Disable heavy MCP servers globally, enable per-task
# In opencode.jsonc: "tools": { "github_*": false }
# Then: "use the github tool to ..." in your prompt

# Use glob to disable all tools of a server:
# "myserver_*": false
```

### Skills Management

```bash
# Discover and install skills from marketplace
npx skills find "code review"
npx skills add owner/repo
npx skills list
npx skills update     # update all installed skills
npx skills remove skill-name

# Project-local skill (committed to repo, shared with team)
mkdir -p .opencode/skills/my-skill
# Create SKILL.md with frontmatter

# Global skill (available in all projects)
mkdir -p ~/.config/opencode/skills/my-skill
```

### AGENTS.md Best Practices

```markdown
# Good AGENTS.md structure:
# 1. Project overview + tech stack (1-3 lines)
# 2. Code standards (language-specific)
# 3. Project layout (key directories)
# 4. Common commands (build, test, run)
# 5. Do NOT commit / sensitive areas

# Keep it focused: ~100-300 lines max
# Use @file references for large docs:
#   "See @docs/api-standards.md for API design rules"
```

### MCP Server Tips

```bash
# Prefer remote MCP servers to avoid subprocess overhead
# Use environment variable interpolation for secrets:
# "Authorization": "Bearer {env:MY_TOKEN}"

# Test a server before adding to config:
opencode mcp debug context7

# Use X-MCP-Toolsets header to limit tool exposure:
"headers": { "X-MCP-Toolsets": "search,read" }

# Rotate stuck OAuth tokens:
opencode mcp logout <server>
opencode mcp auth <server>
```

### Productivity Hacks

```bash
# Use Handoff skill when context gets large:
# "Use the handoff skill to summarize this session"

# Use Grill Me before starting complex features:
# "Use the grill-me skill before writing any code"

# Start with plan mode for complex tasks:
# "Plan the implementation of X, then wait for approval"

# Reference files directly in prompts:
# "Review @src/MyService.cs for performance issues"
# "Follow the patterns in @docs/architecture.md"

# Use worktrees for parallel development:
# "Use the opencode worktrees plugin to create an isolated branch"
```

### Security Checklist

```bash
# Never commit opencode.jsonc with API keys
# Use {env:VAR_NAME} syntax for all secrets
# Add to .gitignore:
echo "opencode.jsonc.local" >> .gitignore

# Use Envsitter Guard plugin to prevent .env leaks
# Use permission control for sensitive tools:
# "permission": { "skill": { "dangerous-*": "ask" } }

# Audit third-party skills before installing:
# Read SKILL.md source — look for network calls
# Check for bundled scripts with external API calls
```

### Creating Your Own Skill

```markdown
# Minimum viable skill:
---
name: my-skill
description: Use when user asks to [SPECIFIC TRIGGER]. Does [SPECIFIC THING].
---

# My Skill

## When to use
[Precise trigger description — this is what the LLM reads to decide if this skill applies]

## Steps
1. [Step one]
2. [Step two]

## Quality checks
- [ ] [Check one]
- [ ] [Check two]
```

```bash
# Validate your skill
npx skills check my-skill

# Test across providers
opencode --model openai/gpt-4o "use the my-skill skill on test.ts"
```

---

## 🎨 Themes

| Theme | Description |
|-------|-------------|
| **[Ayu Dark](https://github.com/awesome-opencode/awesome-opencode)** | Port of the popular Ayu Dark color scheme |
| **[Charcoal](https://github.com/awesome-opencode/awesome-opencode)** | Deep-black grayscale theme |
| **[Lavi](https://github.com/awesome-opencode/awesome-opencode)** | Soft and sweet pastel colorscheme |
| **[Moonlight](https://github.com/awesome-opencode/awesome-opencode)** | Moonlight dark theme |
| **[OpenCode Light Themes](https://github.com/awesome-opencode/awesome-opencode)** | Collection of 21 light color themes |
| **[VS Code Themes](https://github.com/awesome-opencode/awesome-opencode)** | Ports of all built-in VS Code themes |
| **[Poimandres](https://github.com/awesome-opencode/awesome-opencode)** | Poimandres dark theme |

Apply a theme in `tui.json` (same directory as `opencode.jsonc`):
```json
{ "theme": "ayu-dark" }
```

---

## 📚 Resources & Learning

### Official

| Resource | Description |
|----------|-------------|
| **[OpenCode Docs](https://opencode.ai/docs)** | Official documentation |
| **[Skills Docs](https://opencode.ai/docs/skills/)** | Agent Skills guide |
| **[MCP Docs](https://opencode.ai/docs/mcp-servers/)** | MCP server guide |
| **[Config Reference](https://opencode.ai/docs/config/)** | Full config schema |
| **[opencode.school](https://opencode.school)** | Community learning hub |
| **[Agent Skills Standard](https://agentskills.io)** | Open standard specification |

### Starter Configs & Examples

| Resource | Description |
|----------|-------------|
| **[kickstart.opencode](https://github.com/awesome-opencode/awesome-opencode)** | Heavily commented OpenCode starter config |
| **[Opencode Config Starter](https://github.com/awesome-opencode/awesome-opencode)** | Flexible config starting point |
| **[wesammustafa/OpenCode-Everything](https://github.com/wesammustafa/OpenCode-Everything-You-Need-to-Know)** | Community guide covering MCP, agents, tips |
| **[agentsmd.net](https://agentsmd.net/agents-md-examples/)** | AGENTS.md examples for many languages |

### Community

| Resource | Description |
|----------|-------------|
| **[OpenCode Discord](https://discord.gg/opencode)** | Main community server |
| **[r/opencodeCLI](https://reddit.com/r/opencodeCLI)** | Reddit community |
| **[OpenCode Topics](https://github.com/topics/opencode-skills)** | GitHub skill repositories |
| **[skills.sh](https://skills.sh)** | Skill rankings and popularity |
| **[skillsmp](https://skillsmp.io)** | Skills marketplace |

### Related Awesome Lists

| List | Description |
|------|-------------|
| **[awesome-opencode](https://github.com/awesome-opencode/awesome-opencode)** | The original community list |
| **[awesome-copilot](https://github.com/github/awesome-copilot)** | GitHub Copilot skills (cross-compatible) |
| **[awesome-llm-skills](https://github.com/Prat011/awesome-llm-skills)** | Cross-platform LLM skills |
| **[awesome-agent-skills](https://github.com/libukai/awesome-agent-skills)** | Agent skills (Chinese community) |
| **[awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)** | 1000+ Claude skills (cross-compatible) |
| **[awesome-mcp-servers](https://github.com/appcypher/awesome-mcp-servers)** | Comprehensive MCP server list |

### Stack-Specific Resources

| Resource | Description |
|----------|-------------|
| **[.NET MCP Guide](https://learn.microsoft.com/dotnet/ai/quickstarts/build-mcp-server)** | Build MCP servers in C# |
| **[gopls MCP](https://go.dev/gopls/features/mcp)** | Go language server as MCP |
| **[go-sdk/mcp](https://pkg.go.dev/golang.org/x/tools/internal/mcp)** | Official Go MCP SDK |
| **[mark3labs/mcp-go](https://github.com/mark3labs/mcp-go)** | Popular third-party Go MCP library |
| **[Astro Docs](https://docs.astro.build)** | Official Astro documentation |
| **[Tailwind v4 Docs](https://tailwindcss.com/docs)** | Tailwind CSS v4 docs |

---

## 🤝 Contributing

Contributions are **welcome and encouraged**! Here's how:

1. **Fork** this repository
2. **Add your resource** following the existing format
3. Ensure it's **actually useful** and **related to OpenCode**
4. Keep descriptions **concise** (one line per item)
5. Submit a **Pull Request**

### Contribution Guidelines

- ✅ Add real, tested resources — no vaporware
- ✅ One resource per PR for focused review
- ✅ Check for duplicates before adding
- ✅ Skills must follow the `SKILL.md` format spec
- ✅ MCP servers must be configurable in `opencode.jsonc`
- ✅ Include install instructions where possible
- ❌ No self-promotion without genuine value
- ❌ No broken links

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

<div align="center">

**⭐ Star this repo to help others find it! ⭐**

Made with ❤️ by the OpenCode community

[Back to top ↑](#-awesome-opencode)

</div>
