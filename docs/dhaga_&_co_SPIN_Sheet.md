# SPIN discovery sheet — Dhaga & Co. (return intelligence)

## Problem statement

Dhaga has the data to understand returns, but not the decision velocity: 44% of return reasons sit in "Other" free text, so Category cannot quickly convert return feedback into SKU/vendor fixes and timely customer-response actions, and the same avoidable issues repeat.

---

## Decision makers

### S — Who needs to decide or act?

- **Primary decision owner:** Neha, Category Head
- **Execution owner:** Vivek, Listing Lead (size chart/copy/image updates)
- **Business sponsor:** Ritu, CEO (retention and CAC pressure)
- **Technical viability owner:** Dev, CTO (operable without ML specialist)

Neha must be able to trust a weekly issue queue by SKU/size/vendor, not just a dashboard.

---

## Decision pressures (Dhaga-specific)

### P + I — What pressure is shaping their choices?

### 1) Merchandising velocity vs catalogue truth
- New drops are frequent, but return reasons are diagnosed slowly.
- By the time manual review surfaces patterns, correction windows are missed.

### 2) Cost pressure under COD-heavy economics
- Return and RTO economics punish delayed correction.
- Teams need earlier intervention on repeat issue SKUs.

### 3) Signal fragmentation across teams
- Category, listing, CX, and supply each see part of the issue.
- No shared, structured language for return causes from free text.

### 4) Operability reality
- Tool must run with current team capacity.
- Any workflow that adds review overhead without clarity will be rejected.

---

## Boundaries and constraints

### J — What is off-limits in v1?

- No automatic listing edits/delisting/refunds without human approval.
- No ROI claims without baseline and verified pilot outcomes.
- Must work on Hinglish/noisy text and fail visibly.
- Must be maintainable by a non-ML team.
- Policy must be explicit for outreach timing and fallback (WhatsApp <=15s, call at 4h no-response, RTO auto-accept if still no response).

---

## Success criteria

### N — How will Neha judge success?

- "Other" comments convert into usable taxonomy labels at meaningful coverage.
- Low-confidence/invalid rows are clearly separated for review.
- Output is actionable at SKU/vendor/size level (not generic sentiment).
- Weekly review can drive concrete listing/category actions.
- Tool reduces diagnosis time versus manual-only process.
- Eligible cases move through response funnel predictably: WhatsApp in <=15s, call after 4h no-response, then RTO auto-accept if unresolved.

---

## Time urgency

### S — Why now?

- Returns are already high and repeat purchase is flat.
- Every delayed correction cycle means repeat avoidable returns.
- Pilot should start in one category with a short validation loop (2 weeks).

---

## Confidence and trust protocol

### I — How confidence should be interpreted

- Threshold is a routing control, not an accuracy claim.
- High-confidence rows are proposed for review; they are not auto-executed actions.
- Low-confidence rows stay human-decided.
- Any invalid output must be visible and excluded from automatic counting.

---

## SPIN question funnel for Dhaga discovery call

## Situation questions (S)

1. Walk me through the current flow from return comment to actual SKU/vendor fix.
2. How many "Other" comments are reviewed in a normal week, and by whom?
3. Where do return text, SKU metadata, and vendor/size-chart details currently live?
4. What cadence do you run for category corrections today (daily/weekly)?
5. Which team currently sends exchange-confirmation messages, and what is the average response delay?

## Problem questions (P)

1. Where does the current process break: interpretation, prioritization, or execution?
2. Which decisions are being delayed because the reason is unstructured?
3. What kinds of repeat issues are hardest to detect early?
4. What makes manual review inconsistent across reviewers?
5. Where do customer responses get stuck today: message delivery, reply tracking, or follow-up calls?

## Implication questions (I)

1. If "Other" stays unstructured, what happens to recurring issue SKUs over the next 4-6 weeks?
2. What does delayed correction cost in terms of repeat returns and rework time?
3. How does this delay affect retention pressure and acquisition efficiency?
4. What happens when teams disagree on cause because reasons are not standardized?
5. What is the operational impact when no-response cases sit unresolved for hours?

## Need-payoff questions (N)

1. If Neha received a trusted weekly queue by SKU/vendor/size, what decisions would accelerate immediately?
2. If low-confidence rows were isolated automatically, how would reviewer quality improve?
3. What pilot evidence would make you confident enough to scale beyond one category?
4. If confirmations go out in <=15 seconds with 4-hour call fallback and clear RTO closure, what manual effort reduces first?

---

## Expected SPIN arc (Dhaga)

- **S:** Understand return-to-fix workflow and data fragmentation across Category/Listing/CX.
- **P:** Identify decision latency caused by unstructured "Other" text.
- **I:** Link latency to recurring avoidable returns and business pressure.
- **N:** Align on human-in-loop classification plus policy-based response automation as the lowest-risk first move.

---

## Problem definition summary

- **Core problem:** Decision latency from unstructured return reasons.
- **Owner:** Neha (Category).
- **MVP intervention:** Classify -> confidence route -> human review -> SKU/vendor action suggestions.
- **Response policy:** For approved eligible cases -> WhatsApp confirmation <=15s -> call after 4h no response -> auto-accept RTO if still no response.
- **Pilot objective:** Prove actionability and operational trust before financial impact claims.

## Assumptions made

- A meaningful share of "Other" comments contains repeatable, actionable return reasons.
- Category/Listing teams can operationalize weekly issue queues without additional specialist staffing.
- Customers are reachable quickly enough for WhatsApp-first confirmation to be useful.
- A 4-hour no-response call fallback is operationally feasible.
- Auto-accept RTO on no-response is policy-acceptable for pilot scope.
