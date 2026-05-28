---
name: morning-brief
description: |
  Scheduled morning briefing skill. Pulls overnight news, peer moves, regulatory updates, calendar, and top risks into a sub-five-minute read delivered before the working day starts. Designed to run as a daily scheduled task at 07:00 to 07:30 local time.
metadata:
  version: "1.0.0"
  license: "Use freely"
---

# Morning Brief · Scheduled Skill

## When to Trigger

- Scheduled task, runs daily at [[YOUR PREFERRED TIME, typically 07:00]]
- Manually invoked when the user says: morning brief, daily brief, start my day, briefing

## What Goes In

Configure your sources by replacing placeholders:

- **News connectors:** [[YOUR NEWS MCP, e.g., a curated RSS, web fetch of trusted sources]]
- **Peer monitoring:** [[YOUR PEER LIST, NAMED COMPANIES OR TICKERS]]
- **Regulatory tracking:** [[YOUR JURISDICTION-SPECIFIC SOURCES, e.g., EUR-Lex, ESMA, EBA, national DPA]]
- **Calendar connector:** [[YOUR CALENDAR MCP, e.g., M365, Google Workspace]]
- **Risk register:** [[POINTER TO YOUR INTERNAL RISK LOG]]

## What Comes Out

A single-page brief organized as:

### 1. The headline (one sentence)
What is the most important thing for the user to know today?

### 2. Peer moves (3 bullets)
- [[PEER 1]] did X. Implication for us: Y.
- [[PEER 2]] did X. Implication: Y.
- [[PEER 3]] did X. Implication: Y.

### 3. Regulatory radar (only if material)
Anything in the user's jurisdiction or industry that changed yesterday and has a deadline or action implication.

### 4. Calendar today
- Three most important meetings, who is in them, and one line each on what the user needs to bring
- Any meeting where the user is the decision maker is flagged

### 5. Top three risks
From the risk register, the three items closest to triggering. New developments highlighted.

### 6. Quick wins
One or two things the user could close out before noon today that have been sitting too long.

## Style

- Three minutes to read, max
- Plain language, no jargon unless it is the user's own jargon
- Numbers always sourced
- No filler. If a section is empty today, omit it

## Scheduled Task Configuration

```
Schedule: daily at 07:00 (user's timezone)
Output: deliver to user's preferred channel (email, Teams DM, Slack DM)
Failure mode: if a source is unreachable, deliver what is available and flag the gap
Memory: store the brief for retro review
Privacy: never include personal data of others; never include market-sensitive material before publication
```

## Iteration

After two weeks of daily briefs, prompt the user:
- Which sections do you skip every time? Remove them.
- Which sections do you re-read? Expand them.
- What did you wish was in the brief but was not? Add a source.
