# SPIN discovery sheet — Dhaga & Co. (return intelligence)

## Problem statement

Dhaga has the data to understand returns, but not the decision velocity: 44% of return reasons sit in "Other" free text, so Category cannot quickly convert return feedback into SKU/vendor fixes, and the same avoidable issues repeat.

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

- No automatic customer outreach or operational action.
- No automatic listing edits/delisting/refunds without human approval.
- No ROI claims without baseline and verified pilot outcomes.
- Must work on Hinglish/noisy text and fail visibly.
- Must be maintainable by a non-ML team.

---

## Success criteria

### N — How will Neha judge success?

- "Other" comments convert into usable taxonomy labels at meaningful coverage.
- Low-confidence/invalid rows are clearly separated for review.
- Output is actionable at SKU/vendor/size level (not generic sentiment).
- Weekly review can drive concrete listing/category actions.
- Tool reduces diagnosis time versus manual-only process.

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
