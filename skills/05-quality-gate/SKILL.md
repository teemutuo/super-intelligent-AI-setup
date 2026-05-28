---
name: quality-gate
description: |
  Auto-activating verification policy that runs after any significant output (document, analysis, report, presentation). Verifies factual accuracy, brand compliance, regulatory alignment, completeness, and reasoning quality. Triggers after creating: report, document, analysis, deck, presentation, board pack, memo, deliverable.
metadata:
  version: "1.0.0"
  license: "Use freely"
---

# Quality Gate · Universal QA

After producing any non-trivial output, run this gate before declaring done. If any check fails, fix and re-run.

## The Eight Checks

### 1. Factual accuracy
- Every named person, number, date, and quote: traceable to a source
- Any number not in the source data: explicitly marked as estimate
- Any acronym: spelled out on first use

### 2. Source citation
- Sources listed at the end of any data-bearing output
- Distinguish primary (the actual document) from secondary (commentary on the document)
- Distinguish company numbers (named) from market numbers (cited)

### 3. Brand and voice compliance
- Voice attributes followed (refer to your brand-voice skill)
- Colors and typography from the design system
- No em dashes, no marketing superlatives, no AI-tells like "delve" or "in today's fast-paced world"

### 4. Regulatory alignment
- For EU operations: GDPR (personal data), EU AI Act (any AI use case classified by risk), CSRD (sustainability claims), MAR (anything market-sensitive)
- For US operations: SOX, SEC disclosure, state privacy laws
- For finance specifically: applicable accounting standard cited (IFRS or GAAP)

### 5. Completeness
- The user's question answered, not adjacent question
- Counter-arguments acknowledged
- Caveats and assumptions surfaced

### 6. Reasoning quality
- Logic chain visible, not just conclusions
- Numbers add up (literally check the arithmetic)
- No circular references between sources

### 7. Audience fit
- Plain language for non-experts; technical depth where audience expects it
- Length matches the request (15-minute talk does not need 40 slides)
- Format matches the context (memo, deck, table, conversation)

### 8. Tactical sanity
- Does the user know what to do after reading this?
- Are owners and dates assigned where relevant?
- Is anything missing that the user will get asked about in the next meeting?

## Output

If all eight pass:
```
QUALITY GATE: PASS
Confidence: [HIGH | MEDIUM | LOW]
Notes: [any caveats]
```

If any fail:
```
QUALITY GATE: FAIL on [check number and name]
Issue: [one line]
Fix: [what I'm doing about it]
```

Re-run until pass. Never declare done with an open fail.
