---
name: spryxa-improve-website-conversion
description: "Improve website conversion with Spryxa: run the website-conversion Plan/CRO workflow, check required crawl and analyses, and route site-change proposals for approval."
---

# Spryxa Improve Website Conversion

Use this skill when the user asks Spryxa to improve website conversion, run CRO, fix conversion friction, review UX/CTA/trust issues, or launch the website-conversion Plan.

Start with `spryxa_whoami`, then always show the user the active projects before launching this workflow. Call `spryxa_list_projects`, present the project names clearly, and ask the user which project to use unless they already named an exact project in the same request.

After the user chooses a project, call `spryxa_set_active_project` with that project id or synthetic id. Use the selected project id for every subsequent call in this flow, including analysis repair, crawl repair, readiness checks, and the final `spryxa_improve_website_conversion` launch.

When calling `spryxa_improve_website_conversion`, set `project_selection_confirmed:true` only after this project-list and selection step has happened. If this field is false or omitted, the tool will refuse and return the accessible project list to show the user.

Do not start the website-conversion workflow against a guessed or stale active project. If there is only one active project, state the project name and ask for confirmation before setting/using it.

Prefer the dedicated MCP tool when available: `spryxa_improve_website_conversion`.

The Plan identity must be:
`teamSlug: "website"`, `outcomeSlug: "website-conversion"`, `agentKey: "improve-website-conversion"`.

Required analyses:
`GENERAL`, `SEO`, `BRAND_BOOK`.

Required inputs to confirm with the user:
`Site crawl`, `Editable site surface or implementation owner`, `Google Analytics 4`, `Search Console`, `Approval rules for visual or risky changes`.

Approval gates to confirm:
`Visual layout changes`, `Pricing or offer copy`, `Risky code or conversion changes`.

If anything is missing, stop and explain that nothing was started and no credits were spent. Name the remedy, such as running a crawl/analysis, connecting GA4/Search Console, or completing setup in Spryxa.

When a required analysis is missing, ask the user before starting the repair. For example: "SEO analysis is missing. Should I run it now?" If the user says yes, call `spryxa_retry_failed_analysis` with the missing analysis type, then poll `spryxa_get_analysis_status` until it completes. Once all required analyses are complete, ask once before launching `spryxa_improve_website_conversion`.

When no site crawl / `synthetic_id` exists, ask the user before starting a crawl. Use `spryxa_audit_website` when a website URL is available, then poll `spryxa_get_analysis_status`. After the crawl and required analyses complete, return to the website-conversion launch.

Do not auto-launch the Plan just because a prerequisite finished. Ask the user to approve the final workflow launch.

If the tool returns `confirmation_required`, explain the launch and credit spend, then re-call with `confirm:true` only after the user approves.

After launch, report `team_run_id`, `mission_id`, `workflow_id`, `workflow_ids`, `status`, `child_runs`, and the next polling step. Poll with `spryxa_list_workflow_runs` or `spryxa_get_workflow_status` depending on the returned ids.

Do not treat Plan approval-gate confirmation as permission to publish or apply future risky changes. Nova's final site-change proposals still require separate approval.
