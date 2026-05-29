# FAQ

The questions I keep getting.

## On the "hours saved" claim

**Where did the number come from?**
It is mine, on my role and my workload, drawn from time-tracking comparison weeks before and after the build, over a quarter. Single executive, single sector, not peer-reviewed. Anyone who tells you the number is a benchmark for "all professionals" is selling you something.

**What can I expect for my role?**
What I can say with more confidence than the headline number:

- `morning-brief` saves ten to fifteen minutes you would spend prepping for tomorrow's meetings, roughly five days a week.
- `brand-voice` saves the time of one rewrite cycle per piece of writing, multiplied by however many tricky messages you send.
- The combination of `commentary-engine` and `quality-gate` saves two to four hours per board cycle (which for many of us is monthly).
- A scheduled market-insights agent saves twenty to thirty minutes of newsletter scanning per Monday.

Stack those, and "low double-digit hours per week" is realistic. The exact number for you depends on your week. Run the system for four weeks before forming an opinion about your number.

## On Claude versus other AI

**Which AI should I use?**
Claude (Pro, Max, or Enterprise) is what this is built for. The plugin install on Claude Cowork is the smoothest path because the SKILL.md format auto-triggers on conversational cues. ChatGPT (Custom GPTs), Copilot for Microsoft 365 (agents), or any LLM that supports a system prompt will also work; you just lose auto-trigger.

**Do I need the most expensive tier?**
For regulated industries: yes, enterprise tier. The zero-retention contract is standard at enterprise and not at consumer tier. For personal-use AI without sensitive data: Pro is enough.

## On the install path

**Do I need a developer?**
No. Nothing in this repo requires code. Every skill is a Markdown file you paste into a saved instruction. The connectors are point-and-click OAuth. The "no terminal" path in `install.md` takes three minutes.

**What if I am not technical?**
You do not need to be. The hardest part of the build is the memory bootstrap interview, and the only technology involved is saving a Markdown file. If you can write an email, you can build this.

**Does this work without git?**
Yes. Click Code → Download ZIP on GitHub. Unzip. Drag the folder into your Claude plugins directory. No terminal touched.

## On hallucination and accuracy

**Won't the AI just make things up?**
It can. Three guards built into this design:

1. **Skills first, agents later.** Every skill gets ten or more manual runs before it is automated. You catch the failure modes when you are still in the loop.
2. **Agents are read-only by default.** The morning brief, the market digest, the regulatory radar all surface and link. They do not reply, schedule, or commit anything on your behalf.
3. **Verify before forwarding.** If you are about to share something an agent surfaced, click through to the source first.

**Where does the quality-gate skill fit in?**
It is the eight-check filter you run on any output before declaring it done. Factual accuracy, source citation, brand voice, regulatory alignment, completeness, reasoning quality, audience fit, tactical sanity. Built to catch the obvious flaw the AI introduced, before you send.

## On governance and compliance

**EU AI Act, short version?**
The Act regulates AI **systems** by risk classification. Personal-use AI for a single professional's productivity is, in most readings as of May 2026, low risk. But:

- If you use the AI to make or materially influence decisions about employees (hiring, performance, dismissal): that is high-risk territory under the Act. The board-panel skill is fine; do not build a "performance analyzer" skill that scores team members.
- If your company has obligations as an AI deployer under the Act, this setup needs to be on the firm's AI register. Talk to your compliance officer.

This is general guidance, not legal advice. The full governance memo, including the five-question CISO email, is in [`governance.md`](./governance.md).

## On what to never share

**Your filled-in memory bootstrap and your `my-profile.md` are the most sensitive artefacts in this kit.** They contain pending decisions, named stakeholders, your operating environment. The `.gitignore` in the repo already blocks these from being committed by accident. Never paste them into a public Slack channel, email thread, or LinkedIn comment.

**Filled-in setup-interview answers**, same rule.

**Skills and templates are shareable.** Your filled-in versions are not.

## On the framework

**Where did the Superintelligence Ladder come from?**
Originally I was teaching colleagues a four-rung model. The six-rung version is what landed after roughly fifteen iterations of teaching it. The names (Asking, Drafting, Personalized, Equipped, Operating, Autonomous) are pinned because each one names what you can and cannot do at that level. The taxonomy has held up across about a year of real use.

**Why does the README make a fuss about Level 3?**
Because Level 3 is where value starts compounding rather than just adding. Below Level 3 every output is independent: a good prompt produces a good answer. From Level 3 onwards memory carries between conversations, the AI learns your voice, and outputs start improving each other. That is the inflection point and the reason most people who hit Level 2 plateau there.

## On the five power-words

**Are ultrathink, maxeffort, ultraplan, run the panel, critique yourself just placebo?**
Mostly not. They map to real LLM behaviour: longer reasoning, more thorough drafting, multi-step planning, multi-perspective generation, self-critique. The phrasing nudges the model into modes it can otherwise underuse. They are not magic; they will not turn a bad question into a good answer. But on board-grade writing, the 30 to 50 percent quality lift is consistent enough that I treat them as switches.

## On contributing

**Can I PR a new skill?**
Yes. The `SKILL.md` format is at the top of each existing skill: YAML frontmatter with `name` and `description`, then the prompt body. Keep the brand voice (no em dashes, no marketing superlatives, no AI tells). Open a PR with a one-sentence rationale.

**Can I sell what I build on top of this?**
The kit is MIT licensed. Use it, sell what you build with it, change what you keep. If you sharpen a skill, a PR back to this repo is appreciated but not required.
