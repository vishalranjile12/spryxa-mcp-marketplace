---
name: spryxa-propose-site-change
description: Propose, review, and promote Spryxa website changes safely, keeping risky layout, pricing, offer, code, and conversion changes approval-gated.
---

# Spryxa Propose Site Change

Use this skill when the user wants Spryxa to create, review, stage, or promote a website change.

Start with `spryxa_whoami`. If no project is active, use `spryxa_list_projects` and `spryxa_set_active_project`.

Useful tools:
`spryxa_get_audit`, `spryxa_read_site_page`, `spryxa_propose_site_change`, `spryxa_promote_site_change`, `spryxa_list_pending_decisions`, `spryxa_get_command_center`, `spryxa_list_workflow_runs`.

Use `spryxa_propose_site_change` for a reviewable proposed change first. Use `spryxa_promote_site_change` only after the user explicitly approves promotion/application.

Risky visual layout changes, pricing or offer copy, and code/conversion changes need clear user approval. Do not treat earlier Plan confirmation as approval to apply a site change.

If local repository or site-change preconditions fail, stop and explain what setup is missing.
