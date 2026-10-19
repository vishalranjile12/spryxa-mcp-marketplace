---
name: spryxa-run-mission
description: "Run Spryxa missions and agent teams: create or update mission briefs, run strategy sprints, approve plans, dispatch teams, and monitor workflows."
---

# Spryxa Run Mission

Use this skill when the user wants to create a mission, run a strategy sprint, approve a mission plan, dispatch an agent team, transition mission phases, or monitor mission execution.

Start with `spryxa_get_session`. If no project is active, use `spryxa_list_projects` and `spryxa_update_session_project`.

Useful tools:
`spryxa_create_mission`, `spryxa_update_mission_brief`, `spryxa_start_mission_strategy_sprint`, `spryxa_approve_mission_plan`, `spryxa_update_mission_phase`, `spryxa_start_agent_team_run`, `spryxa_list_agent_teams`, `spryxa_list_missions`, `spryxa_get_mission`, `spryxa_get_mission_command_center`, `spryxa_get_workflow_run`, `spryxa_list_workflow_runs`.

For a new mission, gather goal, audience, offer, timeframe, success metric, and relevant assets before running strategy.

Do not approve a mission plan until the user has reviewed it. Do not dispatch a team or transition into execution without explicit approval when the tool requires confirmation.

When reporting status, include the mission phase, plan approval state, active runs, blockers, pending decisions, and next recommended action.
