---
name: spryxa-create-content
description: Create Spryxa content drafts for social, email, blog, or campaign use, then refine, save, schedule, or publish through the proper MCP approval flow.
---

# Spryxa Create Content

Use this skill when the user wants Spryxa to create, draft, rewrite, repurpose, or improve marketing content.

Start with `spryxa_get_session`. If no project is active, use `spryxa_list_projects` and `spryxa_update_session_project`.

Useful tools:
`spryxa_start_content_generation`, `spryxa_update_content_item`, `spryxa_list_content_items`, `spryxa_get_content_item`, `spryxa_list_content_review_queue`, `spryxa_get_insights_overview`, `spryxa_get_site_analysis`.

Create or update drafts first. Do not schedule or publish unless the user asks for that next step.

If generation cannot run because credits or setup cannot be verified, provide a chat-only draft and be clear that nothing was saved, queued, scheduled, or published.

For scheduling use `spryxa_schedule_content_items` (one item, or the whole dated set in one call). For publishing use `spryxa_publish_content_item`, and only after explicit confirmation when required.

When a tool returns `confirmation_required`, summarize what will change and re-call with `confirm:true` only after the user approves.
