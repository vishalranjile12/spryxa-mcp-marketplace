---
name: spryxa-mcp-operator
description: "Use when operating Spryxa through MCP tools: project setup, integrations, audits, content, campaigns, missions, agent teams, workflow status, site changes, KPI ledger, or the website-conversion Plan workflow."
---

# Spryxa MCP Operator

Use this skill when the user wants Codex or another agent to operate Spryxa through the `spryxa_*` MCP tools.

## First Step

Start each new Spryxa MCP session with `spryxa_whoami`.

If the response says project selection is needed, call `spryxa_list_projects`, ask or infer the intended project, then call `spryxa_set_active_project`. If the user is new, collect the website/domain and the user's role before creating the organization.

Never ask for passwords, cookies, API keys, or OAuth tokens. OAuth approval happens in the user's browser through Spryxa connection tools or the Spryxa UI.

## Safety Rules

Treat Spryxa tool scopes and preconditions as server truth. If a tool reports missing setup, missing data, insufficient scope, insufficient credits, or `confirmation_required`, stop and explain the exact next step.

Do not publish, launch, promote, send, disconnect, enable higher autonomy, or start credit-spending async work without explicit user approval. When a write tool requires `confirm:true`, first explain what will happen, then call it again only after the user agrees.

Approval-gate confirmation for a Plan launch means the user acknowledges who owns approvals. It does not approve future visual, pricing, offer, risky code, publishing, campaign, or site changes.

Poll async workflows at most once per turn unless the user asks for active waiting. Prefer `spryxa_get_workflow_status` when a run id is available and `spryxa_list_workflow_runs` when it is not.

## Tool Groups

Project and account context:
`spryxa_whoami`, `spryxa_create_organization`, `spryxa_list_projects`, `spryxa_get_project`, `spryxa_set_active_project`, `spryxa_get_credit_balance`, `spryxa_logout`.

Project intelligence:
`spryxa_get_insights`, `spryxa_get_reports`, `spryxa_get_audit`, `spryxa_get_project_capabilities`, `spryxa_search`, `spryxa_fetch`.

Integrations:
`spryxa_list_integrations`, `spryxa_create_social_connection_link`, `spryxa_connect_external_platform`, `spryxa_get_social_connection_status`, `spryxa_disconnect_social_connection`, `spryxa_list_external_actions`, `spryxa_execute_external_action`.

Content and publishing:
`spryxa_generate_content`, `spryxa_update_content`, `spryxa_list_content_library`, `spryxa_get_content`, `spryxa_get_content_queue`, `spryxa_schedule_content`, `spryxa_schedule_series`, `spryxa_publish_content`.

Campaigns, CRM, email, and audience:
`spryxa_create_campaign_draft`, `spryxa_launch_campaign`, `spryxa_get_ads_performance`, `spryxa_get_crm_contacts`, `spryxa_manage_crm_contact`, `spryxa_get_email_campaign_stats`, `spryxa_send_email_campaign`, `spryxa_get_audience_insights`, `spryxa_run_pipeline_play`.

Missions, agent teams, and workflow orchestration:
`spryxa_list_agent_teams`, `spryxa_list_missions`, `spryxa_get_mission`, `spryxa_create_mission`, `spryxa_update_mission_brief`, `spryxa_run_strategy_sprint`, `spryxa_approve_mission_plan`, `spryxa_transition_phase`, `spryxa_dispatch_agent_team`, `spryxa_get_command_center`, `spryxa_get_workflow_status`, `spryxa_list_workflow_runs`, `spryxa_list_pending_decisions`, `spryxa_get_grow_audience_status`.

Website, crawler, and site-change work:
Use the curated crawler tools registered by Spryxa for crawl, analysis status, analysis results, browser/page reads, and codegen support. For customer site changes use `spryxa_propose_site_change` first, then `spryxa_promote_site_change` only after explicit approval.

KPI ledger:
`spryxa_get_kpi_ledger`, `spryxa_record_kpi_snapshot`, `spryxa_seed_kpi_definitions`.

## Website Conversion Plan

When the user asks to "improve website conversion", "run CRO", "fix conversion issues", or "launch the website-conversion Plan", prefer the dedicated Plan workflow tool if it is available:

`spryxa_improve_website_conversion`

Expected Plan identity:
`teamSlug: "website"`, `outcomeSlug: "website-conversion"`, `agentKey: "improve-website-conversion"`.

Required analyses:
`GENERAL`, `SEO`, `BRAND_BOOK`.

Required Plan inputs:
`Site crawl`, `Editable site surface or implementation owner`, `Google Analytics 4`, `Search Console`, `Approval rules for visual or risky changes`.

Approval gates:
`Visual layout changes`, `Pricing or offer copy`, `Risky code or conversion changes`.

If the dedicated tool is not available, do not silently replace it with `spryxa_dispatch_agent_team`; tell the user that the dedicated MCP Plan tool still needs to be added. The generic dispatch path is not the same as the UI Plan launch path.

When launching the dedicated Plan workflow:

1. Resolve the project.
2. Ensure the required analyses and site crawl are ready.
3. Confirm all required Plan inputs and approval gates with the user.
4. Call the tool without `confirm:true` first if a confirmation preview is useful.
5. After explicit approval, call with `confirm:true`.
6. Report `team_run_id`, `mission_id`, `workflow_id`, `workflow_ids`, `status`, `child_runs`, and the next polling step.

If anything is missing, explain that nothing was started and no credits were spent, then name the exact remedy tool or Spryxa UI setup step.

## Common Operating Patterns

For "what can Spryxa do here", use `spryxa_get_project_capabilities`, not a raw integration audit.

For "what is connected", use `spryxa_list_integrations`.

For "start a mission", create or update the mission brief first, run the strategy sprint when the brief is ready, approve the plan only after the user has reviewed it, then dispatch the team.

For "create content", generate or update a draft first. Scheduling and publishing are separate actions and may require confirmation.

For "change the website", propose a site change first. Promotion/application is a separate approval-gated action.

For "what happened with the workflow", use workflow/run status tools and summarize concise status, blockers, approvals, and next step.
