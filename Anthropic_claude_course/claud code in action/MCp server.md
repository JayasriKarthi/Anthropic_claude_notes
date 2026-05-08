- Install Playwright MCP server:

```
claude mcp add playwright npx @playwright/mcp@latest
```

- Purpose:
    - Adds Playwright MCP server to Claude Code
    - Enables browser automation and UI interaction

---

# Managing Permissions

Edit:

```
.claude/settings.local.json
```

Add:

```
{  "permissions": {    "allow": ["mcp__playwright"],    "deny": []  }}
```

- Use `mcp__playwright` (double underscores)
- Prevents repeated permission prompts

---

# What Playwright MCP Can Do

Claude can:

- Open browser
- Navigate apps/websites
- Interact with UI
- Analyze visual output
- Improve prompts/components based on UI results

---

# Example Workflow

Claude can:

1. Open `localhost:3000`
2. Generate component
3. Review styling
4. Update generation prompt
5. Retest improved component

---

# Main Benefit

- Claude sees actual visual output, not just code
- Leads to better UI and styling decision

---

# Other MCP Server Uses

MCP servers can also support:

- Database operations
- API testing
- File system access
- Cloud integrations
- Development automation
