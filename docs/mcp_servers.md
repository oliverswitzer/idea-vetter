# MCP Server Reference

All MCP servers are configured in `.mcp.json` at the project root. Claude Code loads this automatically.

## Server Overview

| Server | Purpose | Transport | Requires |
|---|---|---|---|
| @playwright/mcp | Browser automation, screenshots | npx | Chromium (`npx playwright install`) |
| google-trends-mcp | Google Trends data | uvx | None |
| mcp-pandoc | Document conversion | uvx | Pandoc binary |

---

## @playwright/mcp

**Why**: Automates browser interactions for scraping dynamic pages, capturing screenshots of competitor products, and navigating sites that require JavaScript.

**Install**:
```bash
npx playwright install chromium
```

**Environment variables**: None required.

**Example usage in this repo**:
- Screenshot competitor landing pages
- Navigate and scrape JavaScript-heavy product pages
- Capture pricing tables that load dynamically

**Links**: [npm](https://www.npmjs.com/package/@playwright/mcp)

---

## google-trends-mcp

**Why**: Provides Google Trends data including interest over time, interest by region, related topics, and related queries. Essential for assessing demand trajectory.

**Install**: No pre-installation needed (runs via `uvx`).

**Environment variables**: None required.

**Example usage in this repo**:
- Check if interest in a problem/solution is growing or declining
- Compare search interest between competing terms
- Identify seasonal patterns in demand
- Find related queries that reveal user intent

**Links**: [PyPI](https://pypi.org/project/google-trends-mcp/)

---

## mcp-pandoc

**Why**: Converts reports between formats. Primary use: Markdown to PDF, DOCX, or HTML for sharing outside the repo.

**Install**:
```bash
brew install pandoc        # macOS
# For PDF output:
brew install --cask basictex
```

**Environment variables**: None required.

**Example usage in this repo**:
- Convert `reports/*.md` to PDF for stakeholder sharing
- Generate DOCX for collaborative editing
- Create HTML reports for web hosting

**Links**: [PyPI](https://pypi.org/project/mcp-pandoc/)

---

## Swapping or Extending Servers

To replace a server, edit `.mcp.json`:

1. Remove or comment out the existing server entry
2. Add the new server with its command, args, and env
3. Update this doc with the new server's details

To add a new server:

1. Add an entry to `.mcp.json`
2. Update agent frontmatter if the agent should use the new server's tools
3. Document the server in this file

Common alternatives:
- **Puppeteer MCP** instead of Playwright
- **SerpAPI MCP** for structured Google results
- **data.ai** or **Sensor Tower** APIs for deeper app store intelligence (if you have access)
