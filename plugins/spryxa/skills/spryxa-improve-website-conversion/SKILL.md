---
name: spryxa-improve-website-conversion
description: "Improve website conversion with Spryxa: launch the Website Crew Plan/CRO workflow and route site-change proposals for approval."
---

# Spryxa Improve Website Conversion

Use this skill when the user asks Spryxa to improve website conversion, run CRO, fix conversion friction, review UX/CTA/trust issues, or launch the website-conversion Plan.

For the exact request "Improve website conversion with Spryxa", use the active project and launch immediately. Do not ask for launch confirmation and do not run separate crawl, analysis, integration, readiness, workflow-catalog, or next-action checks first.

If no project is active, resolve or select the project first. This is the only setup question that may precede launch.

Call `spryxa_start_workflow` with `workflow: "website_conversion"`, `inputs: {}`, and the active `project_id`. The pre-v4 `spryxa_improve_website_conversion` name is rewritten onto it.

The MCP launch creates a Marketing Team run (`mtr_<12-hex>`) whose Temporal workflow class is `PersonaWorkflow` and whose workflow type is `nova-agent`. It routes through `target_channels: ["website"]` without `team: "web"`, so Nova runs the full conversion workflow instead of direct-change mode.

Nova owns crawl, analysis, integration, editable-surface, and approval-rule validation inside the workflow. Report a blocked workflow state and its remedy after launch; do not duplicate those checks in Codex.

After launch, report `workflow_run_id`, `kind: "team_run"`, `status`, and the next polling step. Poll with `spryxa_get_workflow_run`.

Do not treat Plan approval-gate confirmation as permission to publish or apply future risky changes. Nova's final site-change proposals still require separate approval.
