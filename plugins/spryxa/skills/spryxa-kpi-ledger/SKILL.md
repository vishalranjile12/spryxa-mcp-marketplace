---
name: spryxa-kpi-ledger
description: Inspect, seed, and record Spryxa KPI ledger snapshots for weekly metrics, floors, tripwires, and performance tracking.
---

# Spryxa KPI Ledger

Use this skill when the user wants to review KPIs, seed KPI definitions, record metric snapshots, or run a weekly performance ledger rhythm.

Start with `spryxa_get_session`. If no project is active, use `spryxa_list_projects` and `spryxa_update_session_project`.

Useful tools:
`spryxa_get_kpi_ledger`, `spryxa_create_kpi_definitions`, `spryxa_create_kpi_snapshot`, `spryxa_get_insights_overview`, `spryxa_get_ads_performance`, `spryxa_list_email_campaign_stats`, `spryxa_get_email_audience`.

Read the current ledger before writing. When recording a snapshot, confirm the metric source, period, value, and interpretation.

If seeding definitions requires confirmation, explain what definitions will be added and re-call with `confirm:true` only after the user approves.
