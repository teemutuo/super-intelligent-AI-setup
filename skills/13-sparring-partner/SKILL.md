---
name: sparring-partner
description: |
  Year-long professional development companion. You set a theme each quarter; the skill runs weekly sparring sessions on sub-elements of that theme. Designed to enhance professional thinking, decision quality, and judgment under pressure. Use when: setting a quarterly development theme, running a weekly sparring session, asking for a stretch-thinking exercise, requesting a coaching prompt, doing a retrospective on a recent decision. Triggers on: "sparring session", "sparring partner", "stretch my thinking", "coach me on [topic]", "sharpen my [skill]", "professional development", "quarterly theme".
metadata:
  version: "1.0.0"
  license: "Use freely"
---

# Sparring Partner, year-long professional development

This skill turns the AI into a year-long sparring partner for your professional thinking. You set a quarterly theme; the skill runs weekly sessions on sub-elements of that theme. Each session is short, specific, and designed to sharpen one element under safe conditions before you need it under real ones.

This is not a decision-rehearsal skill (use `03-board-panel` for that). This is a development skill, slow compound work over twelve months.

## The shape of a year

| Element | Quantity | When |
|---------|----------|------|
| Quarterly theme | 4 per year | One per quarter, drafted at quarter start |
| Sub-elements per theme | 8 to 12 | Defined when the theme is drafted |
| Weekly sessions | 50 to 52 per year | One per week, Friday afternoon by default |
| Quarterly review | 4 per year | Last week of each quarter |

By the end of a year you have completed ~50 sparring sessions across 4 themes. That is more deliberate professional development than most professionals do in five years.

## Setting a quarterly theme

Use `templates/quarterly-theme.template.md`. A good theme has:

- One core skill, domain, or capability you want to sharpen this quarter.
- Eight to twelve sub-elements within that domain. Specific situations or sub-skills.
- A success criterion that says what good looks like at quarter end.
- A constraint that says what this theme will not become.

Example themes:
- Sharpen scenario thinking under macroeconomic uncertainty.
- Lead through difficult conversations without losing the relationship.
- Read board signal versus board noise.
- Negotiate cross-functional priorities under resource constraints.
- Build executive presence in ambiguity.
- Tighten financial commentary on variance.

## A weekly session

Every Friday (or your chosen weekly slot), trigger the skill:

> Run my sparring session for this week. My theme this quarter is in `current-theme.md`. Pick one sub-element I have not covered in the last three weeks.

The skill rotates through six session formats so the week never feels repetitive. The format is chosen automatically based on what you have done recently.

### Format 1, Case study (10 minutes)
Claude generates a context-specific scenario based on your Profile and your current theme. It asks how you would handle it. You answer in writing or out loud. Claude critiques the answer, surfaces the moves you did not consider, names the assumption you treated as a fact.

### Format 2, Pre-mortem (8 minutes)
Claude picks a real upcoming decision (from your calendar, memory, or pending decisions). You imagine the failure mode twelve months out and work backward to identify why. Claude pressure-tests your read using the Tigers, Paper Tigers, Elephants taxonomy.

### Format 3, Dialogue rehearsal (12 minutes)
Claude plays a counterparty (board member, peer, regulator, customer) and runs a difficult dialogue under your current theme. You respond. Claude flags moves you would not want recorded.

### Format 4, Retrospective (5 minutes)
Claude picks a recent decision from your memory and asks: what second-order effects did you see, what did you miss, what would you now see differently. The shortest format, the highest compounding.

### Format 5, Reading recommendation (5 minutes + reading)
Claude proposes one short reading tied to a sub-element. Article, paper, case. You read offline, return next week to discuss.

### Format 6, Skill drill (10 minutes)
A specific micro-skill exercise. Example: "Write three openings for a board update that acknowledge bad news without panic. Critique each in your own voice."

## Output

Every session produces:
- A short transcript or notes, saved to a quarterly journal file.
- One sharper articulation than you started with.
- An action for the next week, if relevant.

Over the quarter, ~12 session artifacts accumulate. These become the input for the quarterly review.

## Quarterly review

At the end of each quarter, trigger:

> Run the quarterly sparring review. My theme this quarter was X. Show me what I covered, what shifted, what I still avoid, and propose next quarter's theme.

Claude reads the session artifacts, summarises the quarter, surfaces patterns, and proposes the next theme. You decide.

## How to schedule (Claude Cowork)

```yaml
name: Sparring Partner, weekly session
schedule:
  cron: "0 16 * * 5"
  timezone: [your IANA timezone]
prompt: |
  Run my sparring session for this week. My current quarter's theme
  is in current-theme.md. Pick one sub-element I have not covered in
  the last three weeks. Rotate through the six session formats based
  on what we have done recently. Save the session to journal/Q[N]-week-[NN].md.
delivery:
  channel: slack
  recipient: dm-to-self
```

## How to schedule (other platforms)

- ChatGPT Tasks: same prompt, weekly cadence.
- n8n / Make / Zapier: cron-triggered LLM call.
- Manual: a Friday-afternoon ritual.

## When NOT to use this skill

- For decision-rehearsal of a specific upcoming decision, use `03-board-panel`.
- For tactical advice on one situation, use the relevant lens from `04-department-router`.
- For execution support on a project, use `06-commentary-engine` or `05-quality-gate`.
- This skill is for development. Not for delivery.

## The argument for doing this

Most professionals plateau because their working week absorbs all their thinking time. Deliberate practice is the differentiator that separates competent operators from senior judgment. This skill is the deliberate practice, in the cracks of a working week, for the price of a Friday afternoon hour.

The compounding only works if you do not skip the difficult weeks.
