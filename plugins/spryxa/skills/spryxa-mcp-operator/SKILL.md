---
name: spryxa-mcp-operator
description: "Use when operating Spryxa through MCP tools: project setup, integrations, audits, content, campaigns, missions, agent teams, workflow status, site changes, KPI ledger, or the website-conversion Plan workflow."
---

# Spryxa MCP Operator

Use this skill when the user wants Codex or another agent to operate Spryxa through the `spryxa_*` MCP tools.

## First Step

Start each new Spryxa MCP session with `spryxa_get_session`.

If the response says project selection is needed, call `spryxa_list_projects`, ask or infer the intended project, then call `spryxa_update_session_project`. If the user is new, collect the website/domain and the user's role before creating the organization.

Never ask for passwords, cookies, API keys, or OAuth tokens. OAuth approval happens in the user's browser through Spryxa connection tools or the Spryxa UI.

## Safety Rules

Treat Spryxa tool scopes and preconditions as server truth. If a tool reports missing setup, missing data, insufficient scope, insufficient credits, or `confirmation_required`, stop and explain the exact next step.

Do not publish, launch, promote, send, disconnect, enable higher autonomy, or start credit-spending async work without explicit user approval. When a write tool requires `confirm:true`, first explain what will happen, then call it again only after the user agrees.

Approval-gate confirmation for a Plan launch means the user acknowledges who owns approvals. It does not approve future visual, pricing, offer, risky code, publishing, campaign, or site changes.

Poll async workflows at most once per turn unless the user asks for active waiting. Prefer `spryxa_get_workflow_run` when a run id is available and `spryxa_list_workflow_runs` when it is not.

## Tool Groups

Project and account context:
`spryxa_get_session`, `spryxa_create_organization`, `spryxa_list_projects`, `spryxa_get_project`, `spryxa_update_session_project`, `spryxa_get_billing_credits`, `spryxa_disconnect_session`.

Project intelligence:
`spryxa_get_insights_overview`, `spryxa_list_site_analyses`, `spryxa_get_site_analysis`, `spryxa_get_project_capabilities`, `spryxa_search`, `spryxa_fetch`.

Integrations:
`spryxa_list_platform_connections`, `spryxa_connect_platform`, `spryxa_get_platform_connection_status`, `spryxa_disconnect_platform`, `spryxa_list_platform_actions`, `spryxa_run_platform_action`.

Content and publishing:
`spryxa_start_content_generation`, `spryxa_update_content_item`, `spryxa_list_content_items`, `spryxa_get_content_item`, `spryxa_list_content_review_queue`, `spryxa_schedule_content_items`, `spryxa_publish_content_item`.

Campaigns, CRM, email, and audience:
`spryxa_create_ads_campaign_draft`, `spryxa_launch_ads_campaign`, `spryxa_get_ads_performance`, `spryxa_list_crm_contacts`, `spryxa_update_crm_contact`, `spryxa_list_email_campaign_stats`, `spryxa_send_email_campaign`, `spryxa_get_email_audience`, `spryxa_start_outreach_pipeline_play`.

Missions, agent teams, and workflow orchestration:
`spryxa_list_agent_teams`, `spryxa_list_missions`, `spryxa_get_mission`, `spryxa_create_mission`, `spryxa_update_mission_brief`, `spryxa_start_mission_strategy_sprint`, `spryxa_approve_mission_plan`, `spryxa_update_mission_phase`, `spryxa_start_agent_team_run`, `spryxa_get_mission_command_center`, `spryxa_get_workflow_run`, `spryxa_list_workflow_runs`

Website, crawler, and site-change work:
Use the curated crawler tools registered by Spryxa for crawl, analysis status, analysis results, browser/page reads, and codegen support. For customer site changes use `spryxa_start_site_change` first, then `spryxa_promote_site_change` only after explicit approval.

KPI ledger:
`spryxa_get_kpi_ledger`, `spryxa_create_kpi_snapshot`, `spryxa_create_kpi_definitions`.

## Website Conversion Plan

When the user asks to "improve website conversion", "run CRO", "fix conversion issues", or "launch the website-conversion Plan", start the Plan workflow in one call:

`spryxa_start_workflow` with `workflow: "website_conversion"` and `inputs: {}`.

For the exact request "Improve website conversion with Spryxa", use the active project and launch immediately. Do not call readiness, analysis, connection, workflow-catalog, or next-action tools first, and do not ask for launch, ownership, integration, or approval-gate confirmation. Nova validates those conditions inside the workflow. Only resolve a project first when none is active.

Expected MCP identity: Marketing Team run `mtr_<12-hex>`, Temporal workflow class `PersonaWorkflow`, workflow type `nova-agent`.

Report `workflow_run_id`, `kind: "team_run"`, `status`, and the next polling step. Later site-change application or promotion remains separately approval-gated.

## Common Operating Patterns

For "what can Spryxa do here", use `spryxa_get_project_capabilities`, not a raw integration audit.

For "what is connected", use `spryxa_list_platform_connections`.

For "start a mission", create or update the mission brief first, run the strategy sprint when the brief is ready, approve the plan only after the user has reviewed it, then dispatch the team.

For "create content", generate or update a draft first. Scheduling and publishing are separate actions and may require confirmation.

For "change the website", propose a site change first. Promotion/application is a separate approval-gated action.

For "what happened with the workflow", use workflow/run status tools and summarize concise status, blockers, approvals, and next step.
