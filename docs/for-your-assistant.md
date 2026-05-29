# For your assistant or Chief of Staff, a one-page brief

If you are an executive reading this and the idea of pasting prompts into a chatbot is not how you spend your time, hand this page to the person who runs your day. They will have you up in about a week.

## What this is

A personal AI productivity setup for the executive you support. After install, it saves them roughly eight to fourteen hours of weekly admin: drafting, briefing, summarising, scanning, decision rehearsal. It is described in detail in [`../README.md`](../README.md); this is the one-pager for the person doing the install.

## What you do, in order

### Week 1 — interview them (3 x 15 min)

The single most important hour in the whole setup. Open `prompts/08-memory-bootstrap.txt`, read the bracketed placeholders out to your executive, and capture their answers verbatim. Their job title, their company, their tools, their writing samples, the people who matter most, the decisions they keep deferring. Two or three minutes per question is enough.

Output: one file, `my-profile.md`, saved in their AI's private project knowledge. Never commit this file to a public repo.

### Week 2 — connect tools (~10 minutes)

Two OAuth connections in their AI account:

- Microsoft 365 or Google Workspace, for calendar and email
- Slack or Microsoft Teams, for the morning brief delivery

Before you click anything, send the five-question email from `docs/governance.md` to your CISO and wait for the reply. This step protects everyone.

### Week 3 to 7 — install skills, one per week

Each skill is its own folder in `skills/`. The install pattern is the same for all:

1. Open the SKILL.md file.
2. In your executive's AI account, create a new Skill, Custom GPT, or Project (terminology varies by client).
3. Paste the prompt body (everything below the YAML frontmatter) into Instructions.
4. Attach `my-profile.md` as project knowledge.
5. Test it with them in person for five minutes.

The order to install:

1. `superintelligence-ladder` (11), so they can self-assess where they sit.
2. `prompt-power-words` (12), the smallest thing that delivers the biggest quality lift.
3. `brand-voice` (01), so every other output starts sounding like them.
4. `commentary-engine` (06), if their week involves explaining numbers.
5. `board-panel` (03), the decision-rehearsal pattern.
6. `morning-brief` (07), the one you will eventually promote to a scheduled agent.

After each install, use it on a real piece of work that week. The skill earns its place by being used, not by being installed.

### Week 8 — review with them

Spend thirty minutes going through every skill output from the past four weeks. Mark each: useful, neutral, not useful. Anything below 60% useful, rework with them. Anything above 60%, candidate for scheduling.

### Week 9 to 11 — schedule the agents

Only after the manual versions have proven themselves. The three default schedules:

- `morning-brief`, daily at 06:30
- A market or industry scan, daily at 07:00 (designed via the setup interview)
- A regulatory radar, Mondays at 08:00 (designed via the setup interview)

All three are read-only. They surface and link, never commit on the executive's behalf.

### Week 12 onwards

Maintenance mode. Refresh the memory bootstrap with them every quarter. Watch the agents for drift. Kill anything that stops earning its keep.

## What your executive does

- Sits for the three memory-bootstrap interview sessions in week 1.
- Uses the skills you install on real work, one per week.
- Tells you what is working and what is not.
- Approves the agents going on a schedule in weeks 9 to 11.

That is it. They do not need to know any technical detail. You handle the setup; they get the leverage.

## What you do not need

- A developer.
- A new software purchase line.
- An AI agent platform subscription.
- Approval from procurement, assuming your firm already pays for Claude, ChatGPT, or Copilot.

## When to escalate

Bring in your CISO or General Counsel before:

- Connecting any calendar, email, or chat tool to the AI for the first time.
- Running the kit on a real board pack.
- Turning on any of the scheduled agents.

The five-question CISO email in [`governance.md`](./governance.md) is the cleanest starting point.

## How to know you are done

- Your executive opens Slack/Teams DMs before email every morning because the morning brief is there.
- They walk into meetings holding a one-page brief instead of asking you for talking points.
- A peer asks for the setup. You forward this repo URL.

Eight to fourteen hours of weekly admin reclaimed for the executive. About sixty minutes of setup work per week for you, across twelve weeks. The maths is good.
