# MCP Server Recommendations

This document lists MCP (Model Context Protocol) servers that enhance the hardware planning workflow.

## Essential MCPs

### Context7

**Purpose:** Access up-to-date documentation and specifications for hardware components.

**Use cases:**
- Verify compatibility between components
- Get current specifications for CPUs, GPUs, motherboards
- Check supported memory speeds and capacities
- Research benchmark data

**Installation:**
```bash
mcpm install context7
# or add to your Claude Code MCP configuration
```

---

### TIME

**Purpose:** Get accurate current date and time.

**Use cases:**
- Date-stamp hardware profiles accurately
- Set estimate validity periods
- Note when pricing data was retrieved

**Why it's essential:** The AI's training data has a cutoff date. Without TIME MCP, profiles and estimates may have incorrect dates.

**Installation:**
```bash
mcpm install time
```

---

### Browser / WebFetch

**Purpose:** Retrieve current information from websites.

**Use cases:**
- Fetch current pricing from vendor websites
- Check product availability
- Retrieve benchmark scores
- Get current specifications

**Note:** Web fetch capabilities allow the agent to provide real-time pricing rather than estimated or outdated prices.

**Installation:**
```bash
mcpm install browser-mcp
# or use built-in WebFetch tool if available
```

---

## Optional MCPs

### Notion

**Purpose:** Export documents to Notion.

**Use cases:**
- Save hardware profiles to your Notion workspace
- Archive estimates and recommendations
- Maintain a personal hardware knowledge base

**Installation:**
```bash
mcpm install notion
```

---

### Resend

**Purpose:** Send emails directly from the workspace.

**Use cases:**
- Email estimates to yourself for reference
- Send VAT-compliant quotes to your accountant
- Share recommendations with collaborators

**Installation:**
```bash
mcpm install resend
# Requires API key configuration
```

---

## Configuration

### Using mcpm

If you use [mcpm](https://github.com/pathintegral-institute/mcpm.sh) (Model Context Protocol Manager):

```bash
# List available MCPs
mcpm list

# Install an MCP
mcpm install <mcp-name>

# Configure for Claude Code
mcpm configure claude-code
```

### Manual Configuration

Add MCPs to your Claude Code configuration:

**User-level:** `~/.config/claude-code/mcp.json`

**Project-level:** `.claude/mcp.json`

Example configuration:
```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    },
    "time": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-time"]
    }
  }
}
```

---

## MCP Usage in This Workspace

The agent instructions in this repository reference these MCPs:

| MCP | Where Used |
|-----|------------|
| Context7 | `/profile`, `/analyze`, `/recommend`, `/compare` - for specs and compatibility |
| TIME | `/profile`, `/estimate` - for accurate date stamps |
| Browser | `/recommend`, `/estimate` - for current pricing |
| Notion | On user request - for exporting documents |
| Resend | `/estimate` - for emailing quotes |

If an MCP is not available, the agent will:
- Ask the user to verify information manually
- Note that data should be confirmed
- Proceed with available tools

---

## Troubleshooting

### MCP not recognized

1. Verify installation: `mcpm list installed`
2. Restart Claude Code
3. Check configuration file syntax

### Context7 returns no results

- Try different search terms
- Some hardware may not be indexed yet
- Fall back to web search

### TIME shows wrong timezone

- Configure timezone in MCP settings
- Ask user to confirm time if critical

---

## Adding New MCPs

If you discover useful MCPs for hardware planning, consider:
1. Testing them with this workflow
2. Documenting use cases
3. Submitting a PR to update this file
