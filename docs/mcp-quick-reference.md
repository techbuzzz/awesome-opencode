# MCP Quick Reference for OpenCode

## Essential MCP Server Configs

Copy-paste these directly into your `opencode.jsonc`:

### Context7 (Documentation)
```jsonc
"context7": {
  "type": "remote",
  "url": "https://mcp.context7.com/mcp",
  "enabled": true
}
```
**Usage:** Add `use context7` to any prompt to get latest library docs.

---

### GitHub MCP
```jsonc
"github": {
  "type": "remote",
  "url": "https://api.githubcopilot.com/mcp/",
  "oauth": {},
  "enabled": false
}
```
**Usage:** `opencode mcp auth github` then add `use the github tool`.
**⚠️ Warning:** Adds 10,000+ tokens. Keep disabled globally.

---

### Grep by Vercel (Code Search)
```jsonc
"gh_grep": {
  "type": "remote",
  "url": "https://mcp.grep.app",
  "enabled": true
}
```
**Usage:** `use the gh_grep tool to find examples of [pattern]`

---

### PostgreSQL
```jsonc
"postgres": {
  "type": "local",
  "command": ["npx", "-y", "@modelcontextprotocol/server-postgres", "{env:DATABASE_URL}"],
  "enabled": true
}
```

---

### SQLite
```jsonc
"sqlite": {
  "type": "local",
  "command": ["npx", "-y", "@modelcontextprotocol/server-sqlite", "--db-path", "./data.db"],
  "enabled": true
}
```

---

### Playwright (Browser Automation)
```jsonc
"playwright": {
  "type": "local",
  "command": ["npx", "-y", "@playwright/mcp"],
  "enabled": false
}
```
**Enable per-agent:**
```jsonc
"agent": {
  "e2e-tester": {
    "tools": { "playwright_*": true }
  }
}
```

---

### Sentry
```jsonc
"sentry": {
  "type": "remote",
  "url": "https://mcp.sentry.dev/mcp",
  "oauth": {}
}
```
**Auth:** `opencode mcp auth sentry`

---

### gopls (Go Language Server)
```jsonc
"gopls": {
  "type": "local",
  "command": ["gopls", "mcp"],
  "enabled": true
}
```
**Prerequisites:** `go install golang.org/x/tools/gopls@latest`

---

### Docker
```jsonc
"docker": {
  "type": "local",
  "command": ["npx", "-y", "@docker/mcp"],
  "enabled": false
}
```

---

### Supabase
```jsonc
"supabase": {
  "type": "local",
  "command": ["npx", "-y", "@supabase/mcp-server-supabase"],
  "environment": {
    "SUPABASE_URL": "{env:SUPABASE_URL}",
    "SUPABASE_SERVICE_ROLE_KEY": "{env:SUPABASE_SERVICE_ROLE_KEY}"
  }
}
```

---

### Linear (Issue Tracking)
```jsonc
"linear": {
  "type": "local",
  "command": ["npx", "-y", "@linear/mcp-server"],
  "environment": {
    "LINEAR_API_KEY": "{env:LINEAR_API_KEY}"
  }
}
```

---

### Composio (1000+ integrations via single endpoint)
```jsonc
"composio": {
  "type": "remote",
  "url": "https://mcp.composio.dev",
  "headers": {
    "X-Composio-Api-Key": "{env:COMPOSIO_API_KEY}"
  }
}
```

---

## MCP CLI Commands Cheat Sheet

```bash
# List all configured servers and their status
opencode mcp list

# Debug connectivity for a specific server
opencode mcp debug <server-name>

# Authenticate via OAuth
opencode mcp auth <server-name>

# View OAuth authentication status for all servers
opencode mcp auth list

# Remove stored OAuth tokens
opencode mcp logout <server-name>
```

## Token Cost Reference

| Server | Approx. tokens added |
|--------|---------------------|
| Context7 | ~500-1,000 |
| Filesystem | ~200 |
| SQLite | ~300 |
| Playwright | ~1,000 |
| GitHub MCP | ~10,000-15,000 ⚠️ |
| Composio | ~500 (meta-tools only) |

## Tips

1. **Disable globally, enable per-agent** for heavy servers
2. **Use glob patterns** to disable all tools of a server: `"github_*": false`
3. **Use `{env:VAR}` syntax** for all secrets — never hardcode
4. **Test connectivity** before adding to config: `opencode mcp debug <name>`
5. **Use gateway MCPs** (Composio) instead of many individual servers
