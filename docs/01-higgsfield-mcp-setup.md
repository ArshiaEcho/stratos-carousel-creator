# 01 — Connect the Higgsfield MCP

The skill renders through Higgsfield. This is how you connect and authenticate it in Claude Code. Verified current as of June 2026.

## What you need

- A **Higgsfield account** ([higgsfield.ai](https://higgsfield.ai)). The free tier (150 credits/month) is enough to run the full carousel flow.
- **Claude Code** installed ([claude.com/claude-code](https://claude.com/claude-code)).

There are **no API keys**. Higgsfield authenticates with a browser sign-in (OAuth).

## Connect (Claude Code, recommended)

```bash
claude mcp add --transport http --scope user higgsfield https://mcp.higgsfield.ai/mcp
```

`--scope user` makes Higgsfield available in every project. Use `--scope project` to write a shared `.mcp.json` your teammates inherit, or `--scope local` to limit it to the current folder.

## Connect (team / Claude Desktop, via `.mcp.json`)

Put this at your project root and commit it. Anyone who opens the repo in Claude Code gets Higgsfield after a one-time approval prompt. The same JSON works in Claude Desktop's config.

```json
{
  "mcpServers": {
    "higgsfield": {
      "type": "http",
      "url": "https://mcp.higgsfield.ai/mcp"
    }
  }
}
```

## Connect (Claude.ai on the web)

1. Settings → Connectors.
2. Add a custom connector named **Higgsfield**, paste `https://mcp.higgsfield.ai/mcp`.
3. Add → Connect → sign in.

## Authenticate

1. In Claude Code, run `/mcp`.
2. Select `higgsfield` (it will show "Needs authentication").
3. Choose **Authenticate**. Your browser opens.
4. Sign in with the account that has your credits, approve, and the token returns to Claude Code automatically.
5. The status flips to **✓ Connected**.

## Verify

```bash
claude mcp list
# higgsfield: https://mcp.higgsfield.ai/mcp (HTTP) - ✓ Connected
```

## Troubleshooting

- **"Needs authentication"** — the sign-in has not happened or the token expired. Run `/mcp`, pick Higgsfield, choose Authenticate (or Clear authentication, then re-auth).
- **Remove it** — `claude mcp remove higgsfield`.
- **Context cost** — every MCP loads its tool descriptions into context. Higgsfield is light. If you stack many MCPs, remove the ones you are not using.
- **MCP vs CLI** — for very heavy automation, Higgsfield also ships a CLI that is leaner on tokens. The MCP is all you need for this skill.
