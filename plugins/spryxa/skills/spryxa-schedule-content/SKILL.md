---
name: spryxa-schedule-content
description: Schedule or publish Spryxa content safely, using content queue, calendar, confirmation, and publishing MCP tools.
---

# Spryxa Schedule Content

Use this skill when the user wants to schedule, queue, reschedule, publish, or inspect planned content.

Start with `spryxa_get_session`. If no project is active, use `spryxa_list_projects` and `spryxa_update_session_project`.

Useful tools:
`spryxa_list_content_review_queue`, `spryxa_list_content_items`, `spryxa_get_content_item`, `spryxa_schedule_content_items`, `spryxa_publish_content_item`, `spryxa_update_content_item`.

Before scheduling, make sure the target content, platform, date/time, timezone, and recipient/channel are clear.

Before publishing or sending, confirm the final copy and destination. If the tool requires `confirm:true`, ask the user before re-calling.

Do not bulk-send email unless the tool and user request explicitly allow it. Respect any tool errors about reviewed recipients, consent, missing connections, or approval state.
