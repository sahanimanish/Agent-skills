# Agent Query Protocol (Partial Source Set Edition)

This file defines how the agent responds to every query type during PR/CR, with explicit
handling for the confidence limitations introduced by missing sources.

---

## Before Any Query: Confirm Phase 1 Is Complete

The Reconciled Client Record must exist before the agent answers any Phase 2 query.
If Phase 1 has not been completed, the agent must say so and complete it first.

The agent must also confirm that the Triage Report was produced and that any reviewer
decision to proceed despite missing critical sources has been recorded.

---

## How to Answer When Sources Are Missing

For every Phase 2 query, the agent applies this disclosure rule:

If all sources relevant to the query are available and the answer is drawn from verified
data: answer directly with source citations.

If the answer is drawn from data with reduced confidence (primary source absent but
secondary source available): answer and disclose. State what the answer is based on and
that the primary source was not available to confirm it.

If the answer is drawn from data with limited confidence (Tier 3 only, no independent
source): answer and disclose prominently. State that the answer is based on client-provided
unverified information only and that the reviewer must treat it with appropriate caution.

If the relevant dimension is not assessed (no source of any kind available): do not
answer from assumption. State that this dimension could not be assessed because no relevant
source was available, and state what is needed to assess it.

This disclosure rule applies to every query type without exception.

---

## Query Type 1 -- Policy Question About a Specific Client

Step 1 -- Resolve client dimensions from the Reconciled Client Record. Note the confidence
level of each dimension used. If client type is unconfirmed due to missing sources, state
this before proceeding.

Step 2 -- Check prohibited jurisdictions. If jurisdiction is unverified (no independent
source confirmed it), state that the jurisdiction assessment is based on client-stated
information only and apply the most conservative risk tier for that jurisdiction pending
verification.

Step 3 -- Retrieve applicable rule atoms from the KYC Policy KnowledgePack.

Step 4 -- Apply PEP overlay if LexisNexis identified PEP status. If LexisNexis was not
available, state that PEP status could not be independently determined and that the
client's self-declaration (if provided) is the only available evidence.

Step 5 -- Answer from rule atoms. Cite rule_id and effective date for each requirement.

Step 6 -- Disclose all confidence limitations relevant to this answer. If the answer
depends on an unverified jurisdiction, unverified ownership structure, or unscreened
individual, say so explicitly.

---

## Query Type 2 -- Gap Flagging

Step 1 -- Resolve client dimensions.
Step 2 -- Check prohibited jurisdictions.
Step 3 -- Retrieve applicable rule atoms.
Step 4 -- Apply PEP overlay.

Step 5 -- Compare each rule atom against the Reconciled Client Record.

For document-requirement atoms: check the documents array. Record collection gaps
(not held), expiry gaps (held but expired), and verification gaps (held but unverified
because the independent source was not available).

For screening-requirement atoms: check the screening object. If LexisNexis was not
available, record a source gap for every screening-requirement atom. Do not skip these
atoms because the source is absent -- the gap exists precisely because the source is absent.

For approval-requirement atoms: check the review record. Approval gaps are independent
of source availability.

Step 6 -- Record source gaps. For each assessment dimension where a critical source was
absent, record a source gap entry. Apply severity per the Gap Classification Guide.

Step 7 -- Escalate chronic and risk-level-dependent gaps.

Step 8 -- Output: blocking gaps first, then non-blocking. Label each as document gap,
verification gap, or source gap. The reviewer must see all three types clearly distinguished.

---

## Query Type 3 -- Change Comparison

Same as prior version with these additions:

Source availability change: if a source that was available at the prior review is not
available at the current review, flag this as a change. State which source is newly absent
and what dimension it affects. The reviewer must confirm whether the omission is expected.

Confidence change: if the overall confidence of a dimension has decreased since the prior
review (because a source available then is not available now), state the confidence change
explicitly alongside any data changes in that dimension.

---

## Query Type 4 -- Review Summary Generation

Same as prior version with these additions:

Section A must include a Source Coverage Summary with a confidence level for each of the
five dimensions and an honest statement of what each missing source means for the
completeness of the review.

Section C must distinguish document gaps, verification gaps, and source gaps with separate
subsections or labels.

The system recommendation logic is extended:

If any dimension is not assessed because no relevant source was available and the dimension
is critical for this client type: recommend pause -- obtain missing sources before
concluding. This is stronger than escalate-for-review and means the review summary should
not be finalised until the sources are obtained.

If all dimensions have at least limited confidence (no dimension is entirely not assessed):
apply the standard recommendation logic from the prior version, but note the confidence
limitations in the recommendation basis.

---

## What the Agent Must Never Do With Partial Source Sets

Never assume a missing source would have returned a clean result. The absence of a source
is not evidence of the absence of a risk. Record the gap, not an assumed clearance.

Never treat an unverified client document as verified simply because no source contradicted
it. Absence of contradiction is not corroboration.

Never produce a definitive PEP or sanctions clearance without LexisNexis. The client
self-declaration is client-stated only. It cannot clear PEP or sanctions status.

Never collapse the three gap types (document, verification, source) into a single category.
They have different causes, different severities, and different remediation paths.

Never omit the confidence assessment from any Phase 2 answer. The reviewer must always
know what the answer is built on and what it is not built on.
