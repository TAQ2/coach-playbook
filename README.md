# Coach Playbook

A personal life coaching system that runs in Claude Code. You clone it, fill in your details, and start talking. The repo holds your values, projects, life areas, and quarterly reflections — Claude reads it all and coaches you from real context, not generic advice.

Built on [Tiago Forte's PARA methodology](https://fortelabs.com/blog/para/) and his productivity pyramid (Purpose & Principles at the top, PARA for organisation, quarterly assessments for reflection).

## What you get

- An AI coach that knows your life — your priorities, what's stuck, what matters
- `/process` — after any conversation, Claude proposes which files to update and waits for your go-ahead
- `/radar` — a periodic scan that flags what's slipping, what's forgotten, and where to focus next
- `para-auditor` — an agent that checks your PARA files for structural mistakes
- Quarterly assessments with a Wheel of Life and reflection prompts
- A values exercise (Forte's Purpose & Principles + Feynman's 12 Favorite Problems)
- Inline tags (`@TODO`, `@WRITE`) that `/radar` picks up across all your files

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- A terminal

## Setup

1. Clone this repo
2. Open `CLAUDE.md` and replace the three placeholders:
   - `{{YOUR_NAME}}` — your first name
   - `{{SHORT_BIO}}` — one line: age, location, what you do
   - `{{LONG_TERM_GOAL}}` — your broad life direction in one sentence
3. Open `assessments/CLAUDE.md` and customise the Wheel of Life pillars to reflect your life areas
4. Start Claude Code **in this directory** and have your first conversation (see prompts below)

That's it. You don't need to understand PARA or the full system to begin. The system teaches itself to you through use — `/process` will show you how PARA works by proposing where your thoughts should go.

### Your first conversation

Pick one of these to start with. Say it in your own words — don't overthink it.

1. **What's taking up the most mental space in your life right now?**
2. **What's one thing you keep meaning to sort out but haven't?**
3. **If you could only fix one area of your life this quarter, what would it be?**
4. **What's actually going well that you haven't given yourself credit for?**
5. **What would you be embarrassed to still be dealing with in 6 months?**

After that, let the coach ask you questions. It will dig deeper, make connections, and help you think things through. When the conversation reaches a natural pause, run `/process` to capture anything worth keeping.

### When you're ready (not now)

- [ ] Do the values exercise in `purpose-and-principles.md`
- [ ] Do your first quarterly assessment (copy `assessments/quarterly/YYYY-QN-example.md`)
- [ ] Delete the example files (`para/projects/_example-project.md`, `para/areas/_example-area.md`, `assessments/quarterly/YYYY-QN-example.md`) once you have real ones
- [ ] (Optional) Connect a task manager — see "Integrations" below

## How it works

You talk freely. Claude listens. No files change until you say so.

When you're ready to capture what was discussed, run `/process`. Claude reviews the conversation, proposes specific updates to specific PARA files, and waits for your confirmation before editing anything.

Periodically run `/radar` to get a coach's-eye view of your life: what needs attention, what's been forgotten, where momentum is building or dying.

The **repo is the source of truth** — not Claude's memory. This means you can use Claude from any machine and your coach always has full context.

## Slash commands

| Command | What it does |
|---------|-------------|
| `/process` | Reviews conversation, proposes PARA file updates, waits for confirmation |
| `/radar` | Scans all files for what's slipping, forgotten, or needs focus |

## Tags

Two inline tags mark actionable items across your PARA files:

- `@TODO` — something you need to do (actions, follow-ups, measurements). Optional context: `@TODO(quarterly)`, `@TODO(dentist)`
- `@WRITE` — content that needs producing or fleshing out

Tags live inline where the context is. When done, delete the tag (commit history records it existed).

## Agents

| Agent | What it does |
|-------|-------------|
| `para-auditor` | Read-only audit of PARA files for structural correctness and methodology compliance |

## Folder structure

| Path | Purpose |
|------|---------|
| `CLAUDE.md` | Main system prompt — your coach's instructions |
| `inbox.md` | Dump unprocessed thoughts here |
| `purpose-and-principles.md` | Values exercise + 12 Favorite Problems |
| `para/` | PARA structure — projects, areas, resources, archive |
| `para/projects/` | Active work with a specific outcome and done state |
| `para/areas/` | Ongoing responsibilities, maintained to a standard |
| `para/resources/` | Reference material |
| `para/archive/` | Completed or retired items |
| `assessments/` | Quarterly assessments (happiness + wheel + reflection) |
| `sessions/log/` | Session logs — only when something meaningful shifted |

## Integrations (optional)

The core system works without any integrations. If you use a task manager with an API (Todoist, TickTick, etc.), you can:

1. Save a token file (e.g. `.todoist_token`) — these are gitignored
2. Add API commands to `CLAUDE.md` under an integrations section
3. Add relevant permissions to `.claude/settings.local.json`

## What this has surfaced for people

Real moments from using this system:

- **A health root cause chain became visible.** Tracking a health project in PARA revealed a dependency chain: low energy → poor sleep → undiagnosed sleep apnoea. The system made a complex health puzzle navigable by keeping all the threads in one place — one sleep study later, everything shifted.
- **A broken habit system got redesigned.** Tracking 5-10 habits on paper kept failing. Talking it through revealed the real problem: remembering to check the list was itself a habit that never stuck. The fix was fewer habits with timed push reminders instead of a long pull list. The insight was that the system design was wrong, not the discipline.
- **A new life area appeared without being noticed.** "Community" didn't exist as a life area until a quarterly assessment forced the question. Turns out real progress had been happening — co-founding an organisation, attending meetings — but it hadn't been named or acknowledged.
- **The system called out its own over-optimisation.** Multiple attempts to restructure files and add new tags were met with pushback from the coach: "there are gaping holes in the existing content — fill those first." The system kept its user honest.
- **Commit history contradicted the feeling of stuckness.** After a quarter that felt like nothing had moved, `/radar` used `git log` to show what actually changed. The diffs told a different story — real progress buried under the feeling of being stuck.

## Philosophy

- **Repo is source of truth.** Everything that matters lives in files, not in Claude's memory.
- **Organising is procrastination in disguise.** The system resists over-optimisation. Don't polish the system — use it.
- **Commit history as progress signal.** Diffs show what actually changed, not just what was discussed.
- **Conversation first.** Talk freely. File updates come later, only when you're ready.
- **No files edited without confirmation.** Claude proposes. You approve.
