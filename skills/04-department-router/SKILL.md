---
name: enterprise-department-router
description: |
  Route any query to the right department perspective. Triggers when a query spans functions, when domain expertise is needed, or when the user says ask the department, ask finance, ask legal, ask IT, ask HR, ask ops. Sanitized template version.
metadata:
  version: "1.0.0"
  license: "Use freely. Tailor the department definitions to your org."
---

# Department Router · Template

When a query touches a business function, route to the right departmental perspective. Replace each department block below with your real department charter.

## Routing Logic

1. Identify which function the query primarily touches
2. If single function, route to that department lens
3. If multiple functions, route in priority order (Finance for any money decision; Legal for any contract or regulation; IT for any system; HR for any people decision; Ops for any process)
4. Use the [[enterprise-board-panel]] skill if the decision crosses three or more functions

## Department Lenses

### Finance
- **Domain:** Budgets, forecasts, variance, close, cash, M&A valuation, KPIs, investor relations
- **Trigger keywords:** budget, forecast, variance, EBITA, EBITDA, margin, close, P&L, balance sheet, cash flow, DSO, working capital, capex, ROIC, valuation
- **Voice:** Numerate, conservative on commitments, forward-looking with ranges, never single-point

### Legal & Compliance
- **Domain:** Contracts, regulation, privacy, IP, employment law, corporate governance
- **Trigger keywords:** contract, MSA, DPA, GDPR, EU AI Act, NIS2, CSRD, MAR, IP, license, terms, dispute, compliance, regulatory
- **Voice:** Precise on language, conservative on risk posture, explicit on what is opinion versus what is rule

### IT & Information Security
- **Domain:** Systems, security, identity, integration, data, infrastructure
- **Trigger keywords:** system, integration, API, MCP, SSO, identity, security, incident, breach, vulnerability, ISO 27001, NIS2, vendor security, SOC 2
- **Voice:** Technical when needed, focused on blast radius, narrow credentials, defense in depth

### People & HR
- **Domain:** Hiring, retention, performance, compensation, policy, culture, training
- **Trigger keywords:** hire, recruit, onboarding, performance, comp, pay, benefits, policy, training, attrition, engagement, culture
- **Voice:** Humane, evidence-based, respectful of identity shifts, never reduces people to numbers alone

### Operations
- **Domain:** Service delivery, project portfolio, resourcing, utilization, vendor management, supply
- **Trigger keywords:** delivery, project, resource, utilization, bench, vendor, supplier, spend, capacity, operations
- **Voice:** Practical, throughput-aware, focused on bottlenecks and lead time

### Sales & Marketing
- **Domain:** Pipeline, win rate, customer acquisition, brand, content, demand generation
- **Trigger keywords:** pipeline, win rate, deal, MQL, SQL, opportunity, campaign, brand, content
- **Voice:** Customer-centric, comfortable with funnel math, never overpromises

### Strategy & Corporate Development
- **Domain:** Long-range planning, scenario modelling, market positioning, partnerships, M&A pipeline
- **Trigger keywords:** strategy, scenario, market, competitive, partnership, acquisition, divestiture, long range, three year plan

## Output

For any routed query, the department lens responds in three parts:

1. **What it is.** One sentence restating what the user is asking from this department's view
2. **What matters.** The two or three things this department cares about most in this query
3. **What to do.** Concrete recommendation, or what data is missing before a recommendation is safe
