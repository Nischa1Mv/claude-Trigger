# claude Trigger

Repo backing a scheduled cloud-agent routine (via Claude Code's remote-trigger / routines system).

## Purpose

Keep Claude's 5-hour usage windows warm ahead of work hours, so the window is already
open when actual work starts — instead of losing the first chunk of a session mid-task.

## Plan

- Two daily firings: 7:00 AM IST and 12:00 AM IST (converted to UTC cron: `30 1,18 * * *`)
- Each firing spins up a cloud Claude Code session pointed at this repo, running a trivial
  no-op prompt (e.g. "acknowledge, nothing needed") — just enough to count as session activity.
- Setup uses the `RemoteTrigger` tool (`action: create`) with `job_config.ccr` pointing at:
  - `environment_id`: env_012FddwjWLKBzsbTfPK8CFtW (Default)
  - `session_context.sources`: this repo (`https://github.com/Nischa1Mv/claude-Trigger`)
  - `session_context.model`: claude-sonnet-5

## Status

Not yet created — repo and plan only. Routine creation deferred to later session.
