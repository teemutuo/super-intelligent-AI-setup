---
name: sensitivity-templates
description: |
  Fallback patterns for when you cannot paste real data into Claude. Five concrete templates: HTML report, Excel anonymizer, PPTX redaction, Python preprocessor, custom-software bridge. Use when: confidential data, restricted data, board material, market-sensitive, personal data, cannot paste, sensitivity wall.
metadata:
  version: "1.0.0"
  license: "Use freely"
---

# Sensitivity Templates · When You Hit the Wall

You will hit moments where the data you need to work with cannot go into a prompt. Pasting board materials, personal data of third parties, market-sensitive numbers before publication, or anything tagged Restricted is not negotiable. These templates are what you do instead.

## Pattern 1 · HTML Report Shell

When the data is sensitive but the structure is not.

Generate a fully styled HTML report shell with placeholders. The shell contains: the brand-true typography, the chart layouts, the commentary structure, the source attribution. Numbers are placeholders. You fill them in locally, on your machine, with the real data, never pasting them back.

Example prompt:
```
Build me an HTML monthly report shell for [[YOUR DEPARTMENT]]. Sections: KPI grid, commentary on top three movements, risk register snapshot, next-month actions. Use placeholders like {{REVENUE_M}} and {{EBITA_PCT}} for all numbers. Style with [[YOUR BRAND COLORS]]. I will fill in the placeholders locally.
```

Output: a self-contained .html file you save and fill in offline.

## Pattern 2 · Excel Anonymizer Pattern

When you need analysis on real data but cannot share identifiers.

Build an Excel template that: hashes person names to anonymous IDs in one tab, calculates the analysis on the anonymized tab, and produces a chart and commentary based only on the anonymized data. The mapping tab stays local.

Example prompt:
```
Design an .xlsx structure with three sheets: (1) RAW with columns [[YOUR COLUMNS]] including names; (2) ANONYMIZED that uses a hash formula to replace names with IDs; (3) ANALYSIS that computes [[YOUR METRIC]] on the anonymized sheet only. Provide all formulas. I will populate RAW locally and only share ANONYMIZED if needed.
```

## Pattern 3 · PPTX Redaction Template

When you need to draft a board deck but cannot include the actual figures.

Build a PPTX with the narrative, the chart placeholders, and structural commentary. Insert "FIGURE TO INSERT LOCALLY" tags in chart areas. You finish the deck offline.

Example prompt:
```
Draft a board pack deck for the [[QUARTER]] review with these sections: executive summary, financials snapshot, operational KPIs, three strategic decisions, risk update. For each numerical chart, insert a placeholder slide that says FIGURE TO INSERT LOCALLY with the chart type and axes specified. Brand: [[YOUR PALETTE]].
```

## Pattern 4 · Python Preprocessor Script

When you have a large dataset and only want anonymized or aggregated parts to leave your machine.

Ask Claude to write a Python script that runs locally, reads the sensitive CSV or XLSX, strips identifiers, aggregates to the level you need, and writes a sanitized output file. The script never leaves your machine and the sensitive data never enters a prompt.

Example prompt:
```
Write a Python script that reads ./input.xlsx with columns [[YOUR COLUMNS]], drops any column matching a personal-data pattern (name, email, phone, address, ID number), aggregates the remaining columns by [[GROUPING]], and writes ./output.xlsx with only the aggregates. Use pandas. Include logging so I can audit what was stripped.
```

You run this script locally. Only the output file is safe to share.

## Pattern 5 · Custom Software Bridge

When your data lives in a system that has no MCP connector (legacy ERP, custom internal tool, niche compliance database).

Ask Claude to design a thin bridge: a documented export pattern from the source system (CSV, JSON, or REST), a transformation script, and the prompt structure to use on the sanitized output.

Example prompt:
```
My team uses [[CUSTOM SOFTWARE]] which exposes [[REST API / CSV EXPORT / NONE]]. Design a three-step bridge: (1) what to export from the system and how, (2) a script that anonymizes or aggregates the export, (3) the prompt I would use on the cleaned data. The bridge must work even if I cannot install new software, only run scripts locally.
```

## The Meta-Rule

If a piece of data fails any of these tests, do not paste it:
- Could a regulator object?
- Could a third party named in the data object?
- Is the data tagged Restricted, Confidential, or board-only?
- Is this market-sensitive before publication?

For all of those, one of the five patterns above replaces the casual paste. The output is the same. The risk is gone.
