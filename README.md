# vexa-openclaw-skills

**OpenClaw skills for [Vexa](https://vexa.ai)** — send transcription bots to meetings, read live or final transcripts, and turn finished meetings into meeting reports inside your OpenClaw workspace.

## What this is

This repo holds **skills** (tools + instructions) that an OpenClaw agent can use to work with Vexa:

- **Send bots** to Google Meet or Microsoft Teams from a meeting link or calendar event
- **Read transcripts** during or after a meeting
- **Create meeting reports** (summary, decisions, action items, full transcript) into `memory/meetings/`
- **Configure webhooks** so finished meetings automatically trigger report creation
- **Manage meetings** (list, update metadata, share transcript links, optional delete with confirmation)

The agent speaks to you in chat and runs the underlying scripts when you share a Meet/Teams link, ask to join from calendar, or want transcripts and summaries.

## Layout

```
vexa-openclaw-skills/
├── README.md           # this file
└── vexa/               # the Vexa skill
    ├── SKILL.md        # skill definition + usage (for the agent)
    ├── scripts/        # CLI entrypoints (vexa.mjs, onboard.mjs, ingest.mjs, …)
    └── references/     # onboarding, webhook setup, API notes
```

- **`vexa/`** — single skill; no nested git repo. All scripts are run as `node skills/vexa/scripts/<script>.mjs ...` from the OpenClaw workspace root.

## Requirements

- **OpenClaw** workspace (this skill is loaded from `workspace/skills/vexa` or equivalent).
- **Vexa API key** from [vexa.ai/dashboard/api-keys](https://vexa.ai/dashboard/api-keys). Stored in `vexa/secrets/vexa.env` (gitignored).

Optional: `VEXA_BASE_URL` if you use a custom API base (default: `https://api.cloud.vexa.ai`).

## Quick start (for OpenClaw)

1. **Copy or symlink** this repo’s `vexa` folder into your OpenClaw workspace skills dir, e.g.  
   `workspace/skills/vexa` → contents of `vexa-openclaw-skills/vexa/`.

2. **Secrets**  
   Create `vexa/secrets/vexa.env` with your API key (or let the agent guide you via onboarding).

3. **Use in chat**  
   Paste a Google Meet or Teams link and ask to send a bot, or ask for a report after a meeting. The agent uses `SKILL.md` and the scripts under `vexa/scripts/`.

See **`vexa/SKILL.md`** for the full command set, webhook setup, and platform rules (Google Meet, Teams, deletion safety).

## License

Use and adapt as needed for your OpenClaw setup.
