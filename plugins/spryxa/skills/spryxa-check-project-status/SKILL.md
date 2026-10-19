---
name: spryxa-check-project-status
description: "Check what Spryxa can do for a project: project status, capabilities, audits, reports, integrations, missions, workflow runs, pending approvals, and credits."
---

# Spryxa Check Project Status

Use this skill when the user asks what is ready, what is connected, what Spryxa can do, what is running, what needs approval, or why something is blocked.

Start with `spryxa_get_session`. If no project is active, use `spryxa_list_projects` and `spryxa_update_session_project`.

Use `spryxa_get_project_capabilities` for a user-friendly capability menu. Use `spryxa_list_platform_connections` for connected accounts and setup gaps.

Useful status tools:
`spryxa_get_project`, `spryxa_get_billing_credits`, `spryxa_get_project_capabilities`, `spryxa_list_platform_connections`, `spryxa_get_insights_overview`, `spryxa_list_site_analyses`, `spryxa_get_site_analysis`, `spryxa_list_missions`, `spryxa_get_mission`, `spryxa_get_mission_command_center`, `spryxa_list_workflow_runs`, `spryxa_get_workflow_run`

Summarize in plain language: ready items, blocked items, running work, pending approvals, and the next best action.

Poll async workflows at most once per turn unless the user asks you to actively wait.
