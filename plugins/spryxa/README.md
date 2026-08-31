# Spryxa Plugin

This plugin bundles the Spryxa MCP server and Spryxa workflow skills for Codex, ChatGPT workspace plugin import, and Claude Code.

## Included MCP Server

```text
https://app.spryxa.ai/api/mcp/mcp
```

The MCP server uses OAuth. Users still authenticate their own Spryxa account after the plugin is installed.

## Included Skills

- `spryxa-check-project-status`
- `spryxa-connect-integrations`
- `spryxa-create-campaign`
- `spryxa-create-content`
- `spryxa-improve-website-conversion`
- `spryxa-kpi-ledger`
- `spryxa-mcp-operator`
- `spryxa-propose-site-change`
- `spryxa-run-mission`
- `spryxa-schedule-content`

## Safety

Spryxa write actions may require confirmation. Users must approve launches, publishing, sends, promotions, and other high-impact changes before the tool is called with `confirm:true`.
