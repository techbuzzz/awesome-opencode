# Contributing to Awesome OpenCode

Thank you for helping make this list better! Please read this guide before submitting.

## What belongs here

- **Skills** with a valid `SKILL.md` following the [Agent Skills spec](https://agentskills.io)
- **Plugins** that hook into OpenCode runtime events (JS/TS modules)
- **MCP Servers** configurable via `opencode.jsonc`
- **Agents** defined in `.opencode/agents/`
- **Config examples** that are real, tested, and useful
- **Tools & projects** that extend or complement OpenCode

## What does NOT belong

- Abandoned or unmaintained projects (no activity in 12+ months)
- Duplicate entries
- Self-promotion without genuine community value
- Resources unrelated to OpenCode

## Adding a Resource

1. Fork this repository
2. Add your entry to the appropriate section in `README.md`
3. Follow the existing table format:
   ```markdown
   | **[Name](url)** | One-line description | `install command` |
   ```
4. If adding a skill in the `skills/` directory, follow the SKILL.md format (see below)
5. Submit a Pull Request with a clear title: `Add: [Resource Name]`

## SKILL.md Format

Every skill must have a `SKILL.md` with valid YAML frontmatter:

```markdown
---
name: skill-name          # lowercase, hyphens only, 1-64 chars
description: >            # 1-1024 chars, specific trigger description
  Use when the user asks to [SPECIFIC THING].
  Handles [SPECIFIC SCENARIO].
license: MIT              # optional
compatibility: opencode   # optional
---

# Skill Name

## When to use
[Precise description of when this skill should activate]

## Steps
1. [Step one]
2. [Step two]

## Quality checks
- [ ] [Check one]
```

**Skill name rules:**
- 1-64 characters
- Lowercase alphanumeric with single hyphens
- Cannot start or end with `-`
- Must match directory name

## PR Review Criteria

- [ ] Resource is functional and publicly accessible
- [ ] Description is accurate and concise (one line)
- [ ] No duplicates in the list
- [ ] Format matches existing entries
- [ ] Install command is tested (if applicable)
- [ ] Skills follow the SKILL.md format spec

## Reporting Issues

- Use GitHub Issues for broken links, outdated entries, or missing resources
- Tag issues with `broken-link`, `outdated`, or `request` labels

---

By contributing, you agree that your submissions are under the MIT License.
