---
name: enterprise-board-panel
description: |
  Convene a board-style panel of named expert perspectives to deliberate any non-trivial decision. Use when: strategic decision, board prep, decision rehearsal, ask the board, pre-mortem, stakeholder review, multi-perspective critique.
metadata:
  version: "1.0.0"
  license: "Use freely. Replace personas with your own advisors or board members."
---

# Board Panel · Template

When the user asks for "board perspective", "decision rehearsal", "ask the board", "stress-test this", or describes a non-trivial decision, do not give a single answer. Convene the panel.

## Panel Composition

Replace these placeholders with the four to six personas most relevant to your domain. For an admin team in a mid-sized company, useful archetypes are:

- **[[PERSONA 1 · Capital and Investor Lens]]**
  Frames decisions in terms of return on capital, valuation, dilution, and shareholder narrative. Asks: what does this do to ROIC and the cash conversion cycle?

- **[[PERSONA 2 · Design and Customer Lens]]**
  Frames decisions in terms of user experience, customer outcome, and brand integrity. Asks: would a customer feel this? In what way?

- **[[PERSONA 3 · Controls and Audit Lens]]**
  Frames decisions in terms of internal controls, audit risk, and reporting quality. Asks: what does the audit committee see, and is the trail clean?

- **[[PERSONA 4 · Operations and Scalability Lens]]**
  Frames decisions in terms of operational drag, headcount implications, and scalability. Asks: what breaks when this triples in volume?

- **[[PERSONA 5 · Risk and Compliance Lens]]**
  Frames decisions in terms of regulatory exposure, legal liability, and reputation. Asks: what is the worst-case headline and the worst-case lawsuit?

You can keep names abstract (Capital Lens, Design Lens) or use real advisors from your network with their permission. Real names increase psychological realism.

## Deliberation Protocol

For each panel session, follow this order:

1. **Restate the decision in one sentence.** "We are deciding whether to ..."
2. **Each persona speaks in turn, 60 to 100 words.** Their concerns, not their conclusion.
3. **Surface the disagreements explicitly.** Where do they conflict? What trade-off is hidden?
4. **Synthesize.** Three options the panel could live with, with one trade-off line each.
5. **Recommend.** Which option, and which dissents must be addressed in delivery.

## Output Format

```
Decision: [one-sentence restatement]

Panel reactions:
- [Persona 1]: [their take, 60-100 words]
- [Persona 2]: [their take]
- [Persona 3]: [their take]
- [Persona 4]: [their take]
- [Persona 5]: [their take]

Disagreements that matter: [bullet list]

Three options the panel can live with:
1. [option] · trade-off: [one line]
2. [option] · trade-off: [one line]
3. [option] · trade-off: [one line]

Recommendation: [option] because [one line]. Dissent to address: [from persona X, what to do about it]
```

## When NOT to Use This Skill

- Trivial decisions or pure information lookups
- Tasks where a single expert lens is enough
- When the user wants speed and the panel adds friction without value
