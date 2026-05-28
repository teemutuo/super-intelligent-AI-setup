---
name: commentary-engine
description: |
  Draft narrative commentary on numerical data for any audience: management commentary on financials, executive summary on KPIs, briefing notes on operational metrics. Triggers on: write commentary, executive summary, board narrative, management report, variance commentary, KPI explanation.
metadata:
  version: "1.0.0"
  license: "Use freely"
---

# Commentary Engine · Universal Pattern

When asked to write commentary on numbers, follow this exact structure. Replace placeholders with the specific case.

## The Five-Move Structure

1. **The headline (one sentence).** What is the single most important thing the reader should walk away with?
2. **The story (two to three sentences).** What is the trend, in plain language? What changed? What does it mean?
3. **The drivers (three bullets).** What caused the change? Order by magnitude, not by alphabet.
4. **The risk or opportunity (one or two sentences).** What is the implication going forward? Where is the asymmetry?
5. **The action (one sentence).** What is the recommendation, or what decision is needed?

## Style Rules

- **Lead with the insight, not the data.** "Revenue declined six percent" beats "Revenue was twenty-six point seven million euros versus twenty-eight point two million."
- **Use ranges, not single points, for forward-looking statements.** "EBITA likely between three point seven and six point nine million."
- **Attribute every variance to a driver.** Never leave a number unexplained.
- **Quantify the risk.** "Bench rising fifty basis points per month" beats "bench rising."
- **End on what the reader should do.** Commentary that does not lead to a decision is a status update, not commentary.

## Voice Calibration

The commentary inherits the brand voice from the [[brand-voice]] skill if available. If not, default to:

- Confident, not arrogant
- Quantitative, not breathless
- Forward-looking, not backward-narrating
- Honest about what is not known

## Anti-Patterns

- "The team continued to focus on..." (vague filler)
- "Strong momentum across the business" (no information)
- "We remain optimistic about our outlook" (no quantification)
- "Delve into the dynamics" (AI-tell)
- Single-point forecasts with no range
- Variances without owners or causes

## Example Output (Financial)

```
Q1 revenue landed at twenty-six point seven million, a six percent decline year on year, driven by softness in the engineering segment.

The miss was concentrated in two large accounts where roll-offs were not replaced fast enough. AI delivery grew eighteen percent and absorbed roughly half the gap. Cost actions taken in March will show in Q2.

Drivers:
- Engineering revenue down four point one million on slower replacement
- AI services up nine hundred thousand, exceeding plan
- One-time legal settlement of two hundred thousand, non-recurring

Risk: if engineering does not stabilize by Q3, full-year guidance moves to the lower half of the range.

Recommendation: hold Q2 reinvestment in AI delivery, accelerate engineering pipeline conversion by mid-May, revisit guidance at half-year.
```

Adapt for non-financial commentary by replacing the financial nouns with operational, HR, or program metrics.
