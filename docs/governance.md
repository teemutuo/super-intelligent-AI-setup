# Governance

Read this before you connect anything or enable any agent.

This is a personal-productivity pattern, not an enterprise deployment. If you are an officer of a listed company, or work in any regulated industry, the next two pages decide whether this is safe for you to use as described.

## The short version

Enterprise tier, signed DPA, read-only connectors, no market-sensitive material through consumer-grade OAuth, no decisions about people inside the AI. If any of those terms are unfamiliar, route to your CISO before installing.

## Tier matters

| Tier | Default data treatment | What is safe to load |
|------|------------------------|----------------------|
| Consumer (Claude Pro, ChatGPT Plus) | Data may be used for model improvement unless opted out | Public information only. Never confidential, market-sensitive, or personal data of others. |
| Enterprise (Claude Enterprise, ChatGPT Enterprise, Copilot for Microsoft 365) | Zero-retention default, DPA available, BAA where relevant | Most internal business data. Confirm scope with your CISO. |
| On-prem or VPC | Data never leaves your perimeter | Anything your existing IT controls already permit. |

For executive use in regulated industries: enterprise tier or above.

## The MNPI line

If your role exposes you to material non-public information, earnings before publication, planned M&A, personnel decisions, regulatory inspections, you do not load these into any AI before publication, even at enterprise tier, without explicit policy clearance from your General Counsel.

The `sensitivity-templates` skill (file 10) is the answer for these cases. Five concrete patterns for working with sensitive data without pasting it.

## Connector scope hygiene

When you grant the AI access to Microsoft 365 or Google Workspace:

- Read-only by default. Do not grant "send mail on my behalf" until you have to. You almost never have to.
- Exclude HR, M&A, legal-privileged, and audit-committee folders explicitly. Most providers let you scope.
- Calendar: if your event titles contain MNPI ("Earnings prep, Q3, do not share"), either rename those events or exclude that calendar from the connector scope.

## The bootstrap is sensitive

Your filled-in `08-memory-bootstrap.txt` contains pending decisions, named stakeholders, your operating environment. Treat it like your performance review notes:

- Store in project knowledge at enterprise tier, never in a consumer-tier chat.
- Never share with team members. Skills are shareable, your filled-in memory is not.
- Delete on offboarding from your role.

## Agents stay read-only

The three default agent patterns in this repo, morning-brief plus the two you will design via the setup interview, are all read-only. They surface and link. They never send mail, schedule, accept invitations, or commit anything on your behalf.

This is deliberate. The moment an agent can act on your behalf is the moment it can act wrong on your behalf, on your record. Keep all agents read-only until your firm has a documented AI policy that covers write actions by autonomous agents. That is a different conversation, with your CISO, your General Counsel, and your records-retention lead.

## EU AI Act, short

Personal-use AI for one person's productivity is, in most readings of the Act as of May 2026, low risk. But:

- If you use the AI to influence decisions about employees (hiring, performance, dismissal): high-risk territory under the Act. The board-panel skill is fine, do not deploy a "performance analyzer" skill that scores team members.
- If your company has obligations as an AI deployer under the Act: this setup needs to be on your firm's AI register. Talk to your compliance officer.

General guidance, not legal advice.

## The decision flow

Before you turn on the next thing, five questions:

1. Is the data I am about to expose public, internal, confidential, or restricted?
2. Is my AI provider tier matched to that data class?
3. Have I scoped the connector to exclude one class above what I should be exposing?
4. Is the agent I am about to enable read-only?
5. If a regulator asked me to explain this in writing tomorrow, could I?

Five yeses, proceed. Any no, pause.

## The email to send your CISO

Subject: Personal AI setup. Five questions before I connect anything.

> I am setting up a personal AI productivity stack. Before I OAuth my calendar or email, can you confirm:
>
> 1. Which AI tier is approved for executive use against company data?
> 2. Are there folders, calendars, or mailboxes I should exclude from the connector?
> 3. What is our policy on running AI tools against board materials or MNPI?
> 4. Do we have an existing DPA with the AI provider, or do I need to route through procurement?
> 5. What is logged, and where, when I do this?

Five questions. Five-minute reply expected.

That email is the single highest-leverage paragraph in this repo for an executive in a regulated environment.
