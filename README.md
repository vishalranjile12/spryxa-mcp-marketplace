# Spryxa MCP Plugin Marketplace

This repository publishes the Spryxa plugin marketplace. It lets workspace admins import Spryxa into Codex or ChatGPT from GitHub, and lets Claude Code users install the same Spryxa plugin from a marketplace.

## What This Repo Contains

```text
.agents/
  plugins/
    marketplace.json              # OpenAI/Codex marketplace catalog
.claude-plugin/
  marketplace.json                # Claude Code marketplace catalog
plugins/
  spryxa/
    .codex-plugin/
      plugin.json                 # OpenAI/Codex plugin manifest
    .claude-plugin/
      plugin.json                 # Claude Code plugin manifest
    .mcp.json                     # Spryxa remote MCP server config
    skills/
      spryxa-*/SKILL.md           # Spryxa workflow skills
```

## Current Spryxa MCP Endpoint

```text
https://app.spryxa.ai/mcp
```

The MCP server is hosted by Spryxa. This repository only packages the MCP config, skills, and marketplace metadata.

## For OpenAI Workspace Admins

Use these steps to import Spryxa for Codex or ChatGPT workspace users:

1. Open **Workspace settings**.
2. Go to **Plugins**.
3. Select **Add**.
4. Choose **Import marketplace**.
5. In **Source**, paste this GitHub repository URL:

   ```text
   https://github.com/vishalranjile12/spryxa-mcp-marketplace
   ```

6. Leave **Path** empty because `.agents/plugins/marketplace.json` is at the repository root.
7. Leave **Branch / tag / commit** empty to use the default branch, or enter `main`.
8. Select **Import marketplace** and authorize GitHub if prompted.
9. Open the imported **Spryxa** plugin.
10. Set installation policy:
    - **Available** if users should install it themselves.
    - **Installed** if it should be automatically installed for eligible users.
11. Confirm required app/MCP access and action permissions.

Importing the marketplace does not authenticate individual users. Each user still connects their own Spryxa account.

This marketplace uses **authentication on use**. That is intentional for workspace installs: users may receive the plugin from an admin without personally clicking an install button, so Codex should ask them to authenticate when they first invoke Spryxa.

## For Codex Users

After an admin imports the marketplace and makes Spryxa available:

1. Open Codex.
2. Open **Sources**.
3. Select **Use plugins**.
4. Search for **Spryxa**.
5. Select or install the plugin.
6. Click **Authenticate** when prompted.
7. Approve the Spryxa OAuth flow in your browser.

Then use Spryxa naturally, for example:

```text
@spryxa improve website conversion for my selected project
@spryxa create LinkedIn content for this campaign
@spryxa check what is blocked for my project
```

## Reconnecting After Logout

Spryxa includes `spryxa_logout`, but it does not include `spryxa_login`. Login is started by the Codex client because logged-out MCP requests are rejected before normal tools can run.

After logging out, reconnect from Codex by using Spryxa again:

```text
@spryxa check my Spryxa login
```

Codex should receive Spryxa's OAuth challenge and show the authentication prompt. If the prompt does not appear, restart Codex and try again.

For Codex CLI users:

```powershell
codex mcp list
codex mcp login spryxa
```

Use the exact server name shown by `codex mcp list` if it differs from `spryxa`.

## For ChatGPT Users

Availability depends on your ChatGPT plan, workspace settings, and whether your admin enabled imported plugins for your role.

After the workspace admin imports and enables Spryxa:

1. Open ChatGPT in the enabled workspace.
2. Open the plugin/app picker where available.
3. Search for **Spryxa**.
4. Connect or authenticate your Spryxa account.
5. Use Spryxa through the available plugin/app controls or `@spryxa` where supported.

If Spryxa does not appear, ask your workspace admin to check the plugin installation policy and role access.

## For Claude Code Users

Claude Code uses the `.claude-plugin/marketplace.json` file in this repository.

From Claude Code, add the marketplace:

```text
/plugin marketplace add vishalranjile12/spryxa-mcp-marketplace
```

Then install the plugin:

```text
/plugin install spryxa@spryxa
```

Restart or reload Claude Code if needed, then verify MCP:

```text
/mcp
```

Use the Spryxa skills with plugin namespacing:

```text
/spryxa:spryxa-improve-website-conversion
/spryxa:spryxa-create-content
/spryxa:spryxa-check-project-status
```

If Claude Code reports authentication problems, reconnect the MCP server or complete the Spryxa OAuth flow in the browser when prompted.

## Updating The Plugin

1. Edit files under `plugins/spryxa/`.
2. Commit and push to the default branch.
3. OpenAI workspace marketplaces sync daily. Admins can also use **Sync now** from workspace plugin marketplace settings.
4. Claude Code users can run:

   ```text
   /plugin marketplace update spryxa
   ```

## Before Publishing

Replace placeholders before pushing publicly:

- `https://github.com/vishalranjile12/spryxa-mcp-marketplace`
- `vishalranjile12/spryxa-mcp-marketplace`
- privacy policy URL if different from `https://spryxa.ai/privacy`
- terms URL if different from `https://spryxa.ai/terms`
- support email if different from `support@spryxa.ai`

Also test the OAuth flow from a clean Codex or Claude Code install before sharing the repository with customers.
