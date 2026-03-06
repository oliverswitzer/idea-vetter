# Setup Guide

## Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- Node.js 18+ (for npx-based MCP servers)
- Python 3.10+ with `uv` or `uvx` (for Python-based MCP servers)

### Optional Dependencies

| Dependency | Required For | Install |
|---|---|---|
| Pandoc | Report export (PDF/DOCX) | `brew install pandoc` |
| TeX (BasicTeX) | PDF export via Pandoc | `brew install --cask basictex` |
| Playwright browsers | Browser automation | `npx playwright install chromium` |

## Installation

### 1. Clone the repo

```bash
git clone <repo-url> mvp-vetter
cd mvp-vetter
```

### 2. Install MCP server dependencies

Most MCP servers are installed on-demand via `npx` or `uvx`. No pre-installation needed for:
- `@playwright/mcp` (npx)
- `google-trends-mcp` (uvx)
- `mcp-pandoc` (uvx)

> **Note:** `.env` and `.env.example` exist in the repo but are **not currently needed**. They are reserved for future use (e.g., API keys).

For **Playwright** browser automation:

```bash
npx playwright install chromium
```

### 3. Verify the setup

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

### Pandoc export fails
- Verify pandoc is installed: `pandoc --version`
- For PDF: ensure TeX is installed: `xelatex --version`
