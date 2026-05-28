---
name: prompt-power-words
description: |
  Five short phrases you can add to any prompt when quality matters more than speed. Tells Claude to slow down, think harder, work in passes, or invoke multiple perspectives. Use when: high-stakes deliverable, board-grade output, decision that matters, anything you would normally re-read three times before sending.
metadata:
  version: "1.0.0"
  license: "Use freely"
---

# Prompt Power-Words

The default speed of an AI chat is fast. Fast is great for "what is the capital of France." Fast is wrong for "draft the management commentary for the board." These five power-words are switches you flip when quality matters more than speed. Each one is a request for a different kind of effort.

Add the word at the start of the prompt. That is the whole pattern.

---

## 1. ultrathink

**What it does:** Asks Claude to reason longer and more carefully before answering. The output is slower to arrive and noticeably more considered.

**Real-life example:**
> Ultrathink this vendor contract for risks before drafting my response.

**When to use:** Hard analytical questions. Risk assessment. Decisions with downside. Anything where the second-order effects matter more than the first answer.

**When not to use:** Simple lookups, quick drafts, anything where speed is the point.

---

## 2. maxeffort

**What it does:** Tells Claude to commit to the best possible output, not the fast one. Treat the task like it is the most important thing on its desk.

**Real-life example:**
> Maxeffort the Q2 board commentary. This is the version the audit committee will read.

**When to use:** Board-grade deliverables. External-facing writing. Investor communications. Any output where you would re-read your own work three times before sending it.

**When not to use:** Internal drafts that will be revised anyway. The compounding cost of maxeffort on every prompt is wasted attention.

---

## 3. ultraplan

**What it does:** Asks Claude to map the whole thing before doing any of it. Surfaces dependencies, decision points, and gaps before any work starts.

**Real-life example:**
> Ultraplan the month-end close before drafting the day-by-day task list.

**When to use:** Multi-step projects. Anything that spans more than a single deliverable. Onboarding plans. Migration plans. Anything you would normally sketch on a whiteboard first.

**When not to use:** Atomic tasks (one prompt, one output). Ultraplan on a single email is overengineering.

---

## 4. run the panel

**What it does:** Convenes multiple expert perspectives instead of giving you one answer. Surfaces dissent. Forces trade-offs into the open.

**Real-life example:**
> Run the panel on whether to extend probation for [name], then recommend.

**When to use:** Decisions where reasonable people disagree. Decisions with multiple stakeholders. Decisions you do not want to make alone. Pre-mortems.

**When not to use:** Information lookups. Tasks where one expert lens is enough. Trivial choices.

---

## 5. critique yourself

**What it does:** Forces Claude to review its own draft from a specific point of view before declaring done. The most reliable way to catch the obvious flaw before you send.

**Real-life example:**
> After drafting this memo, critique yourself from the perspective of HR Legal. Fix what you find.

**When to use:** After any first draft of an important document. Before sending. Whenever the audience is more sophisticated than the average reader.

**When not to use:** Tight time windows where the critique loop would slow you down more than the catch is worth.

---

## How they combine

You can chain them. The order matters slightly.

```
Ultrathink and ultraplan the close calendar.
Maxeffort the day-by-day task list.
Run the panel on the bottlenecks.
Critique yourself from the controller perspective before delivering.
```

The above takes a single prompt from "write me a close plan" to "give me a board-grade close plan that has been reviewed by four lenses and stress-tested for risk." Worth the extra fifteen seconds of waiting.

---

## What they are not

- They are not magic. They will not turn a bad question into a good answer.
- They are not free. Maxeffort on every prompt wastes attention and tokens. Reserve for the deliverables that matter.
- They are not a substitute for memory. The bootstrap prompt and the loops do more for output quality than any power-word.
- They are not industry standard. These are conventions that work today. Use them, and tell me when they stop working.

---

## Anti-patterns

- **Stacking all five on a one-line question.** "ultrathink ultraplan maxeffort run the panel critique yourself: what time is it" produces nothing useful. Match the depth to the task.
- **Using ultraplan on atomic tasks.** "Ultraplan a single email" makes Claude generate steps for something that should just be done.
- **Skipping memory.** Power-words on a Claude that does not know who you are gives you slower bad output instead of fast bad output. Set up memory first.
