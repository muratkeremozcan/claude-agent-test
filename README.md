# Claude Desktop Model Context Protocol (MCP) Setup Guide

## Prerequisites
- Download Claude Desktop from https://claude.ai/download
- Install and open the application

## Step 1: Locate Claude Configuration Folder
Open Terminal and navigate to the Claude configuration directory:

```bash
open ~/Library/Application\ Support/Claude
touch ~/Library/Application\ Support/Claude/claude_desktop_config.json
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

## Step 2: Brave Search MCP Configuration

### Get Brave API Key
1. Sign up for a Brave Search API account
2. Choose a plan (Free tier: 2,000 queries/month)
3. Generate API key from developer dashboard

### Update Configuration
```json
{
  "mcpServers": {
    "brave-search": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-brave-search"
      ],
      "env": {
        "BRAVE_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

## Step 3: GitHub MCP Configuration

### Create GitHub Personal Access Token
1. Go to GitHub Settings > Developer settings > Personal access tokens
2. Select repository access
3. Create token with `repo` or `public_repo` scope

### Update Configuration
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR_GITHUB_TOKEN"
      }
    }
  }
}
```

## Final Steps
- Restart Claude Desktop
- Verify MCP tools are available

## Note
Replace `YOUR_API_KEY_HERE` and `YOUR_GITHUB_TOKEN` with your actual credentials.