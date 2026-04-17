# Agent Handoff Export

This bundle is a safe export of the current agent's reusable identity, memory, and workspace-local expertise.

## Included

- `SOUL.md` — personality/tone
- `AGENTS.md` — operating rules
- `USER.md` — user context
- `IDENTITY.md` — self-description
- `TOOLS.md` — local notes template
- `MEMORY.md` — curated long-term memory
- `memory/` — recent notes/history
- `skills/` — workspace-local custom skills

## Not Included

- `~/.openclaw/openclaw.json`
- `~/.openclaw/agents/...`
- auth tokens, API keys, OAuth sessions
- gateway tokens
- machine-specific service config

Those are intentionally excluded because they may contain secrets.

## How to use in another OpenClaw instance

1. Copy these files into that agent's workspace root.
2. Merge carefully if files already exist.
3. Place the exported `skills/` directory into the target workspace so the skills are discoverable.
4. Restart or refresh the target OpenClaw session.
5. Tell the target agent to read:
   - `SOUL.md`
   - `USER.md`
   - `AGENTS.md`
   - `MEMORY.md`
   - relevant files under `memory/`
   - any needed `skills/*/SKILL.md`

## Suggested prompt for the new agent

"Adopt the attached workspace identity and operating context. Read SOUL.md, USER.md, AGENTS.md, MEMORY.md, and the recent memory files first. Then treat the included skills as your local specialized expertise. Mimic the same behavior and constraints as closely as possible, while keeping your own runtime/auth configuration separate."

## Fidelity note

This will produce a close behavioral copy, not a bit-perfect clone. Exact behavior still depends on:

- model choice
- OpenClaw version
- runtime config
- available tools
- local machine environment

## Safety note

Do not export raw auth/config files unless you explicitly want to migrate credentials too.
