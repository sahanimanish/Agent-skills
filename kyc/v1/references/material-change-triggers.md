# Material Change Triggers (Partial Source Set Edition)

This file defines what constitutes a material change between reviews, including changes
that arise from differences in source availability between the prior and current review.

---

## How to Perform the Change Comparison With Partial Source Sets

The change comparison compares the current Reconciled Client Record against the prior
review record field by field. When sources are missing in the current review that were
present in the prior review, the comparison must handle this explicitly.

For each dimension: if the prior review had a source that the current review does not,
record the source availability change before comparing any data values. A source newly
absent is itself a material change signal that the reviewer must assess.

For each dimension: compare only the data values that can be compared from available
sources. Do not compare a prior Orbis value against a current client-provided document
as if they are equivalent sources -- the confidence difference must be disclosed.

For each dimension: if the current review has a source that was absent at the prior
review, this is a positive change in confidence. The new source may reveal information
that the prior review could not assess. Any new finding from a newly available source
is treated the same as a new finding from any other source -- it must be recorded and
assessed for materiality.

---

## Source Availability Changes

Source newly absent -- was available at prior review, not available now:
Always flag as a material change signal. The reviewer must confirm whether the absence
is expected (for example a Moodys rating was withdrawn because the client is no longer
rated) or unexplained (the report was not obtained for this review). An unexplained
absence of a previously available source is a data quality flag. Record in Section E
of the review output.

Source newly available -- not available at prior review, available now:
Any findings from the newly available source are new findings relative to the prior
review. Assess each finding for materiality per the triggers below. A newly available
Orbis report revealing a UBO not previously known is always a material change.

---

## Ownership and Structure Changes

New UBO identified: always material. Source may be Orbis (if newly available) or a
client-provided document that differs from the prior review record. If the source is
a client document with no independent corroboration, record as a material change with
limited confidence.

UBO removed: material. If based on a client-provided document with no Orbis corroboration,
flag as unconfirmed removal -- the reviewer must assess whether the removal is genuine.

Ownership percentage change crossing the beneficial ownership threshold: material. If the
change is shown only in a client document with no independent corroboration, record with
limited confidence and flag for independent verification.

New entity in ownership chain: material. Flag especially if the new entity is in a
jurisdiction not previously part of the client profile.

Change in operational status: material. Assess from registrar database if available.

---

## PEP and Sanctions Changes

New PEP identification: always immediately blocking. Source must be LexisNexis. If
LexisNexis was not available at the current review, PEP status change cannot be assessed
-- this is recorded as a not-assessed dimension, not as no change.

PEP status lapsed: material. Apply former PEP treatment rules from the KYC policy.

New sanctions listing: always immediately blocking. Must be from LexisNexis.

Sanctions listing resolved: material positive change. Reviewer must confirm.

New adverse media finding: material. Classify by source tier -- a LexisNexis finding
is a confirmed finding. A news article finding is a signal requiring investigation.

Adverse media resolved: material positive change. Reviewer must confirm.

New internal watchlist match: always material. Always triggers investigation.

---

## Financial Risk Changes

Credit rating downgrade: material. From Moodys only. If Moodys not available, financial
risk change cannot be assessed from prior Moodys rating -- record as not assessed for
this dimension rather than comparing a prior Moodys rating against current management
accounts.

Credit rating upgrade: material positive change.

Rating on review for downgrade or negative outlook: material.

Auditor qualification or going concern note newly present in financial statements: always
a material adverse signal even if Moodys has not changed.

Auditor change: material. Assess whether the new auditor is from a recognised firm.

---

## Document and Verification Changes

Core identity document expired since prior review: blocking if still expired.

Document previously unverified now verified: positive change. Record the verification
outcome.

Document previously verified now unverifiable (independent source no longer available):
record as a confidence reduction, not as a gap in the document itself. The document is
still held. The verification status has changed from verified to unverified due to source
availability change.

New document collected since prior review: positive change. Confirm it meets current
requirements and assess its verification status.

Document outstanding at prior review now chronic: escalates from non-blocking to blocking.

---

## Client Profile Changes

Risk rating change: increase is always material and triggers higher obligations immediately.
Decrease must be documented and approved by reviewer.

Client type reclassification: blocking material change.

Change in stated purpose or business: material if inconsistent with observed activity.

Change in anticipated versus observed activity: material risk signal.

New jurisdiction introduced: material. Assess risk tier. Apply most conservative tier if
jurisdiction is unverified.

Authorised signatory change not reported by client: material. Cross-check against
registrar director records.

---

## How to Record Material Changes When Confidence Is Limited

For each material change, in addition to the standard required fields (change ID,
dimension, prior value, current value, source, policy consequence, required action,
blocking status), add:

Source confidence: the confidence level of the current source reporting this change
(full, reduced, limited).

Verification status: whether the change has been independently verified or is based
on client-provided or lower-tier evidence only.

If confidence is limited: add a required action to obtain independent corroboration
of the change before the review can be concluded on the basis of it.
