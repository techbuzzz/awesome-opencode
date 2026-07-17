# Skills Quick Reference for OpenCode

## What Are Skills?

Skills are directories with a `SKILL.md` file that teach OpenCode reusable behaviors.
- **Progressive loading:** only name+description loaded at startup; full body loaded on-demand
- **Cross-compatible:** skills from Claude Code, Codex, Cursor work in OpenCode unchanged
- **Permissioned:** controlled via `opencode.jsonc`

## Install Skills

```bash
# Using npx skills CLI (recommended)
npx skills find "code review"       # Search
npx skills add owner/repo           # Install
npx skills add owner/repo --skill skill-name  # Install specific skill
npx skills list                     # List installed
npx skills update                   # Update all
npx skills remove skill-name        # Uninstall
npx skills check                    # Check for updates
```

## Discovery Paths

| Scope | Path |
|-------|------|
| Project (OpenCode) | `.opencode/skills/<name>/SKILL.md` |
| Project (Claude) | `.claude/skills/<name>/SKILL.md` |
| Project (Agent) | `.agents/skills/<name>/SKILL.md` |
| Global (OpenCode) | `~/.config/opencode/skills/<name>/SKILL.md` |
| Global (Claude) | `~/.claude/skills/<name>/SKILL.md` |
| Global (Agent) | `~/.agents/skills/<name>/SKILL.md` |

## Create a Skill

```
.opencode/skills/my-skill/
└── SKILL.md          # Required
    references/       # Optional: reference docs
    scripts/          # Optional: helper scripts
    assets/           # Optional: templates, data
```

### Minimal SKILL.md Template

```markdown
---
name: my-skill
description: >
  Use when the user asks to [SPECIFIC TRIGGER].
  Handles [SPECIFIC SCENARIO]. Works with [LANGUAGE/FRAMEWORK].
license: MIT
compatibility: opencode
---

# My Skill

## When to Use
[Clear trigger description — this is key for correct activation]

## Steps
1. [Step one]
2. [Step two]
3. [Step three]

## Quality Checks
- [ ] [Check one]
- [ ] [Check two]

## Examples
[Real-world usage examples]
```

### Name Rules
- 1-64 characters
- Lowercase alphanumeric + single hyphens
- No leading/trailing hyphens
- Must match directory name
- Regex: `^[a-z0-9]+(-[a-z0-9]+)*$`

## Permission Control

```jsonc
// opencode.jsonc
{
  "permission": {
    "skill": {
      "*": "allow",           // allow all
      "internal-*": "deny",   // block internal skills
      "experimental-*": "ask" // prompt before loading
    }
  },
  "agent": {
    "my-agent": {
      "permission": {
        "skill": {
          "dotnet-expert": "allow",
          "*": "deny"           // only allow specified skills
        }
      }
    }
  }
}
```

## Top Community Skills

### Workflow
| Skill | Install |
|-------|---------|
| Firecrawl (web access) | `npx -y firecrawl-cli@latest init` |
| Handoff (session compress) | `npx skills add mattpocock/skills` |
| Grill Me (plan review) | `npx skills add mattpocock/skills --skill grill-me` |
| Caveman (token reduction) | `curl -fsSL .../install.sh \| bash` |
| stop-slop (anti-AI jargon) | `git clone ... ~/.agents/skills/stop-slop` |
| Obra Superpowers (full framework) | See [docs](https://github.com/obra/superpowers) |
| Understand-Anything (codebase map) | `curl -fsSL .../install.sh \| bash -s opencode` |
| Composio (1000+ integrations) | `npx skills add composiohq/skills` |

### Development (included in this repo)
| Skill | Path | Purpose |
|-------|------|---------|
| dotnet-expert | `skills/dotnet-expert/` | C#/.NET best practices |
| go-expert | `skills/go-expert/` | Go idioms and patterns |
| typescript-astro | `skills/typescript-astro/` | Astro + TypeScript |
| tailwind-ui | `skills/tailwind-ui/` | Tailwind CSS components |
| code-review | `skills/code-review/` | Structured code review |
| tdd | `skills/tdd/` | Test-Driven Development |
| git-flow | `skills/git-flow/` | Git workflow + commits |
| security-audit | `skills/security-audit/` | OWASP security checks |

## Signs of a Good Skill

✅ Specific trigger description (not vague like "helps with web tasks")  
✅ Deterministic work done in bundled scripts  
✅ Lean SKILL.md body, detailed reference files  
✅ One skill, one job  
✅ Clear examples in the body  

## Signs of a Bad Skill

❌ Bloated SKILL.md that loads on every adjacent task  
❌ Undocumented network calls in bundled scripts  
❌ No examples  
❌ Tries to cover 5 different workflows  
❌ Name doesn't match directory  
