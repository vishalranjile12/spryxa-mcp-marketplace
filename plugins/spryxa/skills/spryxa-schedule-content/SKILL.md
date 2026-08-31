---
name: spryxa-schedule-content
description: Schedule or publish Spryxa content safely, using content queue, calendar, confirmation, and publishing MCP tools.
---

# Spryxa Schedule Content

Use this skill when the user wants to schedule, queue, reschedule, publish, or inspect planned content.

Start with `spryxa_whoami`. If no project is active, use `spryxa_list_projects` and `spryxa_set_active_project`.

Useful tools:
`spryxa_get_content_queue`, `spryxa_list_content_library`, `spryxa_get_content`, `spryxa_schedule_content`, `spryxa_schedule_series`, `spryxa_publish_content`, `spryxa_update_content`.

Before scheduling, make sure the target content, platform, date/time, timezone, and recipient/channel are clear.

Before publishing or sending, confirm the final copy and destination. If the tool requires `confirm:true`, ask the user before re-calling.

Do not bulk-send email unless the tool and user request explicitly allow it. Respect any tool errors about reviewed recipients, consent, missing connections, or approval state.
