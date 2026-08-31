---
name: spryxa-create-campaign
description: Create or launch Spryxa campaign drafts, inspect ads performance, audience data, CRM contacts, and email campaign stats through MCP.
---

# Spryxa Create Campaign

Use this skill when the user wants to create a campaign draft, prepare ad/email campaign work, inspect campaign performance, or launch an approved campaign.

Start with `spryxa_whoami`. If no project is active, use `spryxa_list_projects` and `spryxa_set_active_project`.

Useful tools:
`spryxa_create_campaign_draft`, `spryxa_launch_campaign`, `spryxa_get_ads_performance`, `spryxa_get_audience_insights`, `spryxa_get_crm_contacts`, `spryxa_manage_crm_contact`, `spryxa_get_email_campaign_stats`, `spryxa_send_email_campaign`, `spryxa_list_integrations`.

Collect enough brief detail before creating a campaign: objective, audience, offer, destination URL or landing page, channel, budget guardrails, and approval owner.

Drafting and launching are separate. Do not launch spend, send emails, or modify CRM records unless the user explicitly approves and the MCP tool confirmation gate passes.

If an integration is missing, stop and explain the connection needed before continuing.
