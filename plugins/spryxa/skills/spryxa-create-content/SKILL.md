---
name: spryxa-create-content
description: Create Spryxa content drafts for social, email, blog, or campaign use, then refine, save, schedule, or publish through the proper MCP approval flow.
---

# Spryxa Create Content

Use this skill when the user wants Spryxa to create, draft, rewrite, repurpose, or improve marketing content.

Start with `spryxa_whoami`. If no project is active, use `spryxa_list_projects` and `spryxa_set_active_project`.

Useful tools:
`spryxa_generate_content`, `spryxa_update_content`, `spryxa_list_content_library`, `spryxa_get_content`, `spryxa_get_content_queue`, `spryxa_get_insights`, `spryxa_get_audit`.

Create or update drafts first. Do not schedule or publish unless the user asks for that next step.

If generation cannot run because credits or setup cannot be verified, provide a chat-only draft and be clear that nothing was saved, queued, scheduled, or published.

For scheduling use `spryxa_schedule_content` or `spryxa_schedule_series`. For publishing use `spryxa_publish_content`, and only after explicit confirmation when required.

When a tool returns `confirmation_required`, summarize what will change and re-call with `confirm:true` only after the user approves.
