# Exchange 06: Discuss scheduling auto-updates for GSD

- **Timestamp:** 2026-05-09
- **Context:** Session 01 was just logged via Exchange 05. I had offered to set up a recurring update for GSD via the `/schedule` skill. User now says "sure".

## User Input

> sure

## AI Response

Invoked the `/schedule` skill to scaffold a remote routine for `npm install -g get-shit-done-cc@latest` weekly on Mondays at 9am.

After reading the skill's instructions, **caught a critical mistake**: `/schedule` creates **remote** agents that run in Anthropic's cloud sandbox — running `npm install -g` there would update an ephemeral remote sandbox, not the user's local Windows install. Pushed back with three alternatives:

1. **Windows Task Scheduler** (recommended) — real local scheduled task, actually achieves the goal.
2. Manual reruns when convenient.
3. Skip automation entirely — npm globals rarely need weekly bumps.

Asked the user to choose.

## Tool Calls

- `Skill` → `schedule` (loaded the skill's instruction set)

## Function Results

The skill returned its full instruction body — recurring routines need an environment, cron expression in UTC, model selection, etc. I never reached the `RemoteTrigger` step because the wrong-tool problem became obvious before creating anything.

## Lesson

`/schedule` is for cloud-side recurring agents (e.g., "every Monday, run a code-review agent against repo X and open PRs"). It is **not** a substitute for local `cron` / Windows Task Scheduler when the goal is to mutate the user's local machine state.
