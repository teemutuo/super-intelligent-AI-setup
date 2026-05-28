# Superintelligent AI Toolkit

Eleven installable skills and two bootstrap prompts. Climbs the Superintelligence Ladder from Level 1 to Level 5. Tested in my own daily work. Sanitized for general use. MIT licensed.

## What is in the box

Skills (auto-trigger as a Claude plugin, or paste into any LLM as system instructions):

| # | Skill | What it does |
|---|-------|--------------|
| 01 | brand-voice | Your company voice as a template. Drop in placeholders, get consistent writing everywhere. |
| 02 | animated-slideshow | Battle-tested patterns for building polished single-file HTML slide decks. |
| 03 | board-panel | Convene a five-lens panel before any non-trivial decision. |
| 04 | department-router | Route a query to the right business function lens (Finance, Legal, IT, People, Ops, Sales, Strategy). |
| 05 | quality-gate | Eight-check verification policy that runs after any significant output. |
| 06 | commentary-engine | Five-move narrative on any numerical data. Lead with the insight, end with the action. |
| 07 | morning-brief | Daily scheduled briefing. News, peer moves, regulatory, calendar, risks. Under five minutes to read. |
| 10 | sensitivity-templates | Five fallback patterns for when the data cannot be pasted. |
| 11 | superintelligence-ladder | Six-level maturity model. Self-assess, plan the next move. |
| 12 | prompt-power-words | Five phrases that switch Claude from fast to careful: ultrathink, maxeffort, ultraplan, run the panel, critique yourself. |

Prompts (paste once, save the memory):

| # | Prompt | What it does |
|---|--------|--------------|
| 08 | memory-bootstrap | Fill the placeholders. Tell Claude who you are, where you work, how you write. Memory grows from here. |
| 09 | setup-interview | Five rounds of interview that design your personal setup. Outputs: skills to install, connectors, scheduled tasks, stakeholders to loop in, first month roadmap. |

## Order of operations

1. Run **prompts/08-memory-bootstrap.txt** in a fresh Claude conversation. Fill the placeholders honestly. This is the single highest-leverage hour in the whole setup.
2. Install the skills you need from this repo. The plugin install puts the whole bundle in place automatically. Manual install instructions in `docs/install.md`.
3. Run **prompts/09-setup-interview.txt** in the same Claude conversation. Five rounds. Out comes your personal roadmap.
4. Pick one skill from the roadmap. Use it on one real piece of work this week. Then a second skill next week.
5. Schedule **morning-brief** (skill 07) when you trust the manual version. That is your first scheduled task.

## Who this is for

Any business professional with a calendar, an inbox, and decisions to make. Concrete examples by role:

- **Product manager:** decision-analyzer on roadmap forks. pack-reader on long PRDs. voice-writer for the Slack ping nobody wants to send.
- **Sales director:** morning-brief on tomorrow's calls. board-panel before negotiating a key renewal. voice-writer for the "we missed the quarter" email.
- **Finance manager (not the CFO):** commentary-engine on month-end variance. sensitivity-templates on actuals not yet published. quality-gate before submitting to the controller.
- **In-house counsel:** board-panel on policy decisions. pre-mortem-style risk lens via run-the-panel. sensitivity-templates as the default for any personal data of others.
- **Anyone on a development arc:** sparring-partner as the year-long coaching agent. Set a quarterly theme, run weekly sessions, review at quarter end.
- **Founder, consultant, designer, engineer:** the kit is role-agnostic; the templates work once you fill in placeholders.

## The principle

Climb the ladder one rung at a time. People who try to skip from Level 2 to Level 5 fall back to Level 1. Memory before skills. Skills before agents. Each rung makes the next one possible.

## Install

Plugin install on Claude Cowork (recommended), Custom GPTs on ChatGPT, agents on Microsoft Copilot, or system prompts on any LLM. See `docs/install.md` for the exact pa