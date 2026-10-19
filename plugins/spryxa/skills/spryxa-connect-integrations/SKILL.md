---
name: spryxa-connect-integrations
description: Connect or inspect Spryxa integrations such as social accounts, GA4, Search Console, CRM, ads, email, and external action providers through MCP.
---

# Spryxa Connect Integrations

Use this skill when the user wants to connect, verify, list, fix, or disconnect Spryxa integrations.

Start with `spryxa_get_session`. If no project is active, use `spryxa_list_projects` and `spryxa_update_session_project`.

Useful tools:
`spryxa_list_platform_connections`, `spryxa_connect_platform`, `spryxa_get_platform_connection_status`, `spryxa_disconnect_platform`, `spryxa_list_platform_actions`, `spryxa_run_platform_action`.

Never ask for passwords, cookies, API keys, or OAuth tokens. For OAuth, return or explain the authorization URL and tell the user to approve it in their browser.

Disconnecting or executing external actions can be high-impact. If the tool returns `confirmation_required`, re-call with `confirm:true` only after explicit approval.

When a workflow is blocked by missing GA4, Search Console, CRM, ads, email, or social access, explain exactly which connection is missing and which tool or Spryxa UI step resolves it.
