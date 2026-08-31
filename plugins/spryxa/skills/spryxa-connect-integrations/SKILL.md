---
name: spryxa-connect-integrations
description: Connect or inspect Spryxa integrations such as social accounts, GA4, Search Console, CRM, ads, email, and external action providers through MCP.
---

# Spryxa Connect Integrations

Use this skill when the user wants to connect, verify, list, fix, or disconnect Spryxa integrations.

Start with `spryxa_whoami`. If no project is active, use `spryxa_list_projects` and `spryxa_set_active_project`.

Useful tools:
`spryxa_list_integrations`, `spryxa_create_social_connection_link`, `spryxa_connect_external_platform`, `spryxa_get_social_connection_status`, `spryxa_disconnect_social_connection`, `spryxa_list_external_actions`, `spryxa_execute_external_action`.

Never ask for passwords, cookies, API keys, or OAuth tokens. For OAuth, return or explain the authorization URL and tell the user to approve it in their browser.

Disconnecting or executing external actions can be high-impact. If the tool returns `confirmation_required`, re-call with `confirm:true` only after explicit approval.

When a workflow is blocked by missing GA4, Search Console, CRM, ads, email, or social access, explain exactly which connection is missing and which tool or Spryxa UI step resolves it.
