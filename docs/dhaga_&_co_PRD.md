# PRD — Dhaga & Co. Return Intelligence (MVP v1)

## Document control

- **Product:** Return Intelligence + Response Automation Queue
- **Version:** v1.0
- **Date:** 2026-10-03
- **Owner:** Category (Neha) with Listing Ops support
- **Status:** Ready for MVP build/pilot

---

## 1) Problem statement

Dhaga collects return feedback, but cannot operationalize it quickly: a large share of reasons remains in unstructured "Other" text, so Category cannot consistently identify which SKUs, sizes, and vendors need corrective action.

---

## 2) Objective

Build a lightweight internal workflow that converts free-text return reasons into actionable categories and runs a policy-based response flow: WhatsApp confirmation in <=15 seconds, call fallback after 4 hours, and automatic RTO acceptance if no response.

---



## 3) Goals and non-goals



## Goals

- Convert "Other" comments into validated taxonomy labels.
- Route uncertain rows to human review.
- Surface SKU/vendor/size clusters with recommended next actions.
- Reduce diagnosis time versus manual-only review.
- Trigger customer confirmation quickly and consistently for eligible exchange cases.



## Non-goals (v1)

- No automatic listing edits or refund decisions.
- No production ROI claims from prototype-only outputs.
- No full-scale platform integrations required for v1.

---



## 4) Users and stakeholders

- **Primary user:** Neha (Category Head)
- **Secondary users:** Listing team reviewers, Category Ops
- **Stakeholders:** Ritu (CEO), Dev (CTO), Growth/CX/Supply heads

---



## 5) User stories

- As a category lead, I want free-text return reasons grouped by actionable issue type so I can prioritize corrections.
- As a listing reviewer, I want low-confidence rows isolated so I can validate only uncertain cases.
- As a business sponsor, I want clear weekly outputs by SKU/vendor so corrective actions can be tracked.

---



## 6) Scope



## In scope

- CSV ingestion of return records containing "Other" comments
- Text classification to fixed taxonomy
- Confidence-based routing (auto-file vs review queue)
- Human review actions: approve/edit/dismiss
- Autonomous response triggers for approved/eligible cases:
  - WhatsApp confirmation message within <=15 seconds
  - Calling agent trigger after 4 hours of no response
  - Auto-accept RTO if no response after call window
- Dashboard views: issue distribution, SKU/vendor clusters, review queue



## Out of scope

- Real-time omnichannel orchestration
- Automated policy execution
- Financial impact attribution without baseline validation

---



## 7) Functional requirements

1. **Ingestion**
  - Accept CSV with required columns.
  - Validate schema and enforce safe limits (row cap, text length cap).
  - Reject malformed files with visible errors.
2. **Classification**
  - Map each comment to fixed taxonomy label(s) with confidence and evidence span.
  - Enforce structured output validation before persistence.
3. **Routing**
  - Confidence >= threshold -> propose as review-ready.
  - Confidence < threshold or invalid output -> send to human review queue.
4. **Review queue**
  - Allow reviewer to approve, edit label, or dismiss.
  - Persist final reviewer decision and use it for dashboards.
5. **Autonomous response orchestration**
  - After an eligible decision, trigger WhatsApp confirmation within <=15 seconds.
  - If no customer response for 4 hours, trigger calling agent workflow.
  - If there is still no response after call attempt window, mark return as auto-accepted RTO.
  - Persist timestamps and status transitions for audit.
6. **Insights**
  - Show top issue themes and top impacted SKU/vendor/size clusters.
  - Provide recommended next action text by issue type.
7. **Failure visibility**
  - Show explicit state when model output is invalid/uncertain.
  - Never silently infer labels after validation failure.

---



## 8) Non-functional requirements

- **Operability:** Must run by existing team (no ML engineer dependency).
- **Safety:** Human approval required for eligibility decision before autonomous response flow starts.
- **Performance:** Complete one batch run within practical review cadence.
- **Reliability:** Validation and fallback paths must be deterministic and visible.
- **Security:** No hardcoded secrets; use environment variables for keys.
- **Response SLA:** WhatsApp confirmation must be sent within <=15 seconds of trigger.

---



## 9) Data requirements

- **Required input fields:** `return_id`, `sku`, `category`, `vendor`, `size`, `return_reason`, `other_text`
- **Data quality controls:** missing-field rejection, text normalization, duplicate handling, size limits
- **Output fields:** predicted label, confidence, evidence span, review status, final label
- **Response fields:** `whatsapp_triggered_at`, `call_triggered_at`, `rto_auto_accepted_at`, `response_status`

---



## 10) Taxonomy (initial v1)

- Fit too small / large / tight / loose
- Size chart mismatch
- Colour image mismatch
- Quality: fabric / stitching-damage
- Description/look mismatch
- Not enough evidence
- Not a product issue

---



## 11) Success metrics



## MVP proof metrics

- % of "Other" comments converted into validated labels
- % of rows routed to human review
- Median time from upload to review-ready output
- Reviewer acceptance/edit rate
- % eligible cases receiving WhatsApp confirmation within <=15 seconds
- % no-response cases escalated to call at 4-hour mark
- % unresolved cases auto-accepted as RTO per policy



## Pilot metrics (post-MVP)

- Time to identify top recurring issue SKUs
- Speed of correction cycle (diagnosis to listing/category action)
- Verified outcome improvements against baseline (not claimed in MVP)

---



## 12) Risks and mitigations

- **Risk:** Ambiguous Hinglish text reduces confidence  
**Mitigation:** Confidence routing + review queue + explicit uncertain state
- **Risk:** Reviewer overload  
**Mitigation:** Threshold tuning and queue monitoring
- **Risk:** False outreach trigger on wrong eligibility  
**Mitigation:** Require reviewer-approved eligibility before automation starts
- **Risk:** Over-claiming prototype impact  
**Mitigation:** Separate prototype outputs from pilot-verified outcomes
- **Risk:** Operational adoption  
**Mitigation:** Keep output directly tied to weekly category/listing workflows

---



## 13) Rollout plan

1. **Week 1:** Validate ingestion, taxonomy quality, and review workflow in one category
2. **Week 2:** Run repeated cycles, measure queue quality and actionability
3. **Decision gate:** Scale only with signed baseline, owner alignment, and acceptable reviewer load

---



## 14) Acceptance criteria

- Upload run produces structured, validated outputs with visible status for every row.
- Review queue supports approve/edit/dismiss with persistent final label.
- Eligible decisions trigger WhatsApp in <=15 seconds, call fallback after 4 hours, and RTO auto-accept on no response.
- Dashboard shows actionable SKU/vendor clusters based on final reviewed labels.
- Failure and uncertainty states are explicit and user-readable.
- MVP can be run and operated without a specialist ML role.
