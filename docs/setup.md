# Setup Guide

## Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- Node.js 18+ (for npx-based MCP servers)
- Python 3.10+ with `uv` or `uvx` (for Python-based MCP servers)

### Optional Dependencies

| Dependency | Required For | Install |
|---|---|---|
| Docker | SearXNG instance | [docker.com](https://docs.docker.com/get-docker/) |
| Pandoc | Report export (PDF/DOCX) | `brew install pandoc` |
| TeX (BasicTeX) | PDF export via Pandoc | `brew install --cask basictex` |
| Playwright browsers | Browser automation | `npx playwright install chromium` |

## Installation

### 1. Clone the repo

```bash
git clone <repo-url> mvp-vetter
cd mvp-vetter
```

### 2. Set up environment variables

```bash
cp .env.example .env
# Edit .env with your values
```

### 3. Install MCP server dependencies

Most MCP servers are installed on-demand via `npx` or `uvx`. No pre-installation needed for:
- `playwright-mcp-server` (npx)
- `google-trends-mcp` (uvx)
- `google-news-trends-mcp` (uvx)
- `mcp-appstore` (uvx/npx)
- `mcp-pandoc` (uvx)

For **SearXNG**, you need a running instance:

```bash
# Option A: Run locally with Docker
docker run -d -p 8080:8080 --name searxng searxng/searxng

# Option B: Use a public instance (less reliable)
# Set SEARXNG_BASE_URL in .env to a public instance URL
```

For **Playwright** browser automation:

```bash
npx playwright install chromium
```

### 4. Verify the setup

Open Claude Code in the project directory:

```bash
cd mvp-vetter
claude
```

Claude should load the project instructions from `.claude/CLAUDE.md` automatically. You can verify MCP servers are configured by checking that `.mcp.json` is recognized.

## Troubleshooting

### MCP servers not loading
- Ensure `.mcp.json` is in the project root
- Check that `uvx` and `npx` are on your PATH
- Try running the server command manually to see errors

### SearXNG connection refused
- Verify Docker is running: `docker ps`
- Check the container: `docker logs searxng`
- Ensure `SEARXNG_BASE_URL` matches your instance

### Pandoc export fails
- Verify pandoc is installed: `pandoc --version`
- For PDF: ensure TeX is installed: `xelatex --version`
