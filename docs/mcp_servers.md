# MCP Server Reference

All MCP servers are configured in `.mcp.json` at the project root. Claude Code loads this automatically.

## Server Overview

| Server | Purpose | Transport | Requires |
|---|---|---|---|
| mcp-searxng-enhanced | Web search and page scraping | uvx | SearXNG instance (Docker) |
| playwright-mcp-server | Browser automation, screenshots | npx | Chromium (`npx playwright install`) |
| google-trends-mcp | Google Trends data | uvx | None |
| google-news-trends-mcp | News-based trend signals | uvx | None |
| mcp-appstore | App store search and reviews | npx | None |
| mcp-pandoc | Document conversion | uvx | Pandoc binary |

---

## mcp-searxng-enhanced

**Why**: Primary tool for web search across categories (general, news, science, IT, forums). Also supports page content scraping.

**Install**:
```bash
# Start a local SearXNG instance
docker run -d -p 8080:8080 --name searxng searxng/searxng
```

**Environment variables**:
- `SEARXNG_BASE_URL` - URL of your SearXNG instance (default: `http://localhost:8080`)

**Example usage in this repo**:
- Search for competitor products by keyword
- Search forums and Reddit for user complaints
- Scrape pricing pages for competitor analysis

**Links**: [npm](https://www.npmjs.com/package/mcp-searxng-enhanced) | [GitHub](https://github.com/search?q=mcp-searxng-enhanced)

---

## playwright-mcp-server

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

**Links**: [npm](https://www.npmjs.com/package/@anthropic/playwright-mcp-server)

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

## google-news-trends-mcp

**Why**: Surfaces trending news topics and recent coverage. Useful for detecting market shifts, funding rounds, and emerging categories.

**Install**: No pre-installation needed (runs via `uvx`).

**Environment variables**: None required.

**Example usage in this repo**:
- Find recent funding rounds in a space
- Detect emerging trends before they show in search volume
- Identify regulatory or market changes affecting an idea

**Links**: [PyPI](https://pypi.org/project/google-news-trends-mcp/)

---

## mcp-appstore

**Why**: Searches and retrieves app listings, ratings, reviews, and metadata from iOS App Store and Google Play. Critical for mobile-related ideas.

**Install**: No pre-installation needed (runs via `npx`).

**Environment variables**: None required.

**Example usage in this repo**:
- Search for competing apps by keyword
- Retrieve ratings, review counts, and pricing
- Read user reviews to mine complaints and feature requests
- Track when competitors last updated their apps

**Links**: [npm](https://www.npmjs.com/package/mcp-appstore)

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
- **Tavily** or **Brave Search** instead of SearXNG (if you want API-based search without self-hosting)
- **Puppeteer MCP** instead of Playwright
- **SerpAPI MCP** for structured Google results
- **data.ai** or **Sensor Tower** APIs for deeper app store intelligence (if you have access)
